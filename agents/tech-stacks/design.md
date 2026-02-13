# Design Tools Stack Documentation

## 🎨 Design Tools

### Figma
**Nivel:** Avanzado

**Workflow:**
1. **Wireframing** - Low-fidelity layouts
2. **Visual Design** - Colors, typography, icons
3. **Prototyping** - Interactive flows
4. **Handoff** - Dev specifications

**Features:**
- Components & variants
- Design tokens
- Auto layout
- Responsive design
- Plugins ecosystem

**Organization:**
```
Project
├── Brand Guide
│   ├── Colors
│   ├── Typography
│   └── Icons
├── Components
│   ├── Buttons
│   ├── Forms
│   └── Cards
├── Screens
│   ├── Desktop
│   ├── Tablet
│   └── Mobile
└── Prototypes
    └── User Flow
```

**Best Practices:**
- Use components for reusability
- Create design system
- Use auto-layout for responsiveness
- Document component usage
- Version control designs
- Share with developers

### Adobe XD
**Nivel:** Intermedio

**Key Features:**
- Wireframe to prototype
- Repeat grid (component arrays)
- Voice & voice prototyping
- Adobe integration

### Sketch
**Nivel:** Intermedio

**Strengths:**
- Lightweight
- Vector editing
- Symbols (components)
- Plugin ecosystem
- Export options

### Photoshop
**Nivel:** Intermedio

**Use Cases:**
- Photo editing
- Complex graphics
- Asset creation
- Image optimization
- Mockup composition

## 🎯 Design System

### Structure

```
Design System
├── Foundation
│   ├── Colors
│   ├── Typography
│   ├── Spacing
│   ├── Shadows
│   └── Animations
├── Components
│   ├── Buttons
│   ├── Inputs
│   ├── Cards
│   ├── Modals
│   └── Navigation
├── Patterns
│   ├── Forms
│   ├── Lists
│   ├── Tables
│   └── Layouts
└── Documentation
    ├── Usage Guidelines
    ├── Do's & Don'ts
    ├── Accessibility
    └── Code Examples
```

### Design Tokens

**Structure:**
```yaml
colors:
  primary:
    50: '#f0f9ff'
    100: '#e0f2fe'
    500: '#0ea5e9'
    900: '#0c2d6b'
  semantic:
    success: colors.primary.500
    error: colors.red.500

typography:
  fontSize:
    sm: '0.875rem'
    base: '1rem'
    lg: '1.125rem'
  fontWeight:
    regular: 400
    semibold: 600
    bold: 700

spacing:
  xs: '0.25rem'
  sm: '0.5rem'
  md: '1rem'
  lg: '1.5rem'
```

### Component Documentation

```markdown
## Button Component

### Variants
- Primary (Blue)
- Secondary (Gray)
- Danger (Red)

### Sizes
- Small: 32px height
- Medium: 40px height (default)
- Large: 48px height

### States
- Default
- Hover
- Active
- Disabled
- Loading

### Usage
```jsx
<Button variant="primary" size="md">
  Click me
</Button>
```

### Accessibility
- WCAG AA compliant
- Proper focus states
- Screen reader friendly
- Min touch target: 44x44px
```

## 📐 Design Principles

### Visual Design
- **Consistency** - Uniform components & patterns
- **Hierarchy** - Clear information ordering
- **Contrast** - Readable text & elements
- **Whitespace** - Breathing room
- **Color** - Purposeful & accessible

### UX Design
- **Simplicity** - Minimal cognitive load
- **Feedback** - User actions acknowledged
- **Error Prevention** - Clear guidance
- **Accessibility** - Inclusive design
- **Performance** - Fast interactions

## ♿ Accessibility in Design

**WCAG 2.1 Guidelines:**
```
Level A: Basic conformance
Level AA: Enhanced (recommended)
Level AAA: Advanced

Key areas:
- Color contrast (4.5:1 for text)
- Touch targets (44x44px minimum)
- Focus indicators (visible)
- Text alternatives (alt text)
- Keyboard navigation
```

**Color Accessibility:**
```
✅ Good:
- Dark text on light background
- High contrast ratios
- Not only color dependent

❌ Avoid:
- Red/Green combinations
- Low contrast text
- Color-only information
```

## 🎬 Export & Handoff

### SVG Export
```xml
<svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
  <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2z" />
</svg>
```

### CSS from Design
```css
.button {
  padding: 0.75rem 1.5rem;
  background-color: #0ea5e9;
  color: white;
  border-radius: 0.375rem;
  font-weight: 600;
  transition: all 0.2s ease;
}

.button:hover {
  background-color: #0284c7;
}
```

### Assets Organization
```
assets/
├── icons/
│   ├── icon-24.svg
│   ├── icon-32.svg
│   └── icon-48.svg
├── illustrations/
│   ├── hero.svg
│   └── empty-state.svg
└── images/
    ├── avatar.webp
    └── screenshot.webp
```

## 📚 Design Handoff Checklist

```markdown
## Assets
- [ ] SVG icons exported
- [ ] Illustrations optimized
- [ ] Images in WebP/AVIF
- [ ] Favicon provided

## Specifications
- [ ] Colors exported (CSS vars)
- [ ] Typography specs documented
- [ ] Spacing system defined
- [ ] Component variants documented

## Documentation
- [ ] Usage guidelines written
- [ ] Do's & Don'ts listed
- [ ] Accessibility notes added
- [ ] Code examples provided

## Deliverables
- [ ] Figma file shared
- [ ] Storybook link provided
- [ ] Component library available
- [ ] Change log updated
```

---

**Last Updated:** February 13, 2025
