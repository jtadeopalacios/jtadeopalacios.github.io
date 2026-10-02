# Página web de Tadeo Palacios Valverde

Sitio publicado en **https://jtadeopalacios.github.io**. GitHub Pages lo construye automáticamente con Jekyll cada vez que se guarda un cambio; la actualización tarda entre uno y tres minutos en verse.

## Qué hay en cada carpeta

| Archivo o carpeta | Para qué sirve |
|---|---|
| `index.html` | La página completa: textos, secciones y diseño. |
| `_posts/` | Las entradas del blog, una por archivo. |
| `_data/actividades.yml` | Lista de actividades y eventos. |
| `_data/galeria.yml` | Lista de fotos y videos de la galería. |
| `galeria/` | Aquí se suben las fotos y los videos propios. |
| `archivos/` | Aquí se suben los PDF de ensayos y artículos. |
| `portadas/` | Portadas de los libros. |
| `_drafts/plantilla-de-entrada.md` | Plantilla para copiar al crear una entrada nueva. |
| `entradas.json`, `actividades.json`, `galeria.json`, `_layouts/`, `_config.yml` | Archivos técnicos. **No hace falta tocarlos.** |

---

## 1. Publicar una entrada en el blog

1. En GitHub, entra a la carpeta `_posts` y pulsa **Add file → Create new file**.
2. Escribe el nombre con este formato exacto: `AAAA-MM-DD-titulo-sin-tildes.md`
   Ejemplo: `2026-10-15-notas-sobre-churata.md`
   La fecha del nombre es la fecha de la entrada; el resto será su dirección web (`/blog/notas-sobre-churata/`).
3. Pega este bloque al inicio y complétalo:

```
---
title: "Título de la entrada"
categoria: "Ensayo"
resumen: "Una o dos líneas que aparecerán en la lista de entradas."
---

Aquí empieza el texto. Cada párrafo se separa con una línea en blanco.
```

4. Pulsa **Commit changes**. La entrada aparecerá en **Últimas entradas**, en **Todas las entradas** y en el **Archivo** por año y mes.

**Campos opcionales** (se agregan debajo de `resumen`):

- `imagen: "/galeria/foto.jpg"` muestra una imagen de portada. Sube antes la foto a la carpeta `galeria`.
- `archivo: "/archivos/mi-ensayo.pdf"` agrega un PDF que se puede leer en pantalla o descargar. Sube antes el PDF a la carpeta `archivos`.
- `enlace: "https://..."` agrega un botón hacia la publicación original en otra web.

**Formato del texto:** `*cursiva*`, `**negrita**`, `## Subtítulo`, `> cita en bloque`, y notas al pie con `texto[^1]` y, al final, `[^1]: texto de la nota.`

Para **editar** una entrada, ábrela en `_posts` y pulsa el lápiz. Para **borrarla**, ábrela y usa los tres puntos → **Delete file**.

> Si el texto lleva comillas dobles dentro del título o del resumen, usa comillas latinas « » o comillas simples para no romper el formato.

---

## 2. Agregar una actividad o evento (con sus fotos)

1. **Si tienes fotos del evento**, súbelas primero a la carpeta `galeria`: entra a la carpeta, pulsa **Add file → Upload files** y arrástralas. Usa nombres sin tildes ni espacios, por ejemplo `aladaa-2026-1.jpg`, `aladaa-2026-2.jpg`.
2. Abre `_data/actividades.yml` y pulsa el lápiz.
3. Copia este bloque, pégalo **arriba de todas las actividades** (debajo de las líneas que empiezan con `#`) y cambia los datos:

```
- fecha: "2026-11-18"
  fecha_fin: "2026-11-20"
  titulo: "Nombre del congreso o actividad"
  lugar: "Institución, ciudad"
  descripcion: "Ponencia: «Título de la ponencia»."
  linkedin: "https://www.linkedin.com/posts/tadeopalacios_..."
  instagram: "https://www.instagram.com/p/XXXXXXXX/"
  enlace: ""
  fotos:
    - "/galeria/aladaa-2026-1.jpg"
    - "/galeria/aladaa-2026-2.jpg"
```

4. Pulsa **Commit changes**.

**Reglas de formato:**
- La primera línea empieza con guion; las demás llevan **dos espacios** al inicio; cada foto lleva **cuatro espacios**, un guion y la ruta entre comillas.
- Las fechas van entre comillas con el formato `AAAA-MM-DD`. Si la actividad dura un solo día, borra la línea `fecha_fin`.
- Los campos que no uses pueden quedar vacíos (`""`) o borrarse. Si aún no tienes fotos, borra las líneas de `fotos`.

**Qué hace la página con esos datos:**
- Las actividades con fecha futura aparecen en **Próximas** y pasan solas a **Realizadas** cuando termina la fecha.
- Las fotos se muestran como miniaturas en la tarjeta del evento; al pulsarlas se abren en grande y se recorren con flechas.
- Esas mismas fotos aparecen **automáticamente en la Galería**, en **Todo**, **Fotos** y **De eventos**, con el nombre del evento como título. No hace falta repetirlas en `galeria.yml`.

**Agregar fotos a un evento que ya existe** (por ejemplo, uno que pasó de Próximas a Realizadas): sube las fotos a `galeria`, busca la actividad en `actividades.yml` y añade al final de su bloque:

```
  fotos:
    - "/galeria/nombre-de-la-foto.jpg"
```

**Enlaces de redes:** en LinkedIn, pulsa los tres puntos de tu publicación → **Copiar enlace a la publicación**; en Instagram, los tres puntos → **Copiar enlace**. Con cualquiera de los dos aparece el botón **Ver publicación aquí**, que muestra la publicación dentro de tu página.

---

## 3. Agregar fotos y videos a la galería

1. Sube la foto o el video a la carpeta `galeria` (**Add file → Upload files**). Usa nombres sin tildes ni espacios, por ejemplo `presentacion-fil-2026.jpg`.
2. Abre `_data/galeria.yml`, pulsa el lápiz y agrega un bloque arriba de todo:

Foto:
```
- tipo: "foto"
  archivo: "/galeria/presentacion-fil-2026.jpg"
  titulo: "Presentación en la FIL Lima"
  fecha: "2026-07-20"
  descripcion: "Texto breve"
```

Video de YouTube (el código es lo que sigue a `watch?v=` en el enlace):
```
- tipo: "video"
  youtube: "5RN82l5wHlI"
  titulo: "Tráiler de Mañana nunca llega"
```

Video propio (archivo `.mp4` de menos de 25 MB):
```
- tipo: "video"
  archivo: "/galeria/lectura.mp4"
  titulo: "Lectura en la Casa de la Literatura"
```

Usa `galeria.yml` para fotos y videos que no pertenecen a un evento (retratos, lecturas, entrevistas). Las fotos de eventos se agregan desde `actividades.yml`, como se explica en el punto 2. Las pestañas **Fotos**, **Videos** y **De eventos** aparecen solas cuando hay contenido de cada tipo.

---

## 4. Activar el formulario de comentarios (una sola vez)

El formulario de la pestaña **Contacto** envía los mensajes a `tadeo.palacios@pucp.edu.pe` mediante el servicio gratuito FormSubmit.

1. Cuando la página ya esté publicada, envía tú mismo un comentario de prueba desde el formulario.
2. Llegará a tu correo un mensaje de **FormSubmit** con el asunto *Action Required: Activate Form*. Pulsa **Activate Form**. Revisa también la carpeta de spam.
3. Desde ese momento, cada comentario llegará a tu bandeja con el nombre, el correo y el mensaje del lector.

Para recibirlos en otra dirección, abre `index.html`, busca `data-email="tadeo.palacios@pucp.edu.pe"` y cambia la dirección en ese atributo y en el `action` de la línea siguiente. Tendrás que activar de nuevo el formulario.

---

## 5. Cambiar textos de la página

Los textos de **Sobre mí**, **Trayectoria**, **Obra**, **Podcasts** y **Contacto** están en `index.html`. Ábrelo, pulsa el lápiz, usa **Ctrl + F** para buscar la frase y edítala. Cada sección está marcada con un comentario visible, por ejemplo `<!-- ========== PODCASTS ========== -->`.

## 6. Tu foto

Sube una foto cuadrada con el nombre exacto `foto.jpg` a la carpeta principal. Reemplazará automáticamente el círculo con las iniciales.
