# Invitación de boda web — Guía completa

Contenido de la carpeta:

```
invitacion/
├── index.html     ← la invitación (aquí se editan textos y datos)
├── LEEME.md       ← esta guía
└── assets/        ← aquí van TUS archivos (fotos, música, PNG)
```

---

## 1. Cambiar tus archivos (assets)

Copia tus archivos dentro de `assets/` **con estos nombres exactos** (así no tocas nada de código).
Si un archivo no existe, la invitación muestra un cuadro gris en su lugar, sin romperse.

| Archivo | Qué es | Recomendado |
|---|---|---|
| `flores.png` | Flores en la esquina del sobre | PNG con **fondo transparente**, ~800 px de ancho |
| `iniciales.png` | (Opcional) Tu monograma ya diseñado. Si no lo pones, se genera uno automático con tus 2 letras fusionadas | PNG con **fondo transparente**, ~600 px |
| `sobre1.jpg`, `sobre2.jpg` | Las 2 fotos que salen del sobre | Verticales, ~800 px de ancho |
| `foto1.jpg` … `foto4.jpg` | Galería estilo polaroid | ~1000 px de ancho |
| `final.jpg` | Foto final | ~1000 px de ancho |
| `portada.jpg` | Imagen que aparece al compartir el link en WhatsApp | 1200×630 px |
| `cancion.mp3` | Tu canción (solo suena cuando el invitado toca **play**) | MP3, idealmente < 5 MB |
| `ambiente.mp3` | Música de fondo suave, en bucle (suena sola al abrir el sobre) | MP3 instrumental, 1–3 MB |
| `disco.jpg` | Foto para el disco que gira (opcional) | **Cuadrada**, ~600×600 px |
| `ic-ceremonia.png`, `ic-foto.png`, `ic-cocktail.png`, `ic-comida.png`, `ic-tarta.png`, `ic-fiesta.png` | Iconos del itinerario | PNG transparente, ~300 px |

**Consejos**
- **Comprime las fotos** antes de subirlas (https://squoosh.app o https://tinypng.com). Cada foto debería pesar menos de 300 KB para que cargue rápido en celular.
- Para quitar el fondo de tus iniciales o iconos: https://www.remove.bg
- Si quieres otros nombres de archivo, cámbialos en el bloque `img` y `itinerario` dentro de `index.html`.
- Para **fotos a color**, pon `blancoYNegro: false`.
- Si quieres más o menos fotos en la galería, agrega o quita líneas en `galeria`.

---

## 2.0 Monograma (tus 2 iniciales fusionadas)

Hay dos formas de tenerlo:

1. **Automático (ya incluido):** en `monograma` cambia las letras y los colores. Las dos letras se encuentran, se fusionan y quedan dentro de un aro que se dibuja solo.
   ```
   monograma: {a:"S", b:"Y", color1:"#b09676", color2:"#8a7156"}
   ```
2. **Tu propio diseño:** crea tu monograma en Canva (o donde prefieras), expórtalo como **PNG con fondo transparente**, llámalo `iniciales.png` y ponlo en `assets/`. Si existe, la invitación lo usa en lugar del automático.

El monograma también aparece en el sello del sobre, en la etiqueta del disco de música y al final de la invitación.

---

## 2. Cambiar textos y datos

Abre `index.html` con un editor de texto (Bloc de notas, VS Code, o el editor de tu celular).
Busca el bloque **PERSONALIZA AQUÍ**. Solo cambia lo que está entre comillas `" "`:

- `nombres`, `fecha` (formato `AAAA-MM-DDTHH:MM:SS`), `fechaTexto`
- `cita`, `padres`, `itinerario`, `dress`, `cierre`
- `lugares`: nombre, horario y **dirección** (con la dirección se generan el mapa y los botones de Google Maps y Waze)
- Colores: al inicio del `<style>`, cambia `--acento` (tono principal), `--trigo` y `--cafe` (tonos de apoyo), `--sh` (color de las sombras en RGB), `--arena` (sobre), `--crema` (fondo) y `--papel` (tarjetas) por tus colores. El sobre y sus pliegues tienen tonos propios (`#b9a283`, `#cdb99c`, `#e6d8c2`) en la sección `.env`.

También cambia el `<title>` y las líneas `og:title` / `og:description` del inicio (es lo que se ve al compartir el link).

---

## 2.1 Datos marcados como "Colocar ..."

Todo lo que no se sabía aparece en la invitación como una nota en cursiva con subrayado punteado, por ejemplo *Colocar nombre del padre*.
Búscalas en `index.html` (Ctrl+F → `Colocar`) y reemplaza el texto por el dato real:

- Nombres de padres y padrinos (`padres`)
- Nombre, hora y dirección de cada lugar (`lugares`). **Al poner una dirección real aparecen el mapa y los botones de Google Maps y Waze.** Mientras diga "Colocar", se muestra un recuadro avisando.
- Horas del itinerario (`itinerario`)
- Fecha límite de confirmación (`asistencia.limite`)
- Nombre y artista de la canción (`cancion`)
- Número de WhatsApp (`asistencia.whatsapp`). Vacío = no se abre WhatsApp, pero igual se muestra el agradecimiento.

## 2.2 Efectos y animaciones

En `efectos` puedes encender o apagar cada detalle poniendo `true` o `false`:

```
efectos: {hojas:true, corazones:true, brillos:true, mariposas:true, toque:true, ramas:true, marco:true, grano:true}
```

- `hojas`: hojitas en beige, salvia, rosa, dorado y terracota que caen girando
- `corazones`: corazoncitos y florecitas que suben suavemente
- `brillos`: estrellitas que parpadean y luces suaves que flotan
- `mariposas`: tres mariposas que cruzan la pantalla
- `toque`: destellos cuando el invitado toca la pantalla
- `ramas`: ramas decorativas que se mecen en los bordes
- `marco`: doble marco fino alrededor de la pantalla
- `grano`: textura de papel sobre el fondo

Reproductor: el disco gira, las barras de sonido bailan y salen notitas mientras suena la canción. Si quieres otros colores para las hojas, edita la lista `PAL` en el script.

Otros movimientos: sello que se rompe con destellos, texto letra por letra, itinerario que entra desde los lados, fotos con parallax y cuenta regresiva con giro. Si el celular del invitado tiene activada la opción "reducir movimiento", todo se muestra sin animaciones.

---

## 2.3 Música y disco

- **Ambiente** (`ambiente.mp3`): música suave de fondo que empieza sola al abrir el sobre y se repite en bucle.
- **Canción** (`cancion.mp3`): solo suena cuando el invitado toca **play**. Mientras suena, el ambiente baja de volumen hasta apagarse y vuelve suavemente cuando pausa o termina.
- Ajusta los volúmenes en `volumen` (de 0 a 1). Si quieres que el ambiente siga sonando bajito durante la canción, pon por ejemplo `ambienteConCancion: .1`.
- Pon el nombre en `cancion` (título y artista).
- El botón flotante ♪ silencia o activa todo el sonido.
- Controles del reproductor: play/pausa, retroceder 10 s, adelantar 10 s, barra para saltar a cualquier parte, volumen y tiempo.
- **Disco que gira:** guarda una foto cuadrada como `assets/disco.jpg`.
  - `modo: "completo"`: la foto cubre todo el disco.
  - `modo: "etiqueta"`: la foto solo va en el centro, como la etiqueta de un vinilo.
  - Sin foto, se muestra un disco beige con tus iniciales.
- Mientras suena: el disco gira, el brazo baja sobre él, brilla un halo, bailan las barras de sonido y flotan notitas.

---

## 3. Links personalizados por invitado

Un mismo archivo sirve para todos. Agrega al final de tu link:

```
https://tu-pagina.com/?invitado=Familia%20Perez&pases=3
```

- Muestra "Invitación para Familia Perez" en la portada.
- Ajusta el texto "Pase para (3) personas".
- Limita el número de personas en el formulario de asistencia.

Usa `%20` en lugar de espacios. Puedes generar todos los links en una hoja de cálculo.

---

## 4. Confirmación de asistencia

El formulario funciona de dos maneras (puedes usar una o las dos):

### A) Por WhatsApp (ya funciona)
En `asistencia.whatsapp` pon tu número con código de país, sin `+` ni espacios (México: `5215512345678`).
Al confirmar, el invitado ve un agradecimiento y se abre WhatsApp con el mensaje ya escrito para enviártelo.

### B) Lista automática en Google Sheets (opcional, gratis)
1. Crea una hoja en https://sheets.google.com con encabezados en la fila 1: `Fecha | Nombre | Asiste | Personas | Mensaje`.
2. Menú **Extensiones → Apps Script**, borra lo que haya y pega:

```javascript
function doPost(e) {
  const d = JSON.parse(e.postData.contents);
  SpreadsheetApp.getActiveSheet().appendRow([d.fecha, d.nombre, d.asiste, d.personas, d.mensaje]);
  return ContentService.createTextOutput("ok");
}
```
3. **Implementar → Nueva implementación → Tipo: Aplicación web**. Ejecutar como: *Yo*. Quién tiene acceso: *Cualquier persona*. Autoriza los permisos.
4. Copia la URL que termina en `/exec` y pégala en `asistencia.endpoint` dentro de `index.html`.

Desde ese momento cada confirmación aparece como una fila nueva en tu hoja.

---

## 5. Mapa y calendario

- Cambia las direcciones en `lugares`. Puedes poner una o varias (ceremonia, recepción…).
- Escribe la dirección como la buscarías en Google Maps (nombre del lugar + ciudad funciona muy bien).
- El botón **Agregar al calendario** descarga un evento con la fecha y la primera ubicación. La duración se ajusta con `duracionHoras`.

---

## 6. Probarla en tu computadora o celular

- **Computadora:** doble clic en `index.html`. Necesitas internet para las fuentes y el mapa.
- **Música:** los navegadores solo reproducen audio después de un toque; por eso el ambiente arranca al tocar el sobre.
- Revisa siempre en celular antes de mandarla.

---

## 7. Publicarla como página web (gratis)

### Opción más fácil: Netlify Drop (sin cuenta técnica, 2 minutos)
1. Entra a https://app.netlify.com/drop (crea cuenta gratis con tu correo).
2. **Arrastra la carpeta `invitacion` completa** a la zona indicada.
3. Te da un link tipo `https://nombre-random.netlify.app`.
4. En *Site configuration → Change site name* ponle uno bonito: `georgina-y-jacob.netlify.app`.
5. Para actualizar algo: en *Deploys* arrastra la carpeta de nuevo.

### Opción: GitHub Pages
1. Crea cuenta en https://github.com y un repositorio público nuevo (por ejemplo `boda`).
2. **Add file → Upload files** y sube `index.html` y la carpeta `assets`.
3. **Settings → Pages → Source: Deploy from a branch → main / (root) → Save**.
4. En 1–2 minutos queda en `https://tu-usuario.github.io/boda/`.

### Opción: Cloudflare Pages o Vercel
Igual que Netlify: creas cuenta, eliges subir una carpeta (o conectar GitHub) y te dan el link.

### Opción: tu propio hosting o dominio
Sube `index.html` y `assets/` por FTP o por el administrador de archivos a la carpeta `public_html`.

### Dominio propio (opcional, ~$12 USD al año)
Compra un dominio (Namecheap, GoDaddy, Cloudflare), por ejemplo `georginaYjacob.com`, y en el panel de Netlify/GitHub/Vercel usa **Add custom domain** y sigue sus pasos. Ellos te dicen qué registros DNS poner. El HTTPS es automático.

### Después de publicar
- Prueba el link en tu celular y en otro (iPhone y Android).
- Pega el link en WhatsApp para ver la vista previa (imagen `portada.jpg`).
- Genera un **código QR** del link en https://qr.io o https://www.qrcode-monkey.com para imprimirlo en invitaciones físicas.
- Manda los links personalizados (sección 3) a cada invitado.

---

## 8. Problemas comunes

| Problema | Solución |
|---|---|
| No se ve una foto | Revisa que el nombre sea idéntico (mayúsculas y extensión: `foto1.jpg`, no `Foto1.JPG`) |
| No suena la música | La **canción** solo suena al tocar *play*. El **ambiente** arranca al abrir el sobre. Revisa que se llamen `cancion.mp3` y `ambiente.mp3` y estén en `assets/` |
| Carga lenta | Comprime fotos y usa un MP3 más ligero |
| Se actualizó pero veo lo anterior | Recarga forzada o abre el link en modo incógnito |
| El mapa sale en otro lugar | Escribe la dirección completa con ciudad y país |
| No llegan confirmaciones al Sheet | Verifica que la implementación tenga acceso "Cualquier persona" y que pegaste la URL `/exec` |
