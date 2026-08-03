# Project Intelligence & Structural Observations: Portfolio Cloud

Este documento centraliza las observaciones técnicas y estructurales del portfolio desarrollado por Juan Carlos Díaz, diseñado bajo una arquitectura de múltiples páginas estáticas (MPA) con un alto enfoque en fidelidad visual y micro-interacciones.

## 1. Arquitectura del Proyecto
- **Modelo:** Multi-Page Application (MPA).
- **Tecnologías:** HTML5, CSS3 (Custom Variables, Grids, Flexbox), Vanilla JavaScript.
- **Estructura de Archivos:** Flat structure (todos los archivos en el root).
- **Navegación:** Sistema de Hub-and-Spoke. El `index.html` actúa como núcleo central que distribuye a proyectos específicos (`nexusgrid.html`, `soltech_english.html`, etc.).

## 2. Observaciones de Ingeniería de Software

### Fortalezas
- **Variables CSS:** Excelente uso de `:root` para mantener temas coherentes por cada sub-marca de proyecto.
- **Performance Visual:** Uso de `requestAnimationFrame` para animaciones de Canvas y backgrounds, con optimizaciones recientes para evitar loops permanentes cuando no hay animación visible.
- **Interacciones:** Implementación de cursores personalizados y efectos de scroll reveal que elevan la percepción de calidad (Polished UI).
- **Seguridad:** Uso correcto de `target="_blank"` con `rel="noopener noreferrer"` en los enlaces externos.

### Áreas de Mejora (Deuda Técnica)
- **Duplicación de Código:** Elementos globales (Google Analytics, Cursor logic, Nav/Footer) están replicados manualmente en cada archivo.
    - *Sugerencia:* Mover a un generador de sitios estáticos (SSG) como Astro o Jekyll para usar componentes reutilizables.
- **Asset Management:** Los estilos y scripts están inline dentro de los archivos HTML. Esto dificulta el caching del navegador y el mantenimiento.
- **Accesibilidad (A11y):** Algunos elementos decorativos y enlaces con `role="button"` podrían mejorar su semántica para lectores de pantalla.

## 3. Desglose de Proyectos (Micro-Brands)
Cada página del portfolio fue diseñada con un lenguaje visual único:
1. **Lighttown Barbershop:** Sitio web realizado por encargo para una barbería neerlandesa (crema/bordó/dorado, estética retro y barber pole animado).
2. **ForoBardo:** Producto comunitario full-stack real (negro/crema/naranja, wordmark inclinado tipo sticker, estética dura de foro/media platform), conservado en hide dentro del grid principal.
3. **Emma 3.0:** Asistente IA local-first e híbrido con LangChain/RAG, compatible con modelos locales y servicios externos (azules eléctricos, lente/punto azul sobre base blanco-cyan, interfaz técnica).
4. **Emma Node:** La misma versión funcional de Emma reconstruida con Node.js y React (verde Node/cian React, interfaz técnica emparentada con Emma 3.0).
5. **Aesthetic Store:** Catálogo de referencias visuales frontend para humanos y agentes IA (cian/coral/lima, cards compactas, estética de biblioteca visual).
6. **AI Mascot:** Widget JavaScript embebible para mascotas de IA (verde/turquesa/lima, amigable, API pequeña, logo sonriente).
7. **Audiobook Generator TTS:** Pipeline local XTTS para audiolibros (violeta/cian/ámbar, icono de onda de audio, enfoque long-form/ACX).
8. **CodeRisk AI / PR Sentinel:** Reviewer de riesgo para pull requests asistido por IA (púrpura/cian/ámbar, dashboard técnico, icono tipo escudo/sentinel), conservado en hide dentro del grid principal.
9. **NexusGrid:** Estética Cyberpunk/High-tech (Azules/Cian, Share Tech Mono), conservado en hide dentro del grid principal.
10. **SolTech:** Fusión Solar-Tech (Naranjas/Amarillos, Outfit/Rajdhani), conservado en hide dentro del grid principal.
11. **Verdant:** Diseño Orgánico/Sostenible (Verdes/Menta, DM Sans), conservado en hide dentro del grid principal.
12. **Lumex:** Neon-Futurism (Púrpuras/Cian, Exo 2), conservado en hide dentro del grid principal.
13. **TalkingDutch:** Branding Institucional Holandés (Rojo/Blanco/Azul/Naranja), conservado en hide dentro del grid principal.

## 4. Estado de los Componentes Críticos

| Componente | Estado | Notas |
| :--- | :--- | :--- |
| **Global Cursor** | Operacional | Replicado en múltiples archivos con variaciones de color. |
| **Canvas background** | Optimizado | Flash en `index.html` y `contact.html` se agenda por ráfagas; Lumex limita partículas y FPS. |
| **Formulario de Contacto** | UI Only | El frontend es robusto, pero requiere integración con un backend o servicio (Formspree/Netlify) para la funcionalidad. |
| **SEO / Meta** | Básico | Se recomienda estandarizar las etiquetas OpenGraph y meta-descriptions en todas las páginas. |
| **Certificación PCAP** | Visible | `index.html` enlaza `certificate_XkrV.RHDC.X8CV.pdf` desde un CTA secundario debajo de `Contact`. |

## 5. Estado Actual del Portfolio Principal
- **Nombre visible:** El hero principal y la página de contacto usan `Juan Carlos Díaz`; `Juan Carlos` permanece en blanco y `Díaz` mantiene el tratamiento azul/degradado del glitch.
- **Responsive del nombre:** `index.html` y `contact.html` mantienen el nombre en una sola línea mediante `white-space: nowrap` y breakpoints específicos para evitar overflow horizontal en narrow viewports. En `contact.html`, el `h1` usa una banda full-bleed (`width: 100vw` + `margin-left: calc(50% - 50vw)`) para centrar el nombre contra el viewport, no contra el ancho de la tarjeta de contacto.
- **CTAs del hero:** En desktop, `Contact` y `PCAP Certification` aparecen debajo de la bio; en narrow, ambos quedan centrados aunque el texto del hero esté alineado a la izquierda.
- **Orden visible del grid:** `Lighttown Barbershop`, `Emma 3.0`, `Emma Node`, `Aesthetic Store`, `AI Mascot` y `Audiobook Generator TTS`.
- **Privacidad / Ubicación:** `index.html` y `contact.html` no muestran ubicación personal; cualquier referencia visible heredada a la ciudad anterior debe reemplazarse por `Buenos Aires` y mantenerse en inglés.
- **Performance de animaciones:** El efecto de relámpago en `index.html` y `contact.html` ya no corre en un loop continuo de `requestAnimationFrame`; se agenda por ráfagas, pausa con `document.hidden` y respeta `prefers-reduced-motion`.
- **Lumex:** `lumex.html` conserva su identidad neon, pero su card permanece en `card-hidden`; el canvas de partículas se limitó a 30fps, con menos partículas, pausa por pestaña oculta y cursor custom throttleado por RAF.
- **SolTech:** La card de `soltech_english.html` permanece en `card-hidden`; su espacio visible fue reemplazado por AI Mascot.
- **Verdant:** La card de `verdant.html` permanece en `card-hidden`; su espacio visible fue reemplazado por Aesthetic Store.
- **NexusGrid:** La card de `nexusgrid.html` permanece en `card-hidden`; el proyecto sigue disponible por URL directa y como micro-brand documentado.
- **Lighttown Barbershop:** La card visible enlaza `https://lighttown-barbershop.nl/` y presenta el sitio realizado por encargo en Países Bajos con HTML, CSS y JavaScript.
- **ForoBardo:** La card enlaza `https://forobardo.net/` pero permanece en `card-hidden`; usa `forum.html` como referencia visual local para el wordmark y sistema negro/crema/naranja.
- **Emma Node:** La card visible enlaza `https://github.com/sistaterro/emma_node` y presenta la misma versión de Emma reconstruida con Node.js y React.
- **TalkingDutch:** La card enlaza `https://talkingdutch.com/` pero permanece en `card-hidden`.
- **CodeRisk AI:** La card enlaza `https://github.com/sistaterro/coderisk_ai` pero permanece en `card-hidden`.
- **Audiobook Generator TTS:** La card visible enlaza `https://github.com/sistaterro/audiobook_generator_tts` y resume el producto como pipeline local XTTS para convertir scripts narrables en WAV/MP3 con voces curadas, limpieza de silencios, merge y export ACX-style.

## 6. Roadmap de Refactorización Recomendado
1. **Extracción de Assets:** Mover los bloques `<style>` y `<script>` a archivos `.css` y `.js` externos compartidos.
2. **Normalización de GA:** Centralizar el script de Google Tag Manager para evitar errores de medición entre páginas.
3. **Optimización de Imágenes:** Asegurar que los favicons y cualquier imagen futura utilicen formatos modernos (WebP/SVG).
4. **Lógica de Contacto:** Implementar feedback visual (Toast notifications) cuando el usuario interactúa con los formularios.

---
*Documento actualizado para reflejar el estado actual del portfolio y las últimas decisiones de implementación.*
