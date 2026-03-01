# Coding Agents Presentation 🤖

Presentación interactiva sobre **Agentes de IA como Compañeros de Codificación** — herramientas modernas, flujos de trabajo eficientes, buenas prácticas y estrategias para evitar alucinaciones.

**Presentado por**: Alejandro de la Fuente  
**Duración**: 45-60 minutos  
**Live**: https://codigosinsiesta.github.io/coding-agents-presentation/

---

## 📋 Tabla de Contenidos

- [Visión General](#visión-general)
- [Temas Clave](#temas-clave)
- [Inicio Rápido](#inicio-rápido)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Stack Tecnológico](#stack-tecnológico)
- [Desarrollo](#desarrollo)
- [Sistema de Diseño](#sistema-de-diseño)
- [Navegación](#navegación)
- [Licencia](#licencia)

---

## 🎯 Visión General

Esta presentación explora el ecosistema de **agentes de codificación con IA**: herramientas que van más allá del autocompletado y pueden entender contexto, ejecutar comandos, refactorizar código y mantener conversaciones técnicas complejas.

Cubrimos:

- **Panorama actual**: Cursor, Claude Code, Windsurf, OpenCode, GitHub Copilot Workspace
- **Cómo funcionan**: System prompts, contexto, herramientas, subagentes
- **Alucinaciones**: Por qué ocurren y cómo detectarlas
- **Estrategias anti-alucinación**: Verificación, prompts estructurados, validación
- **Buenas prácticas**: Gestión de contexto, iteración, delegación efectiva
- **Demo en vivo**: Ejemplo real de trabajo con un agente

---

## 🎓 Temas Clave

### Slides 1-2: Introducción y Panorama
- ¿Qué es un coding agent?
- Panorama de herramientas: Cursor, Claude Code, Windsurf, OpenCode
- Diferencias entre autocompletado y agentes completos

### Slides 3-5: Arquitectura Interna
- **Cómo funcionan**: El loop básico de un agente
- **System Prompt**: La "personalidad" del agente
- **Agentes y Subagentes**: Delegación y especialización

### Slides 6-7: Alucinaciones
- **Qué son**: Generación de código incorrecto pero convincente
- **Por qué ocurren**: Límites del modelo, falta de contexto, ambigüedad
- **Tipos comunes**: APIs inexistentes, parámetros inventados, lógica errónea

### Slides 8-9: Evitando Alucinaciones
- Verificación explícita
- Prompts estructurados y específicos
- Iteración incremental
- Revisión de código asistida

### Slides 10-11: Cierre y Demo
- Buenas prácticas resumidas
- Gestión de contexto efectiva
- Demo en vivo con casos reales

---

## 🚀 Inicio Rápido

### Prerrequisitos
- **Node.js** 18.x o superior
- **pnpm** (recomendado) o npm

### Instalación

```bash
# Clonar el repositorio
git clone https://github.com/CodigoSinSiesta/coding-agents-presentation.git
cd coding-agents-presentation

# Instalar dependencias
pnpm install

# Iniciar servidor de desarrollo
pnpm run dev
```

La presentación estará disponible en **http://localhost:4323**

### Build para Producción

```bash
# Type-check y build
pnpm run build

# Preview del build localmente
pnpm run preview
```

---

## 📁 Estructura del Proyecto

```
coding-agents-presentation/
├── src/
│   ├── components/
│   │   ├── slides/              # 11 slides individuales
│   │   │   ├── Slide01Hero.svelte
│   │   │   ├── Slide02Landscape.svelte
│   │   │   ├── Slide03HowTheyWork.svelte
│   │   │   ├── Slide04SystemPrompt.svelte
│   │   │   ├── Slide05AgentsSubagents.svelte
│   │   │   ├── Slide06Hallucinations.svelte
│   │   │   ├── Slide07AvoidHallucinations.svelte
│   │   │   ├── Slide08BestPractices.svelte
│   │   │   ├── Slide09ContextManagement.svelte
│   │   │   ├── Slide10RealDemo.svelte
│   │   │   └── Slide11Closing.svelte
│   │   └── Navigation.svelte    # Navegación entre slides
│   ├── layouts/
│   │   └── PresentationLayout.astro
│   ├── styles/
│   │   ├── global.css           # Design system tokens + reset
│   │   └── animations.css       # Clases de animación GSAP
│   ├── utils/
│   │   └── animations.ts        # Helpers GSAP
│   └── pages/
│       └── index.astro          # Punto de entrada
├── package.json
├── astro.config.mjs             # Configuración de Astro
└── README.md
```

---

## 🛠️ Stack Tecnológico

### Framework Core
- **[Astro 4.x](https://astro.build)** - Generación de sitio estático
- **[Svelte 5.x](https://svelte.dev)** - Componentes reactivos
- **[TypeScript](https://www.typescriptlang.org)** - Type safety

### Estilos y Animaciones
- **[Tailwind CSS 4.x](https://tailwindcss.com)** - CSS utility-first
- **[GSAP 3.x](https://greensock.com/gsap/)** - Animaciones profesionales
- **CSS Custom Properties** - Sistema de diseño y theming

---

## 💻 Desarrollo

### Comandos Disponibles

```bash
pnpm run dev      # Servidor de desarrollo en http://localhost:4323
pnpm run build    # Build para producción
pnpm run preview  # Preview del build local
```

### Patrón de Slides

Cada slide sigue este patrón:
```svelte
<div class="swiper-slide">
  <div class="slide-content">
    <!-- header: eyebrow + title + subtitle -->
    <!-- main content: grid/layout -->
  </div>
</div>
```

El sistema de navegación se basa en CSS (opacity + visibility) + GSAP para transiciones. **No usa Swiper JS**.

---

## 🎨 Sistema de Diseño

### Paleta de Colores (Tema Azul Monocromático)

```css
--color-base-dark: #0A1628           /* Fondo oscuro */
--color-primary-cobalt: #1E3A8A      /* Elementos primarios */
--color-accent-bright: #3B82F6       /* Call-to-action */
--color-electric: #60A5FA            /* Highlights */
--color-neutral-light: #FAF9F6       /* Texto claro */
```

### Tipografía

- **Display (4-6rem)**: Space Grotesk 800-900 - Títulos principales
- **Subheaders (2-3rem)**: Bricolage Grotesque 600-700 - Subtítulos
- **Body (1-1.2rem)**: IBM Plex Sans 400-500 - Párrafos
- **Monospace**: JetBrains Mono 500 - Código

---

## 🧭 Navegación

- **Teclado**: `←` / `→` para navegar entre slides
- **Botones**: prev/next en los laterales
- **Hash URLs**: `#/slide-name` para enlazar directamente
- **Contador**: muestra "N/11" en esquina inferior derecha

### Nombres de Slides (para hash navigation)

```
hero, landscape, how-they-work, system-prompt, agents-subagents,
hallucinations, avoid-hallucinations, best-practices, 
context-management, real-demo, closing
```

---

## 🔗 Enlaces Rápidos

- **Presentación Live**: https://codigosinsiesta.github.io/coding-agents-presentation/
- **Repositorio**: https://github.com/CodigoSinSiesta/coding-agents-presentation

---

## 📝 Licencia

Este proyecto es open source. Consulta el archivo LICENSE para más detalles.

---

**Hecho con ❤️ por Código Sin Siesta**
