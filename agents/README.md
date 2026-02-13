# 🤖 Agentes de Desarrollo

Sistema de agentes especializados para optimizar cada área de tu stack técnico.

## 📋 Agentes Disponibles

### 1. **Frontend Optimizer Agent** 🎨
**Propósito:** Optimizar código frontend y rendimiento visual

**Tecnologías:** React, Next.js, Vue.js, Nuxt.js, Astro, TypeScript

**Responsabilidades:**
- Code review de componentes React/Vue
- Optimización de rendimiento (bundle size, lazy loading)
- Auditoría de accesibilidad (a11y)
- Análisis de tamaño de bundle

**Invoca cuando:**
- Realizas cambios en componentes
- Necesitas mejorar performance del cliente
- Quieres refactorizar código legacy

---

### 2. **Backend Architect Agent** 🏗️
**Propósito:** Diseñar y revisar arquitecturas backend

**Tecnologías:** Node.js, PHP, Laravel, SQL

**Responsabilidades:**
- Revisión de diseño de APIs
- Optimización de bases de datos
- Cumplimiento de Clean Architecture
- Auditorías de seguridad

**Invoca cuando:**
- Diseñas nuevas APIs
- Necesitas optimizar queries SQL
- Implementas patrones arquitectónicos

---

### 3. **DevOps Engineer Agent** 🚀
**Propósito:** Gestionar infraestructura y deployment

**Tecnologías:** Docker, Git, CI/CD, nginx, Linux

**Responsabilidades:**
- Configuración de pipelines
- Optimización de contenedores
- Monitoreo de performance
- Endurecimiento de seguridad

**Invoca cuando:**
- Configuras CI/CD
- Desplegaste cambios
- Necesitas escalar infraestructura

---

### 4. **Testing Specialist Agent** ✅
**Propósito:** Asegurar calidad del código

**Tecnologías:** Vitest, PHPUnit, Code Reviews, Clean Architecture

**Responsabilidades:**
- Definir estrategia de testing
- Análisis de cobertura
- Standards de code review
- Métricas de calidad

**Invoca cuando:**
- Escribes testes
- Necesitas mejorar cobertura
- Revisas código crítico

---

### 5. **SEO & Performance Agent** ⚡
**Propósito:** Optimizar SEO y rendimiento

**Tecnologías:** Web Performance, Core Web Vitals, SEO

**Responsabilidades:**
- Auditorías Lighthouse
- Optimización de Core Web Vitals
- Checks técnicos de SEO
- Optimización de assets
- Estrategias de caching

**Invoca cuando:**
- Necesitas mejorar PageSpeed
- Optimizas para Core Web Vitals
- Trabajas en SEO técnico

---

### 6. **Design System Agent** 🎭
**Propósito:** Mantener consistencia en diseño

**Tecnologías:** Figma, Design Tools

**Responsabilidades:**
- Mantenimiento de librerías de componentes
- Gestión de design tokens
- Checks de consistencia UI
- Handoff design-to-code

**Invoca cuando:**
- Creas nuevos componentes
- Actualizas design system
- Trabajas con diseñadores

---

## 🔄 Workflows Predefinidos

### New Project Workflow
```
1. Design System Agent     → Setup componentes base
2. Frontend Optimizer      → Estructura de projeto
3. Backend Architect       → Diseño de API
4. DevOps Engineer         → Setup infraestructura
```

### Performance Audit Workflow
```
1. SEO & Performance       → Audit Lighthouse
2. Frontend Optimizer      → Análisis bundle
3. DevOps Engineer         → Optimización infra
```

### Code Review Workflow
```
1. Testing Specialist      → Calidad y coverage
2. Backend Architect       → Arquitectura
3. Frontend Optimizer      → Performance
```

### Deployment Workflow
```
1. DevOps Engineer         → Build y test
2. Testing Specialist      → QA checks
3. SEO & Performance       → Post-deploy audit
```

---

## 💡 Cómo Usar

### Invocación Individual
```bash
# Ejemplo: Code review de componente React
@frontend-optimizer Review del componente Button.tsx
- Verificar rendimiento
- Controlar accesibilidad
- Sugerir mejoras
```

### Invocar Workflow
```bash
# Ejemplo: Audit de performance completo
@performance-audit Mi sitio está lento
- Analizar todas las métricas
- Dar recomendaciones
- Priorizar mejoras
```

---

## 🎯 Tech-Stack Específicos

Cada agente tiene conocimiento profundo de su stack:

### Frontend Stack
- Componentes React hooks
- Composition API en Vue
- State management (Redux, Pinia)
- Testing con Vitest
- Build tools (Vite, webpack)

### Backend Stack
- Arquitectura en capas
- Patrones de diseño (Factory, Repository)
- ORM (Eloquent, Sequelize)
- Database migrations
- API versioning

### DevOps Stack
- Docker best practices
- CI/CD pipelines
- Container orchestration
- Monitoring y logging
- Infrastructure as Code

---

## 📊 Métricas para Cada Agente

| Agente | KPI | Target |
|--------|-----|--------|
| Frontend | Lighthouse Score | >90 |
| Backend | Code Coverage | >80% |
| DevOps | Deployment Time | <5 min |
| Testing | Test Pass Rate | 100% |
| SEO | Core Web Vitals | Green |
| Design | Component Reuse | >70% |

---

## 🚨 Alerts & Triggers

Los agentes se activan automáticamente cuando:

- ❌ Lighthouse score cae <80
- ❌ Test coverage baja <75%
- ❌ Build time aumenta >10 min
- ❌ Core Web Vitals = Red
- ❌ Seguridad vulns detectadas
- ❌ Performance budget exceeded

---

**Última actualización:** Febrero 13, 2025
