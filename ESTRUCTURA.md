# Estructura del artículo: blog_repository_02_cu

---

## Cómo funciona el HTML

El archivo `index.html` es una página web estática. Todo el contenido va de arriba a abajo, en orden. Cada bloque es una "caja" que ocupa su lugar en la página.

Hay dos tipos de bloques:
- **Siempre visibles** — aparecen cuando cargas la página
- **Ocultos por defecto** — existen en el código pero están invisibles (`display:none`) hasta que el usuario hace click en un botón

---

## Mapa del artículo (de arriba a abajo)

```
┌─────────────────────────────────────────────────┐
│  TOPBAR                                         │
│  ← Blog                                         │
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐
│  HERO                                           │
│  Kicker: Spatial culture · Protest · UNAM       │
│  Título: Ciudad Universitaria as a spatial...   │
│  Byline: By Daniela Reséndiz                    │
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐
│  PÁRRAFO 1                                      │
│  "CU is not merely a backdrop..."               │
│  → tiene glosario: space syntax theory          │
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐
│  PÁRRAFO 2                                      │
│  "Designed in the post-revolutionary context..."│
│  → tiene glosario: co-presence                  │
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐
│  EXPERIENCIA 1: SLIDER (figure#sliderWrap)      │  ← visible
│  ┌───────────────────────────────────────────┐  │
│  │  div#mapSlider                            │  │
│  │  ┌──────────────┬──────────────────────┐  │  │
│  │  │ FONDO        │ FRENTE               │  │  │
│  │  │ unam gris    │ axial map vívido     │  │  │
│  │  │ (siempre     │ (se revela al        │  │  │
│  │  │  visible)    │  arrastrar)          │  │  │
│  │  └──────────────┴──────────────────────┘  │  │
│  │  divisor (la línea blanca + ↔)            │  │
│  └───────────────────────────────────────────┘  │
│  etiquetas: Axial map | Master plan             │
│  caption: Drag to reveal...                     │
└─────────────────────────────────────────────────┘

          BOTÓN: "Explore annotations →"           ← siempre visible
          (al hacer click: oculta EXPERIENCIA 1
           y muestra EXPERIENCIA 2)

┌─────────────────────────────────────────────────┐
│  EXPERIENCIA 2: MAPA ANOTADO (figure#annotatedMap) │  ← oculta por default
│  ┌───────────────────────────────────────────┐  │
│  │  space_syntax_1.png (imagen completa)     │  │
│  │  SVG encima con flechas y anotaciones:    │  │
│  │    • Rectoría                             │  │
│  │    • Las Islas                            │  │
│  │    • Biblioteca Central                   │  │
│  │    • Research institutes                  │  │
│  │    • Frontones                            │  │
│  │  (hover: título en azul, sub-texto)       │  │
│  └───────────────────────────────────────────┘  │
│  leyenda: Global integration (gradiente)        │
│  + mapa de covisibilidad (space_syntax_2)       │
│  + leyenda covisibilidad                        │
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐
│  PÁRRAFO 3                                      │
│  "Unlike gated campuses..."                     │
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐
│  PÁRRAFO 4                                      │
│  "Its spatial form concentrates..."             │
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐
│  GALERÍA DE FOTOS (3 momentos históricos)       │
│  ┌─────────────────────────────────────────┐    │
│  │  1968 · Movimiento estudiantil          │    │
│  │  [foto 1] [foto 2] [foto 3]            │    │
│  └─────────────────────────────────────────┘    │
│  ┌─────────────────────────────────────────┐    │
│  │  2014 · Ayotzinapa                      │    │
│  │  [foto 1] [foto 2]                     │    │
│  └─────────────────────────────────────────┘    │
│  ┌─────────────────────────────────────────┐    │
│  │  2019–2020 · Feminist protests          │    │
│  │  [foto 1] [foto 2] [foto 3]            │    │
│  └─────────────────────────────────────────┘    │
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐
│  PÁRRAFOS DE ANÁLISIS (Hillier + Massey)        │
│  4 párrafos teóricos                            │
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐
│  VIDEO inline                                   │
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐
│  PÁRRAFOS DE CONCLUSIÓN                         │
└─────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────┐
│  REFERENCIAS                                    │
│  Lista alfabética con DOIs                      │
└─────────────────────────────────────────────────┘
```

---

## El problema actual: el botón

El botón "Explore annotations →" necesita vivir en un contenedor que **no se oculte** cuando cambias de experiencia. La solución correcta es:

```
┌─────────────────────────────────────────────────┐
│  div#mapSection  (position: relative)           │
│                                                 │
│  ┌─────────────────────────────────────────┐    │
│  │  EXPERIENCIA 1: #sliderWrap             │    │
│  │  (visible / oculta según botón)         │    │
│  └─────────────────────────────────────────┘    │
│                                                 │
│  ┌─────────────────────────────────────────┐    │
│  │  EXPERIENCIA 2: #annotatedMap           │    │
│  │  (oculta / visible según botón)         │    │
│  └─────────────────────────────────────────┘    │
│                                                 │
│  BOTÓN (position: absolute, esquina)            │
│  → siempre visible porque vive en #mapSection   │
│  → nunca desaparece                             │
└─────────────────────────────────────────────────┘
```

---

## Cómo funcionan los glosarios

Las palabras en azul (*space syntax theory*, *co-presence*) tienen un tooltip oculto dentro del texto. Al pasar el cursor, JavaScript lo posiciona en el margen derecho de la página.

---

## Cómo funcionan las galerías

Cada foto tiene un `figcaption` oculto. Al pasar el cursor sobre la foto, aparece el texto con fondo negro semitransparente (overlay).

---

## Archivos de imagen usados

| Imagen | Uso |
|--------|-----|
| `unam_layout_escalado_inv.png` | Fondo del slider (plano gris) |
| `space_syntax_escalado_viv.png` | Frente del slider (axial vívido) |
| `space_syntax_1.png` | Mapa anotado completo |
| `space_syntax_2.png` | Mapa de covisibilidad |
| `unam_68.webp`, `unam_68_2.webp`, `unam_68_3.jpeg` | Galería 1968 |
| `unam_fem*.jpg` | Galería feminista 2019–2020 |
| `unam_43*.jpg` | Galería Ayotzinapa 2014 |
