---
applyTo: "**"
---

# Sunny Dodti Portfolio - Style & Design System Guidelines

## 🎨 Overview

This documen## 🔧 Design Tokens for Consistency

### Consistent Styling Approach (Required)

**CRITICAL**: All portfolio implementations MUST use design tokens from `/data/styles/style.json` to ensure consistent styling across technologies.fines the comprehensive design system for Sunny Dodti's multi-technology portfolio. The system ensures visual consistency across React, Flutter, Angular, Vue, Next.js, and Svelte implementations while maintaining a professional, blue-themed aesthetic.

## 📁 Style Architecture

### File Structure

```
/data/styles/
├── style.json                      # Complete color palette & design tokens
├── pallet-demo-dark-light.html     # Interactive theme preview & testing
└── README.md                       # Style documentation
```

### Design Tokens Source

- **Primary Source**: `/data/styles/style.json`
- **Demo & Testing**: `/data/styles/pallet-demo-dark-light.html`
- **Version**: 1.0.0
- **Theme**: Blue-focused with comprehensive dark/light mode support

## 🌈 Color Palette Guidelines

### Primary Blue Scale

```json
{
  "light_mode": {
    "primary": {
      "50": "#eff6ff", // Lightest blue backgrounds
      "100": "#dbeafe", // Light blue backgrounds
      "200": "#bfdbfe", // Subtle blue accents
      "300": "#93c5fd", // Light blue elements
      "400": "#60a5fa", // Medium blue interactions
      "500": "#3b82f6", // Primary blue (buttons, links)
      "600": "#2563eb", // Primary blue hover states
      "700": "#1d4ed8", // Dark blue accents
      "800": "#1e40af", // Darker blue elements
      "900": "#1e3a8a" // Darkest blue
    }
  }
}
```

### Theme Usage Rules

#### Light Mode

- **Primary Action Color**: `#3b82f6` (Blue 500)
- **Background**: `#ffffff` (Pure white)
- **Surface**: `#f8fafc` (Light gray)
- **Text Primary**: `#0f172a` (Dark slate)
- **Text Secondary**: `#475569` (Medium gray)
- **Border**: `#e2e8f0` (Light gray border)

#### Dark Mode

- **Primary Action Color**: `#60a5fa` (Blue 400)
- **Background**: `#0f172a` (Dark slate)
- **Surface**: `#1e293b` (Medium dark)
- **Text Primary**: `#f8fafc` (Light gray)
- **Text Secondary**: `#e2e8f0` (Medium light)
- **Border**: `#334155` (Dark gray border)

### Color Accessibility

- **Contrast Ratios**: All color combinations meet WCAG 2.1 AA standards
- **Focus States**: High contrast blue (`#3b82f6` light, `#60a5fa` dark)
- **Error States**: Red variants that work in both themes
- **Success States**: Green variants optimized for accessibility

## 🎯 Component Design Standards

### Typography System

```json
{
  "font_families": {
    "primary": "Inter, system-ui, -apple-system, sans-serif",
    "mono": "JetBrains Mono, Menlo, Monaco, Consolas, monospace"
  },
  "font_sizes": {
    "xs": "0.75rem", // 12px - Small labels
    "sm": "0.875rem", // 14px - Body text small
    "base": "1rem", // 16px - Body text
    "lg": "1.125rem", // 18px - Large body
    "xl": "1.25rem", // 20px - Small headings
    "2xl": "1.5rem", // 24px - Section headings
    "3xl": "1.875rem", // 30px - Page headings
    "4xl": "2.25rem", // 36px - Hero headings
    "5xl": "3rem", // 48px - Large hero
    "6xl": "3.75rem" // 60px - Extra large
  }
}
```

### Spacing Scale

```json
{
  "spacing": {
    "xs": "0.25rem", // 4px
    "sm": "0.5rem", // 8px
    "md": "1rem", // 16px
    "lg": "1.5rem", // 24px
    "xl": "2rem", // 32px
    "2xl": "3rem", // 48px
    "3xl": "4rem" // 64px
  }
}
```

## � CSS Variables for Consistency

### CSS Custom Properties (Required)

**CRITICAL**: All portfolio implementations MUST use CSS variables to ensure consistent styling and theme switching across technologies.

#### Design Token Implementation by Technology

**Source**: Always reference `/data/styles/style.json` for exact color values, spacing, typography, etc.

##### Web Technologies (React, Vue, Angular, Svelte)

```css
/* Use CSS Custom Properties */
:root {
  --color-primary-light: #3b82f6;
  --color-primary-dark: #60a5fa;
  --color-background-light: #ffffff;
  --color-background-dark: #0f172a;
  --spacing-md: 1rem;
  --font-family-primary: "Inter", system-ui, sans-serif;
}

[data-theme="dark"] {
  --color-primary: var(--color-primary-dark);
  --color-background: var(--color-background-dark);
}
```

##### Flutter

```dart
class PortfolioColors {
  // Light mode colors from style.json
  static const Color primaryLight = Color(0xFF3B82F6);
  static const Color backgroundLight = Color(0xFFFFFFFF);
  static const Color surfaceLight = Color(0xFFF8FAFC);

  // Dark mode colors from style.json
  static const Color primaryDark = Color(0xFF60A5FA);
  static const Color backgroundDark = Color(0xFF0F172A);
  static const Color surfaceDark = Color(0xFF1E293B);
}

class PortfolioSpacing {
  static const double xs = 4.0;   // 0.25rem
  static const double sm = 8.0;   // 0.5rem
  static const double md = 16.0;  // 1rem
  static const double lg = 24.0;  // 1.5rem
}
```

##### Other Technologies (Swift, Kotlin, etc.)

```swift
// iOS Swift example
struct PortfolioColors {
    static let primaryLight = UIColor(hex: "#3b82f6")
    static let primaryDark = UIColor(hex: "#60a5fa")
    static let backgroundLight = UIColor(hex: "#ffffff")
    static let backgroundDark = UIColor(hex: "#0f172a")
}
```

#### Consistency Rules

1. **NEVER use hardcoded colors** - Always reference `/data/styles/style.json`
2. **Consistent naming** - Use same color names across all technologies
3. **Theme switching** - Implement light/dark mode in technology-appropriate way
4. **Single source of truth** - `/data/styles/style.json` contains all design tokens

## �🛠️ Technology-Specific Implementation

### React/Next.js

```jsx
// REQUIRED: Use design tokens from style.json
import { portfolioTheme } from "../styles/theme";

const Button = ({ variant = "primary", children, ...props }) => (
  <button
    className={`btn btn-${variant}`}
    style={{
      background: "var(--gradient-button)",
      color: "var(--color-text-inverse)",
      padding: "var(--spacing-md) var(--spacing-lg)",
      borderRadius: "var(--border-radius-md)",
      fontSize: "var(--font-size-base)",
      fontFamily: "var(--font-family-primary)",
    }}
    {...props}
  >
    {children}
  </button>
);

// Or use theme object from style.json
const cardStyles = {
  background: portfolioTheme.gradients.light_mode.card,
  border: `1px solid ${portfolioTheme.colors.light_mode.border.primary}`,
  borderRadius: portfolioTheme.border_radius.lg,
  padding: portfolioTheme.spacing.lg,
  color: portfolioTheme.colors.light_mode.text.primary,
};
```

### Flutter

```dart
// Define theme data using the color palette
class PortfolioTheme {
  static ThemeData lightTheme = ThemeData(
    primarySwatch: Colors.blue,
    primaryColor: Color(0xFF3B82F6),
    backgroundColor: Color(0xFFFFFFFF),
    scaffoldBackgroundColor: Color(0xFFF8FAFC),
  );

  static ThemeData darkTheme = ThemeData.dark().copyWith(
    primaryColor: Color(0xFF60A5FA),
    backgroundColor: Color(0xFF0F172A),
    scaffoldBackgroundColor: Color(0xFF1E293B),
  );
}
```

### Angular

```typescript
// Define theme using Angular Material
@Injectable()
export class ThemeService {
  lightTheme = {
    primary: "#3b82f6",
    background: "#ffffff",
    surface: "#f8fafc",
    "on-primary": "#ffffff",
    "on-background": "#0f172a",
  };

  darkTheme = {
    primary: "#60a5fa",
    background: "#0f172a",
    surface: "#1e293b",
    "on-primary": "#0f172a",
    "on-background": "#f8fafc",
  };
}
```

## 📱 Responsive Design Guidelines

### Breakpoints

```json
{
  "breakpoints": {
    "sm": "640px",
    "md": "768px",
    "lg": "1024px",
    "xl": "1280px",
    "2xl": "1536px"
  }
}
```

### Mobile-First Approach

- **Base styles**: Mobile (320px+)
- **Progressive enhancement**: Tablet and desktop
- **Touch targets**: Minimum 44px for interactive elements
- **Typography scaling**: Fluid typography using clamp()

## ♿ Accessibility Standards

### Color Contrast Requirements

- **Normal text**: 4.5:1 minimum contrast ratio
- **Large text**: 3:1 minimum contrast ratio
- **Interactive elements**: Clear focus indicators
- **Error states**: Not relying on color alone

## 🧪 Testing & Validation

### Color Palette Testing

1. **Open Demo Page**: `/data/styles/pallet-demo-dark-light.html`
2. **Toggle Themes**: Test light/dark mode switching
3. **Component Preview**: Review all UI components
4. **Contrast Check**: Validate accessibility ratios
5. **Cross-browser**: Test in Chrome, Firefox, Safari, Edge

## 📋 Usage Checklist

### Before Implementation

- [ ] Review complete color palette in `/data/styles/style.json`
- [ ] Test interactive demo for visual approval
- [ ] Understand light/dark mode color mapping
- [ ] Validate accessibility requirements

### During Development

- [ ] Use CSS variables for theme switching
- [ ] Implement consistent spacing scale
- [ ] Follow typography hierarchy
- [ ] Test responsive design at all breakpoints
- [ ] Validate color contrast ratios

### After Implementation

- [ ] Cross-browser compatibility testing
- [ ] Accessibility audit (WAVE, axe)
- [ ] Performance testing (Lighthouse)
- [ ] Visual consistency across portfolio versions

## 🔄 Maintenance Guidelines

### Theme Updates

- **Source of Truth**: Always update `/data/styles/style.json` first
- **Demo Sync**: Update HTML demo when colors change
- **Version Control**: Increment version number for major changes
- **Documentation**: Update this file when adding new components

Remember: The blue theme represents professionalism, trust, and technical expertise - core values of Sunny Dodti's brand identity.

---

**Last Updated**: September 22, 2025  
**Theme Version**: 1.0.0
