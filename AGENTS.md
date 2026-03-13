# Arrancandonga - AI Agent Documentation

> **Idioma principal del proyecto**: Español (Uruguay)
> 
> Este documento está escrito en español para mantener consistencia con el contenido y comentarios del código fuente.

## Descripción General del Proyecto

**Arrancandonga** es el sitio web de un estudio de Branding y Diseño Estratégico dirigido a emprendedoras. El proyecto tiene dos versiones:

1. **Versión React SPA** (`index.html` en la raíz): Aplicación de página única usando React 18 + Tailwind CSS via CDN
2. **Versión Astro** (`astro-version/`): Versión estática moderna usando Astro 5.x + Tailwind CSS 4.x (versión recomendada)

### Propósito del Sitio
- Presentar servicios de branding, diseño gráfico, desarrollo web y marketing digital
- Mostrar portfolio de proyectos realizados
- Captar leads mediante agendamiento de reuniones (Calendly) y WhatsApp
- Transmitir profesionalismo con un estilo visual colorido y moderno

---

## Estructura del Proyecto

```
arrancandonga/
├── index.html                    # Versión React SPA (legacy)
├── astro-version/               # Versión Astro (recomendada)
│   ├── astro.config.mjs         # Configuración de Astro
│   ├── package.json             # Dependencias y scripts
│   ├── src/
│   │   ├── layouts/
│   │   │   └── Layout.astro     # Layout base con SEO y metatags
│   │   ├── components/
│   │   │   ├── Header.astro     # Navegación sticky + menú mobile
│   │   │   ├── Footer.astro     # Footer con links y CTA WhatsApp
│   │   │   ├── Hero.astro       # Sección principal con CTA
│   │   │   ├── ServicesGrid.astro
│   │   │   ├── ServiceCard.astro
│   │   │   ├── Roadmap.astro    # Proceso de trabajo (6 pasos)
│   │   │   ├── PortfolioPreview.astro
│   │   │   ├── Testimonials.astro
│   │   │   └── Icon.astro       # Componente de íconos SVG
│   │   ├── data/
│   │   │   ├── servicesData.js  # Datos de servicios (8 servicios)
│   │   │   └── projectsData.js  # Datos de proyectos portfolio
│   │   ├── pages/
│   │   │   ├── index.astro      # Página de inicio
│   │   │   ├── portfolio.astro  # Listado de proyectos
│   │   │   ├── servicios/
│   │   │   │   └── [id].astro   # Página dinámica de servicio
│   │   │   └── proyecto/
│   │   │       └── [id].astro   # Página dinámica de proyecto
│   │   └── styles/
│   │       └── global.css       # Estilos globales + Tailwind
│   └── dist/                    # Output de build (generado)
└── [imágenes PNG en raíz]       # Assets de branding
```

---

## Stack Tecnológico

### Versión Astro (Recomendada)
| Tecnología | Versión | Propósito |
|------------|---------|-----------|
| Astro | ^5.17.1 | Framework web estático |
| Tailwind CSS | ^4.2.1 | Estilos y utilidades CSS |
| @tailwindcss/vite | ^4.2.1 | Integración Vite/Tailwind |
| TypeScript | - | Soporte de tipos (en Astro) |

### Versión React SPA (Legacy)
- React 18 (via CDN unpkg)
- React DOM 18 (via CDN)
- Babel Standalone (para JSX en navegador)
- Tailwind CSS (via CDN con configuración inline)

---

## Comandos de Build y Desarrollo

### Versión Astro

```bash
# Navegar al directorio
cd astro-version

# Instalar dependencias
npm install

# Servidor de desarrollo (hot reload)
npm run dev
# o
astro dev

# Build para producción
npm run build
# o
astro build

# Preview del build local
npm run preview
```

### Versión React SPA
No requiere build - es un archivo HTML estático que carga React desde CDN.
Simplemente abrir `index.html` en un servidor web.

---

## Guía de Estilos y Convenciones

### Paleta de Colores
Los colores están definidos en `astro-version/src/styles/global.css`:

```css
--color-brandYellow: #FDB62A;   /* Amarillo principal */
--color-brandPink: #FFBEC6;      /* Rosa */
--color-brandBlue: #6B87C8;      /* Azul */
--color-brandOlive: #AEA433;     /* Verde oliva */
--color-brandOrange: #FE5007;    /* Naranja/Coral */
--color-brandGreen: #25D366;     /* Verde WhatsApp */
--color-brandDark: #1a1a1a;      /* Negro suave */
--color-brandLavender: #E6D5F5;  /* Lavanda */
--color-brandPurple: #6B87C8;    /* Púrpura (mismo que azul) */
--color-cream: #F8F3E0;          /* Fondo crema */
```

### Tipografía
- **Fuente principal**: Poppins (Google Fonts)
- **Pesos disponibles**: 300, 400, 500, 600, 700, 800

### Convenciones de Código

1. **Componentes Astro**: Usar PascalCase (ej: `Header.astro`, `ServiceCard.astro`)
2. **Props de componentes**: Definir interfaz `Props` con tipos explícitos
3. **Datos**: Centralizar en archivos `src/data/*.js`
4. **Estilos**: Usar Tailwind con clases utilitarias; personalizaciones en `global.css`
5. **Colores**: Usar las variables de Tailwind definidas (ej: `bg-brandPink`, `text-brandDark`)

### Animaciones Disponibles
```css
.animate-float           /* Flotación suave (6s) */
.animate-float-reverse   /* Flotación inversa (7s) */
.animate-spin-slow       /* Rotación lenta (25s) */
.animate-marquee         /* Carrusel infinito (20s) */
```

### Clases Utilitarias Custom
```css
.hero-grid    /* Fondo con grilla sutil */
.grain        /* Efecto de grano texturizado */
.btn-lineal   /* Botón con efecto hover suave */
```

---

## Estructura de Datos

### Servicios (`servicesData.js`)
```javascript
{
    id: string,           // Identificador único (ej: 'branding')
    title: string,        // Nombre del servicio
    desc: string,         // Descripción corta
    color: string,        // Clase Tailwind (ej: 'bg-brandYellow')
    iconName: string,     // Nombre del ícono en Icon.astro
    priority: 'high' | 'low'  // Prioridad en grid
}
```

### Proyectos (`projectsData.js`)
```javascript
{
    id: string,           // Identificador numérico
    title: string,        // Nombre del proyecto
    category: string,     // 'identidad' | 'web' | 'social'
    desc: string,         // Descripción corta
    clientReview: string, // Testimonial del cliente
    client: string,       // Nombre del cliente
    year: string,         // Año del proyecto
    services: string[],   // Lista de servicios realizados
    challenge: string,    // Descripción del desafío
    solution: string,     // Descripción de la solución
    image1: string,       // URL imagen principal
    image2: string,       // URL imagen detalle 1
    image3: string       // URL imagen detalle 2
}
```

---

## Páginas y Rutas

| Ruta | Descripción | Componente |
|------|-------------|------------|
| `/` | Página de inicio | `index.astro` |
| `/portfolio` | Listado de proyectos | `portfolio.astro` |
| `/proyecto/[id]` | Detalle de proyecto | `[id].astro` (SSG) |
| `/servicios/[id]` | Detalle de servicio | `[id].astro` (SSG) |

### Rutas Dinámicas
Las páginas de servicios y proyectos usan `getStaticPaths()` para generación estática:

```typescript
export function getStaticPaths() {
    return servicesData.map((service) => ({
        params: { id: service.id },
        props: { service },
    }));
}
```

---

## Componentes Clave

### Icon.astro
Componente unificado para todos los íconos SVG. Props:
- `name`: Nombre del ícono (type-safe con union type)
- `class`: Clases CSS adicionales (opcional)

Íconos disponibles: `Calendar`, `Arrow`, `ArrowRight`, `Instagram`, `WhatsApp`, `Menu`, `Close`, `Star`, `Check`, `Branding`, `Identity`, `Web`, `Social`, `Design`, `Pack`, `Ads`, `Marketing`

### Header.astro
- Navegación sticky con backdrop blur
- Menú hamburguesa para mobile (con animación)
- Links dinámicos desde `servicesData`
- CTA "Agendar" con link a Calendly

### Layout.astro
- Estructura HTML base
- Metatags SEO (Open Graph, Twitter Cards)
- Google Fonts (Poppins)
- Fondo `grain` texturizado

---

## Consideraciones de Diseño

### Principios Visuales
1. **Bordes gruesos**: Uso de `border-4` para elementos con bordes definidos
2. **Bordes redondeados**: Uso extenso de `rounded-2xl`, `rounded-3xl`, `rounded-full`
3. **Sombras suaves**: Efectos `hover:shadow-lg` en tarjetas interactivas
4. **Rotaciones sutiles**: Elementos decorativos con `transform -rotate-1`, `rotate-1`, etc.
5. **Gradientes sutil**: Fondo crema con grilla (`hero-grid`)

### Responsive Design
- Mobile-first approach
- Breakpoints usados: `sm:`, `md:`, `lg:`, `xl:`
- Menú mobile: drawer lateral con animación
- Grid adaptable: 1 col (mobile) → 2 cols (md) → 3 cols (lg)

### Accesibilidad
- Atributos `alt` en todas las imágenes
- Contraste de colores verificado (fondo crema + texto oscuro)
- Scrollbar personalizada con colores de marca
- Focus states en botones interactivos

---

## Integraciones Externas

### Calendly
- URL: `https://calendly.com/arrancandonga-estudiocreativo/conocernos-mejor`
- Usado para agendamiento de reuniones gratuitas

### WhatsApp Business
- Número: `+598 99 928 009`
- Links: `https://wa.me/59899928009`
- Botón flotante fijo en esquina inferior derecha

### Imágenes
- Logo header: CDN externo (estudioforgelab.com)
- Imágenes de portfolio: Unsplash (URLs con parámetros de optimización)
- Assets locales: `arrancandonga-footer-blanco.png`, etc.

---

## Deployment

### Configuración Actual
- **Versión Astro**: Configurada para static site generation (SSG)
- **Output**: Directorio `dist/` (configurado en `.gitignore` para no versionar)

### Recomendaciones de Hosting
- Vercel (optimizado para Astro)
- Netlify
- GitHub Pages
- Cualquier CDN estático

### Variables de Entorno
No se requieren variables de entorno para el funcionamiento básico.

---

## Notas para Desarrolladores

### Al Agregar Nuevos Servicios
1. Agregar entrada en `src/data/servicesData.js`
2. El ícono debe existir en `Icon.astro`
3. Agregar contenido detallado en `src/pages/servicios/[id].astro` (objeto `detailedContent`)

### Al Agregar Nuevos Proyectos
1. Agregar entrada en `src/data/projectsData.js`
2. Rebuild automático generará la nueva ruta estática

### Modificaciones de Estilo
- Preferir modificar `global.css` para cambios globales
- Usar clases utilitarias de Tailwind en componentes
- Mantener consistencia con la paleta de colores existente

### Performance
- Astro genera HTML estático (no hidratación innecesaria)
- Imágenes optimizadas via Unsplash params
- Fonts cargadas con `display=swap`
- Animaciones CSS puras (no JS)

---

## Contacto del Proyecto

- **Email**: hola@arrancandonga.com
- **Teléfono**: +598 99 928 009
- **Ubicación**: Uruguay
- **Sitio en producción**: https://arrancandonga.vercel.app/

---

## Licencia

Proyecto privado - Arrancandonga Estudio Creativo © 2026
