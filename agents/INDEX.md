# 📖 Documentation Index

Your complete tech stack reference and agent system.

## 🎯 Main Documents

### SKILLS.md
Complete overview of your technical stack organized by category:
- AI & Development (Claude, Windsurf, Agents)
- Frontend (React, Next.js, Vue, Astro, TypeScript, etc.)
- Backend (Node.js, PHP, Laravel, SQL)
- Testing & Quality (Vitest, PHPUnit, Clean Architecture)
- DevOps & Tools (Docker, Git, CI/CD, nginx)
- Performance & SEO
- Design Tools (Figma, Photoshop, Adobe XD)
- CMS & eCommerce (WordPress, Prestashop)
- Currently Learning (PostgreSQL, Kafka, AWS S3, TDD, DDD, FFB)

## 🤖 Agent System

### agents/README.md
Overview of the 6 specialized agents:
1. **Frontend Optimizer** - Optimize React, Vue, performance
2. **Backend Architect** - Design Node.js, PHP, Laravel systems
3. **DevOps Engineer** - Manage Docker, CI/CD, infrastructure
4. **Testing Specialist** - Ensure quality with Vitest, PHPUnit
5. **SEO & Performance** - Optimize Core Web Vitals, SEO
6. **Design System** - Maintain Figma, components, design tokens

### agents/GETTING_STARTED.md
How to use the agent system effectively with examples and workflows.

### agents/agents.json
Configuration file defining agents, technologies, and workflows.

## 📋 Agent System Prompts

Each file contains specialized instructions for AI assistants:

### agents/prompts/
- **frontend-optimizer.md** - React/Vue/TypeScript expert guidance
- **backend-architect.md** - System design & API expertise
- **devops-engineer.md** - Infrastructure & deployment expertise
- **testing-specialist.md** - QA & code quality expertise
- **seo-performance.md** - Performance & SEO expertise
- **design-system.md** - Design consistency expertise

## 📚 Technical Documentation

All files in `agents/tech-stacks/` contain implementation examples and best practices:

### agents/tech-stacks/frontend.md
Deep dive into:
- HTML5, CSS3, JavaScript (ES6+), TypeScript
- React, Next.js, Vue.js, Nuxt.js, Astro
- Three.js, Web Components
- Testing with Vitest
- Performance optimization techniques

### agents/tech-stacks/backend.md
Deep dive into:
- Node.js, Express, Fastify
- PHP, Laravel with Eloquent ORM
- SQL query optimization
- REST APIs & SOAP
- Clean Architecture patterns
- Security best practices

### agents/tech-stacks/devops.md
Deep dive into:
- Docker & Docker Compose
- GitHub Actions & GitLab CI/CD
- nginx & Apache configuration
- Linux & Bash scripting
- Monitoring & logging
- Security hardening
- Infrastructure as Code (Terraform)

### agents/tech-stacks/testing-quality.md
Deep dive into:
- Unit testing with Vitest & PHPUnit
- Integration & E2E testing
- TDD (Test-Driven Development)
- Code review standards
- Clean Architecture principles
- Test coverage analysis

### agents/tech-stacks/performance-seo.md
Deep dive into:
- Core Web Vitals (LCP, FID, CLS)
- Lighthouse audits
- Asset optimization
- Caching strategies
- Schema markup & SEO
- Performance budgets
- Monitoring tools

### agents/tech-stacks/design.md
Deep dive into:
- Figma advanced features
- Adobe XD, Sketch
- Design systems & tokens
- Component libraries
- WCAG accessibility
- Design-to-code handoff

### agents/tech-stacks/cms-ecommerce.md
Deep dive into:
- WordPress theme & plugin development
- PrestaShop module development
- eCommerce best practices
- Payment integration
- Database optimization
- Security in eCommerce

### agents/tech-stacks/learning.md
Current learning priorities with examples:
- PostgreSQL (40% proficiency)
- Kafka (20% proficiency)
- AWS S3 (30% proficiency)
- TDD (60% proficiency)
- DDD (50% proficiency)
- FFB (20% proficiency)

## 🧭 How to Navigate

### For Learning a New Technology
1. Start with [SKILLS.md](../SKILLS.md) - Overview
2. Check [agents/tech-stacks/](./tech-stacks/) - Deep documentation
3. Find specific agent prompt - Get guidance
4. Reference examples - Implement

### For Solving a Problem

**Performance Issue:**
```
1. agents/tech-stacks/performance-seo.md
2. Ask @seo-performance agent
3. Follow recommendations
```

**Code Quality Issue:**
```
1. agents/tech-stacks/testing-quality.md
2. Ask @testing-specialist agent
3. Implement improvements
```

**Design System Question:**
```
1. agents/tech-stacks/design.md
2. Ask @design-system agent
3. Update components
```

### For Onboarding

Share these files with new team members:
1. [SKILLS.md](../SKILLS.md) - Your tech stack
2. [agents/README.md](./README.md) - How agents work
3. [agents/GETTING_STARTED.md](./GETTING_STARTED.md) - Using agents
4. Relevant `agents/tech-stacks/*.md` files
5. Your project context (`agents/context.md` if created)

## 📊 Document Statistics

```
Total Files:       12+ markdown files
Total Lines:       5000+ lines of documentation
Coverage:          9 technology categories
Agents:            6 specialized agents
Tech Stacks:       8 deep dive documents
Code Examples:     100+ runnable examples
```

## 🔍 Search Quick Links

### By Technology

**React** → [frontend.md](./tech-stacks/frontend.md#react)
**vue.js** → [frontend.md](./tech-stacks/frontend.md#vuejs)
**Next.js** → [frontend.md](./tech-stacks/frontend.md#nextjs)
**Node.js** → [backend.md](./tech-stacks/backend.md#nodejs)
**Laravel** → [backend.md](./tech-stacks/backend.md#laravel)
**Docker** → [devops.md](./tech-stacks/devops.md#docker)
**PostgreSQL** → [learning.md](./tech-stacks/learning.md#postgresql)
**Kafka** → [learning.md](./tech-stacks/learning.md#kafka)

### By Concept

**Performance** → [performance-seo.md](./tech-stacks/performance-seo.md)
**Security** → [backend.md](./tech-stacks/backend.md#security)
**Testing** → [testing-quality.md](./tech-stacks/testing-quality.md)
**Deployment** → [devops.md](./tech-stacks/devops.md#cicd-pipelines)
**SEO** → [performance-seo.md](./tech-stacks/performance-seo.md#seo-optimization)
**Accessibility** → [design.md](./tech-stacks/design.md#-accessibility-in-design)

### By Agent

**Frontend Optimizer** → [prompts/frontend-optimizer.md](./prompts/frontend-optimizer.md)
**Backend Architect** → [prompts/backend-architect.md](./prompts/backend-architect.md)
**DevOps Engineer** → [prompts/devops-engineer.md](./prompts/devops-engineer.md)
**Testing Specialist** → [prompts/testing-specialist.md](./prompts/testing-specialist.md)
**SEO & Performance** → [prompts/seo-performance.md](./prompts/seo-performance.md)
**Design System** → [prompts/design-system.md](./prompts/design-system.md)

## 🎓 Learning Paths

### Frontend Developer Path
1. [frontend.md](./tech-stacks/frontend.md) - Learn React/Vue
2. [performance-seo.md](./tech-stacks/performance-seo.md) - Optimize
3. [design.md](./tech-stacks/design.md) - Design skills
4. Ask @frontend-optimizer regularly

### Full Stack Developer Path
1. [frontend.md](./tech-stacks/frontend.md) - Frontend skills
2. [backend.md](./tech-stacks/backend.md) - Backend skills
3. [devops.md](./tech-stacks/devops.md) - DevOps basics
4. [learning.md](./tech-stacks/learning.md) - PostgreSQL, TDD

### DevOps Engineer Path
1. [devops.md](./tech-stacks/devops.md) - Docker, CI/CD
2. [backend.md](./tech-stacks/backend.md) - API insights
3. [performance-seo.md](./tech-stacks/performance-seo.md) - Monitor
4. Ask @devops-engineer regularly

## 🔄 Maintenance Schedule

- **Monthly:** Review [SKILLS.md](../SKILLS.md) - Update proficiency
- **Quarterly:** Review [agents/agents.json](./agents.json) - Check relevance
- **Per Release:** Update [learning.md](./tech-stacks/learning.md) - Progress
- **As Learned:** Update tech-stacks/* - Add new knowledge
- **Yearly:** Full system review - Update all documentation

## 📱 Quick Reference

### File Size Guide
- **SKILLS.md** - 5min read (overview)
- **agents/README.md** - 10min read (system explanation)
- **agents/prompts/*.md** - 5min each (AI instructions)
- **agents/tech-stacks/*.md** - 15-20min each (deep dive)
- **agents/GETTING_STARTED.md** - 10min read (tutorial)

### Best Times to Reference
- **When learning:** Use SKILLS.md → tech-stacks/*
- **When reviewing code:** Use prompts/* + tech-stacks/*
- **When mentoring:** Use GETTING_STARTED.md + tech-stacks/*
- **When onboarding:** Use README.md → GETTING_STARTED.md
- **When stuck:** Use tech-stacks/* + ask agent

## 💡 Pro Tips

1. **Bookmark this file** for quick navigation
2. **Share GETTING_STARTED.md** with team members
3. **Update tech-stacks** as you learn
4. **Reference prompts** when consulting agents
5. **Link to specific sections** when discussing code

---

**Last Updated:** February 13, 2025
**Version:** 1.0
