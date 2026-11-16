# Campaña de Comunicación — Mercado Automotriz La Habana

Repositorio con la infraestructura completa de la campaña digital (0 € presupuesto) para impulsar visitas e interacciones a la web del proyecto de Ciencia de Datos: **https://arandomfool.github.io/ICD-Mercado-Automotriz/**

---

## 📁 Estructura y descripción de archivos

### Documentos principales
| Archivo | Descripción |
|---------|-------------|
| `CAMPANA_MERCADO_AUTOMOTRIZ.md` | Documento maestro: estrategia, audiencias, 4 plantillas, calendario 7 días, KPIs, riesgos, ética |
| `Informe_panorámico.pdf` | Informe final formateado para entrega académica (capturas GA4, bitácora, conclusiones) |
| `Link_web.txt` | URL canónica de la web interactiva publicada |

### Datos y tracking
| Archivo | Columnas / Contenido | Uso |
|---------|---------------------|-----|
| `utm_links.csv` | `canal, grupo_canal, plantilla, utm_content, link_completo, link_corto_pendiente` | **18 links UTM únicos** (solo Facebook) con link corto is.gd |
| `bitacora_campana.csv` | `fecha, canal, grupo_canal_exacto, plantilla_usada, utm_content_usado, link_corto_usado, alcance_estimado_miembros, usuarios_ga4, evento_interaccion_ga4, comentarios_respuestas, notas` | Seguimiento diario de las 18 publicaciones en grupos FB |
| `datos_rapidos.txt` | UTMs listos para copiar, tabla por marca (11 marcas), 10 cifras maestras, acortadores, checklist diario | Hoja de trabajo día a día |

### Contenido creativo
| Archivo | Especificaciones | Uso |
|---------|-----------------|-----|
| `plantillas_posts.txt` | 4 plantillas (A: general, B: marca, C: repuestos, D: diáspora) + mensaje admin + horarios pico + guía GA4 | Copy-paste directo a grupos Facebook |
| `campana-card.svg` | Vectorial editable, 1200×630 px, capas separadas | Modificar cifras/colores en Figma/Inkscape/Illustrator |
| `campana-card.png` | **1200×630 px, 103 KB, ratio 1.91:1 (OG estándar)** | Imagen adjunta en cada publicación |

---

## 🎯 Resumen de la campaña (solo Facebook)

- **18 grupos de Facebook** especializados en compraventa de autos en Cuba
- **4 plantillas** según audiencia: compraventa general (A), por marca (B), repuestos/mecánicos (C), diáspora (D)
- **1 link UTM único por grupo** → acortado con is.gd → registrado en bitácora
- **Métrica principal:** evento `interaccion` en GA4 (usuario toca al menos un control interactivo)
- **Panel de resultados:** Looker Studio conectado a GA4 (público "cualquiera con el enlace")

---

## 📅 Ejecución (7 días)

| Día | Acción | Grupos FB |
|-----|--------|-----------|
| 1 | Unirse, pedir permisos, primeras 5 publicaciones | 5 |
| 2 | Plantilla A (compraventa) + Plantilla B (marcas) | 11 |
| 3 | Plantilla C (repuestos) + Plantilla D (diáspora) | 7 |
| 4 | "Analizamos tu anuncio gratis" (engagement) | 3 |
| 5 | Revisión GA4 → republicar en top 3 | 3 |
| 6 | 2ª ronda en 5 mejores grupos | 5 |
| 7 | Bitácora completa + capturas + export GA4 | — |
| 8 | **Entrega** | — |

**Total: 18 publicaciones únicas + 8 republicaciones estratégicas = 26 posts**

---

## 🔧 Infraestructura técnica

- **GA4:** `G-XXXXXXXXXX` en `index.html` raíz + `assets/js/analitica.js` (14 eventos custom + marcador `interaccion`)
- **UTMs:** 18 únicos (`utm_source=facebook`, `utm_medium=grupo`, `utm_campaign=autos_uh`, `utm_content=slug_grupo`)
- **Links cortos:** is.gd (gratis, sin cuenta) — todos guardados en `utm_links.csv`

---

## 📄 Licencia / Uso académico

Proyecto de 1er año Ciencia de Datos — Universidad de La Habana, 2026.  
Libre para uso educativo y como plantilla de campañas sin presupuesto.