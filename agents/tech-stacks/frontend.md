# Frontend Stack Documentation

## 📚 Tecnologías Core

### HTML5
**Nivel:** Experto
```html
<!-- Semantic HTML -->
<header>
  <nav aria-label="Main navigation">
    <!-- nav items -->
  </nav>
</header>
<main>
  <article>
    <h1>Title</h1>
    <p>Content</p>
  </article>
</main>
<footer>Copyright</footer>
```

**Best Practices:**
- Usar semantic tags
- ARIA labels cuando sea necesario
- Mobile-first approach
- Validate HTML

### CSS3
**Nivel:** Experto
```css
/* Modern CSS patterns */
:root {
  --color-primary: #3b82f6;
  --spacing-unit: 1rem;
}

.component {
  display: grid;
  gap: var(--spacing-unit);
  
  @media (max-width: 768px) {
    grid-template-columns: 1fr;
  }
}
```

**Tools & Frameworks:**
- Tailwind CSS
- CSS Modules
- CSS-in-JS (Styled Components)
- PostCSS

### JavaScript (ES6+)
**Nivel:** Experto
```javascript
// Modern JavaScript patterns
const fetchData = async () => {
  try {
    const response = await fetch('/api/data');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error:', error);
  }
};

// Arrow functions, destructuring, spread
const { name, ...rest } = person;
const arr = [...existing, ...new];
```

## 🚀 Frameworks

### React
**Nivel:** Avanzado
```jsx
import { useState, useCallback } from 'react';

export const Counter = () => {
  const [count, setCount] = useState(0);
  
  const increment = useCallback(() => {
    setCount(c => c + 1);
  }, []);
  
  return (
    <button onClick={increment}>
      Count: {count}
    </button>
  );
};
```

**Especialidades:**
- Functional components & hooks
- Custom hooks
- Context API
- Suspense & lazy loading
- Concurrent features

### Next.js
**Nivel:** Avanzado
```typescript
// app/page.tsx
import { Metadata } from 'next';

export const metadata: Metadata = {
  title: 'Home',
  description: 'Welcome',
};

export default function Page() {
  return <div>Home</div>;
}
```

**Features:**
- App Router
- Server Components
- Streaming
- Incremental Static Regeneration (ISR)
- API Routes

### Vue.js
**Nivel:** Avanzado
```vue
<script setup lang="ts">
import { ref, computed } from 'vue';

const count = ref(0);
const doubled = computed(() => count.value * 2);
</script>

<template>
  <button @click="count++">Count: {{ count }}</button>
  <p>Doubled: {{ doubled }}</p>
</template>
```

### Nuxt.js
**Nivel:** Avanzado
- Auto-routing
- Server-Side Rendering (SSR)
- Static Site Generation (SSG)
- Composables
- Middleware

### Astro
**Nivel:** Avanzado
```astro
---
// Component script
const data = await fetch('/api/data').then(r => r.json());
---
<section>
  <h1>My Site</h1>
  {data.items.map(item => (
    <Item key={item.id} title={item.title} />
  ))}
</section>
```

**Strengths:**
- Island architecture
- Partial hydration
- Static-first
- Multi-framework support

### TypeScript
**Nivel:** Avanzado
```typescript
interface User {
  id: string;
  name: string;
  email?: string;
}

type ApiResponse<T> = {
  data: T;
  status: number;
};

async function fetchUser(id: string): Promise<User> {
  // implementation
}
```

## 🎮 Specialized Libraries

### Three.js
**Uso:** 3D graphics, visualizations
```javascript
import * as THREE from 'three';

const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, w/h, 0.1, 1000);
const renderer = new THREE.WebGLRenderer();

const geometry = new THREE.BoxGeometry();
const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });
const cube = new THREE.Mesh(geometry, material);
scene.add(cube);
```

### Web Components
**Uso:** Reusable custom elements
```javascript
class MyElement extends HTMLElement {
  connectedCallback() {
    this.render();
  }
  
  render() {
    this.innerHTML = `<h1>${this.getAttribute('title')}</h1>`;
  }
}

customElements.define('my-element', MyElement);
```

## 📦 Package Management

- **npm** - Primary package manager
- **Vite** - Build tool & dev server
- **pnpm** - Optional faster alternative
- **Bundlers** - webpack, Rollup, esbuild

## 🧪 Testing

**Vitest Setup:**
```typescript
import { describe, it, expect } from 'vitest';

describe('Counter', () => {
  it('increments', () => {
    const count = 0;
    expect(count + 1).toBe(1);
  });
});
```

## 📈 Performance Optimization

**Critical Optimizations:**
1. Code splitting
2. Lazy loading components
3. Image optimization
4. Minification
5. Caching strategies

---

**Last Updated:** February 13, 2025
