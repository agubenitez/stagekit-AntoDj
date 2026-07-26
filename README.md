# StageKit Core — LandingDJ

LandingDJ es el primer producto del ecosistema **StageKit Core**, una landing page premium, moderna, accesible y altamente personalizable diseñada específicamente para DJs y artistas de eventos en vivo.

Este proyecto ha sido concebido bajo una arquitectura robusta, modular y completamente declarativa, permitiendo desplegar múltiples landings independientes para diferentes DJs modificando exclusivamente un archivo de configuración JSON externo, recursos multimedia y variables de estilo.

## Arquitectura y Stack

El proyecto utiliza un stack de nivel de producción alineado con los objetivos de StageKit Core:

- **Framework**: Next.js 15 (App Router, React Server Components) para optimización de SEO, Server-Side Rendering y máxima velocidad de carga.
- **Estilos**: Tailwind CSS (v4) con ~75 variables CSS dinámicas inyectadas desde la configuración.
- **Animaciones**: Motion (`motion/react` v12) para transiciones premium y micro-interacciones suaves.
- **Tipografía**: Catálogo predefinido con fuentes de Google Fonts cargadas de forma óptima.
- **Validación de Configuración**: Zod para verificar que la configuración sea robusta y segura antes del renderizado.
- **Servicios**: Arquitectura de correo electrónico desacoplada (Email Services) con un patrón Provider para evitar el acoplamiento con intermediarios específicos.
- **Tours Dinámicos**: Integración con Google Sheets (CSV público) para gestión de eventos en tiempo real sin deploy.

---

## Estructura de Documentación (`/docs`)

Para asegurar la continuidad del desarrollo por cualquier desarrollador o IA, la documentación está organizada en los siguientes documentos clave:

1. **[PROJECT_CONTEXT.md](./docs/PROJECT_CONTEXT.md)**: Visión del negocio, alcance de LandingDJ y objetivos del producto. *(Léase primero)*.
2. **[DECISIONS.md](./docs/DECISIONS.md)**: Bitácora de decisiones arquitectónicas y técnicas (ADRs), justificando cada elección.
3. **[ROADMAP.md](./docs/ROADMAP.md)**: Planificación de fases desde la fundación hasta el lanzamiento de la v1 y escalamiento.
4. **[PROJECT_STATE.md](./docs/PROJECT_STATE.md)**: Estado actual del proyecto, componentes completados, tareas pendientes y estado de los builds.
5. **[CONFIG_GUIDE.md](./docs/CONFIG_GUIDE.md)**: Guía completa de reconfiguración vía JSON con ejemplos prácticos.
6. **[IMPROVEMENTS.md](./docs/IMPROVEMENTS.md)**: Catálogo de ideas de mejora para aumentar el dinamismo vía JSON.
7. **[AI_HANDOVER.md](./docs/AI_HANDOVER.md)**: Instrucciones específicas y contexto técnico detallado para asistentes de IA que retomen el proyecto.
8. **[CONVENTIONS.md](./docs/CONVENTIONS.md)**: Convenciones técnicas de desarrollo, estructura de carpetas y estándares de código.
9. **[ActiveTask.md](./docs/ActiveTask.md)**: Registro de la última tarea completada con contexto histórico.

---

## Como Iniciar el Proyecto

### Requisitos Previos

- Node.js (v18.x o superior)
- npm (v9.x o superior)

### Instalacion

```bash
npm install
```

### Desarrollo

Para iniciar el servidor de desarrollo en el puerto 3000:

```bash
npm run dev
```

### Produccion

Para compilar y arrancar la version de produccion:

```bash
npm run build
npm run start
```

---

## Reconfiguracion via JSON

Este proyecto se personaliza integramente editando `config/landingdj.config.json`. No necesitas tocar codigo React para cambiar contenido, colores, secciones o SEO.

| Categoria | Campo clave en el JSON | Que cambia |
|-----------|------------------------|------------|
| Identidad | `artisticName`, `slogan`, `description`, `logo`, `favicon` | Nombre del artista/marca, eslogan, logo y favicon del sitio |
| Design Presets | `designPreset`, `validDesignPresets` | 12 presets visuales con ~75 tokens (colores, tipografia, radios, sombras, animaciones) |
| Hero | `hero.url`, `.ctaText`, `.layout` | Imagen o video de portada, texto del CTA y layout (default/titles) |
| BioConFoto | `bioConFoto.url`, `bioConFotoTexts.*` | Seccion de presentacion con imagen + texto (Split Editorial) |
| Servicios | `services[]` | Lista de servicios/productos con titulo, descripcion e icono |
| Equipamiento | `equipment[]` | Rider tecnico con categorias e iconos |
| Galeria | `gallery[]` | Hasta 10 imagenes en grilla responsiva |
| Videos | `videos[]` | Hasta 10 videos de YouTube con lazy loading |
| Songs | `songs[]` | Tracks embedidos (SoundCloud, Spotify, Apple Music) |
| Music | `music[]`, `musicTexts.*`, `musicSoundCloudVisual` | Tracks embedidos con visual mode para SoundCloud |
| FAQ | `faq[]` | Hasta 10 preguntas frecuentes con acordeon |
| Tours | `tours[]`, `toursSource`, `toursSheetUrl` | Fechas de shows (estatico o via Google Sheets dinamico) |
| Redes Sociales | `socials.*` | Links a Instagram, SoundCloud, Spotify, etc. |
| Contacto | `contactForm`, `destinationEmail`, `whatsapp` | Formulario, email destino, WhatsApp |
| Textos | `*Texts.*` | Todos los labels, placeholders, headings y mensajes |
| Orden de secciones | `sectionOrder` | Reordena las secciones (hero, bio, services, etc.) |
| SEO | `seo.title`, `.description`, `.keywords`, `.ogImage` | Meta tags, Open Graph, keywords |

> Para la guia completa con todos los campos en detalle, ejemplos de reconfiguracion (incluyendo como convertir esta landing en una tienda de presets) y los limites del JSON -> **[`docs/CONFIG_GUIDE.md`](./docs/CONFIG_GUIDE.md)**
