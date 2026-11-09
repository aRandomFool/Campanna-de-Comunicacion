# Campaña de Comunicación — Mercado Automotriz La Habana

**Proyecto:** Ciencia de Datos (1er año) — Universidad de La Habana  
**Web:** https://arandomfool.github.io/ICD-Mercado-Automotriz/  
**Objetivo:** Visitas e interacciones en la web para la nota final  
**Presupuesto:** 0 € (solo tiempo)  
**Métrica principal:** Evento `interaccion` en GA4 (personas que tocaron al menos un control)

---

## 1. Resumen ejecutivo

Campaña 100% digital, sin inversión económica, centrada en **grupos de Facebook y Telegram especializados en compraventa de autos en Cuba**. El activo principal es la web interactiva ya publicada (3.566 anuncios, 83 modelos formales, 30 entrevistas) y una imagen OG con las 3 cifras gancho. Se mide todo con GA4 + bitácora manual.

---

## 2. Audiencias y canales

| Audiencia | Canales objetivo | Plantilla | Gancho principal |
|---|---|---|---|
| Compradores/vendedores en La Habana | FB: compraventa general, Revolico, clasificados<br>TG: autos Cuba, carros La Habana | A | Brecha 10.699 USD, 48,9% sin año, checklist |
| Dueños/aficionados por marca | FB: Hyundai, Kia, Toyota, Nissan, Dongfeng, Lada, BMW<br>TG: canales por marca | B | Precios reales de SU marca (informal vs formal) |
| Prescriptores: mecánicos, repuestos, mipymes | FB/Telegram: repuestos, talleres, importadoras, mipymes autos | C | Mantenimiento real 200–3.000 USD/año (30 entrevistas) |
| Diáspora que compra para familia | FB: cubanos en Miami, España, envíos carros a Cuba | D | Precios reales, riesgos (sin año), checklist antes de enviar dinero |

**Criterio de grupos:** >5.000 miembros, actividad diaria, temática 100% autos. No grupos genéricos ni de memes.

---

## 3. Estrategia de contenido

### 4 plantillas (en `plantillas_posts.txt`)

| Plantilla | Uso | Datos clave |
|---|---|---|
| **A** | Compraventa general | 3.566 anuncios, brecha 10.699, 48,9% sin año, mantenimiento 200–3k, calculadora, checklist, catálogo |
| **B** | Por marca | Rellenar con tabla de `datos_rapidos.txt` (anuncios, mediana informal, modelos formales, mediana formal) |
| **C** | Repuestos/mecánicos/mipymes | Combustible 2–2,80 USD/L, reparaciones 200–3k, piezas dificultad alta, neumáticos 60–80, baterías 300 |
| **D** | Diáspora | Medianas 22k/32k, 48,9% sin año, mantenimiento 200–3k, checklist 6 pasos |

### Imagen única
- `campana-card.png` (1200×630, Open Graph 1.91:1)
- 3 cifras grandes: 10.699 USD | 48,9% | 200–3.000 USD
- URL + QR placeholder + "Proyecto UH · Gratis · Sin cookies"

### Mensaje para admins (privado)
> "Hola! Soy estudiante de la UH. Hice un análisis de datos del mercado de autos (3.566 anuncios Revolico, 83 modelos comercializadoras, 30 entrevistas). ¿Me permites compartir el link? No vendo nada, es info gratis y útil. Adjunto captura."

### Horarios pico (hora Cuba)
- **Facebook:** 11:00–13:00 | 19:00–21:00
- **Telegram:** Día "libre" del canal o mayor actividad histórica

---

## 4. Infraestructura técnica

### Analítica (GA4)
- **ID:** `G-XXXXXXXXXX` (configurado en `index.html` raíz, no en `web/`)
- **Tag:** `gtag.js` en `<head>` con `anonymize_ip: true`
- **Eventos personalizados** (`assets/js/analitica.js`):
  - 14 eventos de interacción (`interactivo_*`, `checklist_*`, `clic_fuente`, `compartir_*`)
  - 1 marcador de sesión: `interaccion` (primera interacción real)
  - 2 de consumo: `bloque_visto`, `tiempo_lectura` (no marcan `interaccion`)
- **Eventos clave marcados en GA4:** `interaccion`, `checklist_descargar`, `compartir_*`, `clic_fuente`
- **Dimensiones personalizadas:** `bloque`, `tipo`, `campo`, `item`, `destino`, `rango_presupuesto`, `percentil`, `utm_content`

### UTMs (28 únicos en `utm_links.csv`)
Formato: `?utm_source=facebook|telegram&utm_medium=grupo|canal&utm_campaign=autos_uh&utm_content=NOMBRE_GRUPO`
- 18 Facebook (5 general + 6 marcas + 4 repuestos + 3 diáspora)
- 10 Telegram (3 general + 3 marcas + 3 repuestos + 1 noticias)

### Bitácora (`bitacora_campana.csv`)
Columnas: `fecha, canal, grupo_canal_exacto, plantilla_usada, utm_content_usado, link_corto_usado, alcance_estimado_miembros, usuarios_ga4, evento_interaccion_ga4, comentarios_respuestas, notas`

### Panel público (Looker Studio)
- Conectado a GA4
- Tarjetas: Usuarios, Sesiones, Eventos, **Evento `interaccion` (usuarios)**
- Tabla: `Session source/medium` × Usuarios × `interaccion`
- Serie temporal: Usuarios/día
- Compartido: "Cualquiera con el enlace puede ver" → link en pie de web

---

## 5. Flujo de trabajo diario

1. **Preparar:** Abrir `datos_rapidos.txt` → copiar link UTM → acortar en `is.gd` → copiar link corto
2. **Publicar:** Texto (plantilla) + `campana-card.png` + link corto en **primer comentario**
3. **Responder:** TODOS los comentarios en ≤1 hora (dato + "más en el link")
4. **Registrar:** Pegar link corto en `bitacora_campana.csv` → `link_corto_usado`
5. **Cada 24h:** GA4 → Adquisición → Tráfico → filtrar por `utm_content` → anotar `usuarios_ga4` y `evento_interaccion_ga4` en bitácora
6. **Decidir:** Top 3 grupos por `interaccion` → duplicar esfuerzo; 0 interacciones en 48h → no repetir

---

## 6. Calendario 7 días

| Día | Acciones | Meta |
|---|---|---|
| **1** | Unirse 15 FB + 8 TG, pedir permiso a 10 admins, publicar en 5 donde ya eres miembro | 5 publicaciones |
| **2** | Publicar en 10–12 grupos FB (A/B según marca) + 4–5 canales TG, responder comentarios | 15–17 publicaciones |
| **3** | Plantilla C en 5 grupos repuestos/mecánicos/mipymes + Plantilla D en 3 grupos diáspora | 8 publicaciones nicho |
| **4** | "Analizamos tu anuncio gratis" (5 cupos) en 3 grupos FB grandes | Engagement + comentarios |
| **5** | Revisar GA4: top 3 grupos por `interaccion` → republicar en esos con plantilla distinta (checklist) | Duplicar lo que funciona |
| **6** | Segunda ronda en 5 mejores grupos: "Actualicé dato X / nueva calculadora" | Recapturar audiencia |
| **7** | Bitácora completa + captura panel Looker Studio + export CSV GA4 | Evidencia para nota |

---

## 7. KPIs y evaluación

| Métrica | Definición | Meta (3 semanas) |
|---|---|---|
| **Visitantes únicos** | GA4: Usuarios totales | 500–800 |
| **Tasa de interacción** | Usuarios con evento `interaccion` / Usuarios totales | ≥35% |
| **Interacciones/visitante** | Total eventos `interactivo_*`, `checklist_*`, `compartir_*`, `clic_fuente` / Usuarios | ≥2 |
| **Compartidos** | Suma `compartir_whatsapp`, `compartir_facebook`, `compartir_telegram`, `compartir_copiar` | ≥30 |
| **Canales activos** | Fuentes (`utm_source` + `utm_content`) con ≥1 `interaccion` | ≥5 |
| **Calidad** | % móvil, tiempo lectura `3m+`, `checklist_descargar` | Monitorear |

**Para la nota:** Captura panel Looker Studio + export CSV GA4 + bitácora completada + tabla resumen por canal.

---

## 8. Archivos generados (en `/Campanha_de_Comunicacion/`)

| Archivo | Descripción |
|---|---|
| `utm_links.csv` | 28 links con UTM únicos (canal, grupo, plantilla, link completo) |
| `bitacora_campana.csv` | Plantilla de seguimiento (28 filas pre-cargadas) |
| `plantillas_posts.txt` | 4 plantillas A/B/C/D + mensaje admin + horarios + seguimiento GA4 |
| `datos_rapidos.txt` | Hoja de trucos: 28 UTMs listos, tabla por marca, cifras maestras, acortadores, checklist diario |
| `campana-card.svg` | Vectorial editable (Figma/Inkscape/Illustrator) |
| `campana-card.png` | **1200×630 px, 103 KB** — lista para publicar |

---

## 9. Riesgos y ética

- **No bots, no autorefresco, no granjas de clics** — se detecta (sesión 1s, rebote 100%, geo única) y es deshonesto académicamente
- **No spam sin permiso** — pide autorización a admins; aporta valor antes de pedir
- **GA4 usa cookies (`_ga`)** — actualizado pie de privacidad: "Usamos Google Analytics 4 para contar visitas e interacciones agregadas. No recopilamos nombres, correos ni datos de contacto. Google Analytics usa cookies; puedes inhabilitarlo con el complemento oficial o un bloqueador."
- **Sin PII** — eventos no envían texto libre, emails, nombres. `visitante_id` anónimo solo para agrupar en hoja opcional
- **Conectividad Cuba** — probar carga real en datos móviles; si `googletagmanager.com` falla, GA4 no registra (tener plan B: contador ligero)
- **Bloqueadores** — subestiman visitas; reportar como "visitantes únicos estimados (GA4, cookies opcionales)"

---

*Documento generado para la campaña de comunicación del proyecto "Mercado Automotriz de La Habana" — Ciencia de Datos, Universidad de La Habana, 2026.*