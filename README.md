# Arrancandonga - Estudio Creativo

> **Caso de Estudio: Desarrollo Web para Estudio de Branding y Diseño Estratégico**
>
> Sitio web corporativo con gestión de portfolio, servicios y casos de estudio para emprendedoras.

---

## 📋 Resumen del Proyecto

**Arrancandonga** es el sitio web oficial de un estudio creativo uruguayo especializado en branding, diseño estratégico y marketing digital dirigido a emprendedoras. El proyecto incluye un sistema completo de gestión de portfolio con 14 casos de estudio reales, páginas de servicios dinámicas y una experiencia de usuario moderna y optimizada.

### Objetivos Alcanzados
- ✅ Sitio multi-página estático de alto rendimiento
- ✅ Sistema de portfolio con 14 proyectos categorizados
- ✅ Páginas de servicios dinámicas (SSG)
- ✅ Carruseles interactivos 3D para contenido social
- ✅ Métricas y visualización de datos (Instagram growth)
- ✅ Diseño responsive mobile-first
- ✅ SEO optimizado con meta tags dinámicos
- ✅ Performance 100/100 en Lighthouse

---

## 🚀 Stack Tecnológico

### Core Framework
| Tecnología | Versión | Propósito |
|------------|---------|-----------|
| **Astro** | ^5.17.1 | Framework web estático con Islands Architecture |
| **TypeScript** | 5.x | Tipado estático para robustez |
| **Tailwind CSS** | ^4.2.1 | Estilos utilitarios y diseño system |
| **@tailwindcss/vite** | ^4.2.1 | Integración Vite/Tailwind nativa |

### Ventajas de Astro seleccionadas
- **Zero JS by default**: Solo se hidrata lo necesario
- **SSG nativo**: Generación estática en build time
- **Rutas dinámicas**: `getStaticPaths()` para páginas de proyecto/servicio
- **Optimización automática**: Imágenes, fuentes, bundles

---

## 🏗️ Arquitectura del Proyecto

```
arrancandonga/
├── public/                     # Assets estáticos
│   ├── casos-de-estudio/       # 42 imágenes .webp del portfolio
│   ├── *.png                   # Logos, iconos, favicons
│   └── favicon.*               # Multi-format favicon
├── src/
│   ├── components/             # Componentes Astro reutilizables
│   │   ├── Header.astro        # Navegación sticky + mobile menu
│   │   ├── Footer.astro        # Footer con CTAs
│   │   ├── Hero.astro          # Sección principal
│   │   ├── ServicesGrid.astro  # Grid de servicios
│   │   ├── ServiceCard.astro   # Tarjeta individual
│   │   ├── PortfolioPreview.astro
│   │   ├── Testimonials.astro
│   │   ├── Roadmap.astro       # Proceso de trabajo
│   │   └── Icon.astro          # Sistema de íconos SVG
│   ├── data/
│   │   ├── projectsData.js     # 14 proyectos con challenge/solution
│   │   └── servicesData.js     # 8 servicios con metadatos
│   ├── layouts/
│   │   └── Layout.astro        # Layout base + SEO
│   ├── pages/
│   │   ├── index.astro         # Homepage
│   │   ├── portfolio.astro     # Listado de proyectos
│   │   ├── proyecto/
│   │   │   └── [id].astro      # Página dinámica de proyecto
│   │   └── servicios/
│   │       └── [id].astro      # Página dinámica de servicio
│   └── styles/
│       └── global.css          # Tailwind + custom CSS
└── astro.config.mjs            # Configuración SSG
```

---

## 🎨 Sistema de Diseño

### Paleta de Colores
```css
--color-brandYellow: #FDB62A;   /* Primario - CTAs, acentos */
--color-brandPink: #FFBEC6;      /* Fondos de sección */
--color-brandBlue: #6B87C8;      /* Elementos secundarios */
--color-brandOlive: #AEA433;     /* Detalles */
--color-brandOrange: #FE5007;    /* Highlights, links */
--color-brandDark: #1a1a1a;      /* Texto, bordes */
--color-brandLavender: #E6D5F5;  /* Fondos alternativos */
--color-brandGreen: #25D366;     /* WhatsApp */
--color-cream: #F8F3E0;          /* Fondo base */
```

### Tipografía
- **Fuente**: Poppins (Google Fonts)
- **Pesos**: 300, 400, 500, 600, 700, 800
- **Escala**: Fluida con `clamp()` para responsiveness

### Patrones Visuales
- **Bordes**: `border-4` (4px) con `border-brandDark`
- **Radios**: `rounded-2xl` (16px), `rounded-3xl` (24px), `rounded-full`
- **Sombras**: `shadow-[6px_6px_0px_#27272A]` (efeto "neubrutalismo" suave)
- **Decorativos**: Grids sutil, efecto grano, rotaciones `-1deg` a `1deg`

---

## ⚡ Features Destacadas

### 1. Carrusel 3D de Reels (Edesia Social Media)
- Implementación con `transform-style: preserve-3d`
- Navegación circular con `rotateY()` y `translateZ()`
- Lazy loading de thumbnails
- Responsive: adaptativo a mobile/desktop

### 2. Métricas Instagram con Chart.js
- Gráfico de barras con gradientes personalizados
- Timeline de 5 meses (Enero → Mayo)
- Animación de entrada progresiva
- Tooltips interactivos

### 3. Sistema de Portfolio Dinámico
- Rutas dinámicas: `/proyecto/[id].astro`
- `getStaticPaths()` genera 14 páginas en build
- Relación bidireccional entre proyectos (ej: Edesia Identidad ↔ Social)
- Galería con modal de imágenes

### 4. Páginas de Servicio SSG
- Cada servicio tiene su propia URL: `/servicios/{id}`
- Contenido detallado con pasos, deliverables, precios
- Componentes condicionales por tipo de servicio

### 5. Modal de Imágenes
- Navegación prev/next
- Cierre con ESC o click fuera
- Transiciones suaves
- Accesible (ARIA labels)

---

## 🛠️ Prácticas de Desarrollo

### Performance
- **Imágenes**: Formato WebP con fallbacks
- **Lazy loading**: `loading="lazy"` en imágenes debajo del fold
- **CSS crítico**: Inlined en Layout.astro
- **Fuentes**: `display=swap` para FOUT controlado
- **Zero JS**: Astro no envía JS innecesario al cliente

### SEO
- Meta tags dinámicos por página (`title`, `description`, `og:image`)
- Canonical URLs
- Schema.org básico
- Sitemap.xml (generado automáticamente)

### Accesibilidad
- Contraste de colores verificado (WCAG AA)
- Navegación por teclado completa
- ARIA labels en elementos interactivos
- Alt text obligatorio en imágenes
- Focus states visibles

### Código
- **Componentes**: Principio de responsabilidad única
- **Datos**: Centralizados en `src/data/*.js`
- **Estilos**: Tailwind + clases utilitarias custom
- **TypeScript**: Tipado estricto en props

---

## 📦 Scripts Disponibles

```bash
# Instalación
npm install

# Desarrollo (hot reload)
npm run dev        # localhost:4321

# Build producción
npm run build      # Genera dist/ estático

# Preview local
npm run preview    # Servir dist/ localmente
```

---

## 🚀 Deployment

### Configuración
- **Output**: Static Site Generation (SSG)
- **Directorio build**: `dist/`
- **Base URL**: `/` (root)

### Plataformas recomendadas
| Plataforma | Configuración |
|------------|---------------|
| **Vercel** | Build command: `npm run build`, Output: `dist` |
| **Netlify** | Publish directory: `dist` |
| **GitHub Pages** | Funciona con `base: '/repo-name'` en config |

---

## 📸 Casos de Estudio Documentados

1. **Edesia Café** - Identidad visual completa
2. **Edesia Café - Social Media** - Gestión de redes + métricas
3. **Orillas Concept Store** - Branding lifestyle
4. **Escribanía Patrón** - Identidad corporativa
5. **FRAVAS Accesorios** - Branding producto
6. **Mar Ruíz English Academy** - Identidad educativa
7. **Marga Confecciones** - Rebranding textil
8. **Nutridamente** - Social media nutrición
9. **Óptica Rochas Visión** - Marketing local
10. **Panadería San Antonio** - Branding gastronómico
11. **Panes Artesanos Javier Muñoz** - Identidad artesanal
12. **Personal Shopper** - Desarrollo web
13. **Picot** - Diseño gráfico
14. **Vení a la Fiesta!** - Identidad eventos

Cada caso incluye: desafío, solución detallada, imágenes (banner, mockup, miniatura), testimonial del cliente y año.

---

## 🔗 Integraciones Externas

| Servicio | Uso | URL |
|----------|-----|-----|
| Calendly | Agendamiento reuniones | `/conocernos-mejor` |
| WhatsApp Business | Contacto directo | `wa.me/59899928009` |
| Google Fonts | Tipografía Poppins | fonts.google.com |

---

## 📄 Licencia

Proyecto privado - Arrancandonga Estudio Creativo © 2026

Desarrollado con ❤️ en Uruguay

---

## 📝 Notas de Mantenimiento

### Para agregar nuevos proyectos:
1. Agregar entrada en `src/data/projectsData.js`
2. Copiar imágenes a `public/casos-de-estudio/`
3. Re-build automático genera la nueva ruta

### Para agregar servicios:
1. Agregar en `src/data/servicesData.js`
2. Agregar contenido detallado en `src/pages/servicios/[id].astro`
3. Incluir ícono en `Icon.astro` si es necesario

---

**Versión**: 2.0 (Migración Astro)  
**Última actualización**: Marzo 2026  
**Estado**: ✅ Producción
