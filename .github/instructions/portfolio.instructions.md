---
applyTo: "**"
---

# Sunny Dodti Portfolio Development Guidelines

## 🎯 Project Context

This repository contains Sunny Dodti's professional portfolio system with multi-technology implementations. The portfolio showcases software development expertise across different frontend frameworks while maintaining data consistency through a centralized JSON system.

## 📊 Data Architecture Guidelines

### JSON Profile Structure

- **Primary Data Source**: `/data/profiles/default.json` (single source of truth)
- **Portfolio Apps**: All portfolio technologies use `default.json` directly unless specified
- **Specialized Profiles**: For non-portfolio use cases (job applications, specific contexts)
- **Data Validation**: All profiles must pass JSON schema validation
- **Consistency**: Maintain data consistency across all portfolio versions

### When Working with Profile Data:

```javascript
// Always validate data structure
const profile = await validateProfile(profileData);

// Use centralized data fetching utilities
import { PortfolioDataFetcher } from "../shared/utils/data-fetcher.js";

// Transform data for specific technologies when needed
const transformedData = transformForTechnology(profile, "react");
```

## 🏗️ Repository Structure Guidelines

### Main Repository (`sunnydodti`)

- **Purpose**: Central coordination, data management, shared assets
- **Key Directories**:
  - `/data/profiles/`: JSON profile data
  - `/portfolio/`: Git submodules for each technology
  - `/shared/`: Common assets, themes, utilities
  - `/.github/`: CI/CD workflows and instructions

### Technology-Specific Repositories

- **Naming Convention**: `portfolio-{technology}` (e.g., `portfolio-react`)
- **Independence**: Each repo manages its own deployment and dependencies
- **Data Integration**: Fetch `default.json` from main repository's JSON endpoints
- **Consistency**: Follow shared design system and component structure

## 🎨 Design System Guidelines

### Blue-Themed Color System

**Primary Color Source**: `/data/styles/style.json` - Complete blue-themed palette with dark/light mode support

```json
{
  "light_mode": {
    "primary": "#3b82f6",
    "background": "#ffffff",
    "surface": "#f8fafc",
    "text": "#0f172a"
  },
  "dark_mode": {
    "primary": "#60a5fa",
    "background": "#0f172a",
    "surface": "#1e293b",
    "text": "#f8fafc"
  }
}
```

**Interactive Demo**: `/data/styles/pallet-demo-dark-light.html` - Live preview with theme toggle

### Design Tokens (CRITICAL)

**ALL portfolio implementations MUST use design tokens from `/data/styles/style.json` for consistency:**

```css
/* Web Technologies: Use CSS variables */
.component {
  background: var(--color-background-primary);
  color: var(--color-text-primary);
  padding: var(--spacing-lg);
}
```

```dart
/* Flutter: Use color constants */
Container(
  color: PortfolioColors.backgroundLight,
  padding: EdgeInsets.all(PortfolioSpacing.lg),
  child: Text(
    'Content',
    style: TextStyle(color: PortfolioColors.textLight),
  ),
)
```

### Component Standards

- **Design Tokens**: NEVER use hardcoded colors - always use design tokens from style.json
- **Theme Switching**: Light/dark mode using technology-appropriate methods
- **Responsive Design**: Mobile-first approach
- **Accessibility**: WCAG 2.1 AA compliance
- **Consistency**: Same colors across all technologies
- **Performance**: Lighthouse score 95+
- **Consistency**: Same sections across all technologies

## 🚀 Development Standards

### Code Quality Requirements

- **TypeScript**: Prefer TypeScript for type safety
- **Linting**: ESLint/equivalent for each technology
- **Formatting**: Prettier/equivalent for consistent formatting
- **Testing**: Unit tests for utilities, component tests for UI

### Technology-Specific Guidelines

#### React Portfolio

- **Framework**: React 18+ with TypeScript
- **Styling**: Tailwind CSS for consistency
- **State Management**: Context API or Zustand for simple state
- **Build Tool**: Vite for fast development

#### Flutter Web Portfolio

- **Version**: Flutter 3.x with Dart
- **Responsive**: Use LayoutBuilder and MediaQuery
- **Performance**: Optimize for web with tree shaking
- **Navigation**: Auto routing for deep linking

#### Angular Portfolio

- **Version**: Angular 16+ with TypeScript
- **UI Library**: Angular Material for components
- **Architecture**: Standalone components preferred
- **PWA**: Implement service worker for offline capability

### Cross-Technology Requirements

- **Performance**: First Contentful Paint < 1.5s
- **SEO**: Meta tags, Open Graph, JSON-LD
- **Analytics**: Google Analytics 4 integration
- **Monitoring**: Error tracking and performance monitoring

## 🌐 Deployment Guidelines

### Domain Strategy

- **Primary**: `sunnydodti.com` → React (default)
- **Technology Subdomains**: `{tech}.sunnydodti.com`
- **Backup Domains**: `*.sunnydodti.persist.site`

### CI/CD Requirements

- **Automated Deployment**: GitHub Actions for each repository
- **Data Sync**: Automatic updates when profile data changes
- **Testing**: Run tests before deployment
- **Rollback**: Ability to rollback deployments

### Platform Recommendations

- **React/Next.js**: Vercel
- **Flutter Web**: Firebase Hosting
- **Angular/Vue**: Netlify
- **Static Sites**: GitHub Pages

## 📝 Content Guidelines

### Portfolio Sections (Required)

1. **Hero**: Name, title, brief description, call-to-action
2. **About**: Detailed background, interests, current focus
3. **Experience**: Work history with expandable details
4. **Projects**: Categorized with filters (work, personal, academic)
5. **Skills**: Technical skills with visual indicators
6. **Education**: Academic background and certifications
7. **Contact**: Contact form and social media links
8. **Technology Showcase**: Links to other portfolio versions

### Content Best Practices

- **Concise**: Clear, scannable content
- **Quantified**: Include metrics and achievements
- **Current**: Regular updates with latest projects
- **Professional**: Maintain professional tone and imagery

## 🔄 Maintenance Guidelines

### Data Updates

- **Source**: Always update `default.json` first
- **Propagation**: Updates automatically sync to all portfolios
- **Validation**: Validate JSON before committing
- **Testing**: Test changes across all technology versions

### Version Control

- **Branching**: Feature branches for new developments
- **Submodules**: Update submodules when shared data changes
- **Releases**: Tag releases for major updates
- **Documentation**: Update documentation with changes

### Performance Monitoring

- **Metrics**: Monitor Core Web Vitals across all portfolios
- **Alerts**: Set up alerts for performance degradation
- **Optimization**: Regular performance audits and optimizations
- **Analytics**: Track user engagement and conversion metrics

## 🛠️ Development Workflow

### Setting Up New Technology Portfolio

1. Create new repository: `portfolio-{technology}`
2. Add as submodule to main repository
3. Implement core sections using technology standards
4. Set up data fetching from main repository
5. Configure deployment pipeline
6. Add subdomain DNS configuration
7. Update main portfolio with cross-links

### Making Changes

1. **Data Changes**: Update in main repository first
2. **UI Changes**: Update in specific technology repository
3. **Shared Changes**: Update in `/shared/` directory
4. **Testing**: Test across affected portfolios
5. **Documentation**: Update relevant documentation

## 🎯 Success Criteria

### Technical

- [ ] All portfolios deployed and accessible
- [ ] Performance scores meet targets (95+ Lighthouse)
- [ ] Zero critical accessibility violations
- [ ] Cross-browser compatibility verified

### User Experience

- [ ] Consistent design across all technologies
- [ ] Fast loading times (< 2s)
- [ ] Mobile-responsive design
- [ ] Intuitive navigation between portfolio versions

### Business

- [ ] Professional presentation of skills and experience
- [ ] Easy contact and networking opportunities
- [ ] Showcase of technology versatility
- [ ] SEO optimized for discoverability

## 📞 Support and Questions

For questions about portfolio development:

1. Check existing documentation in `/docs/`
2. Review similar implementations in other technology portfolios
3. Ensure consistency with design system and data structure
4. Test changes across multiple devices and browsers

Remember: The goal is to create a cohesive, professional portfolio ecosystem that demonstrates technical versatility while maintaining consistency and user experience across all technology implementations.
