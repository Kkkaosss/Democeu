# DEMOCEU · Web de 6.º B (EP), Es Liceu

Web estática preparada para GitHub Pages. Respeta la estructura de los prototipos Canva: portada DEMOCEU, bloque «¿Quiénes somos?», accesos a las tres categorías y recomendaciones, páginas de categoría, ajustes, formulario y horarios.

## Archivos

- `index.html`: estructura y contenido de las páginas.
- `styles.css`: diseño responsive, temas y animaciones.
- `script.js`: navegación, traducciones, productos, lista de deseados, ajustes, música y formulario.
- `config.js`: endpoint de Formspree (vacío hasta configurarlo).
- `audio/musica.mp3`: archivo de audio que has proporcionado.
- `assets/producto-01.svg` … `producto-09.svg`: imágenes provisionales; sustitúyelas por las fotos de vuestros productos conservando los nombres o cambia las rutas en `PRODUCTS` dentro de `script.js`.

## Publicar en GitHub Pages

1. Entra en [https://github.com](https://github.com) e inicia sesión. Si no tienes cuenta, pulsa **Sign up** y sigue los pasos de registro y verificación.
2. Pulsa **New** (o el símbolo `+` y después **New repository**). Ponle un nombre, por ejemplo `democeu`, elige **Public** y pulsa **Create repository**.
3. En el repositorio, pulsa **Add file → Upload files**. Arrastra el contenido de esta carpeta (no la carpeta contenedora): `index.html`, `styles.css`, `script.js`, `config.js`, `README.md`, y las carpetas `audio` y `assets`. Conserva exactamente los nombres y las carpetas. Pulsa **Commit changes**.
4. El MP3 ya está en `audio/musica.mp3`. Si en el futuro lo cambias, sube el nuevo archivo con ese mismo nombre y ruta. Ten en cuenta que el MP3 que has adjuntado ocupa aproximadamente 172 MB: es un archivo muy pesado y puede superar límites de subida de GitHub o hacer que la web tarde mucho en cargar. Recomendación: exportar una versión MP3 más ligera (por ejemplo, 128 kbps y duración recortada) antes de publicarla. No subas archivos mayores de los límites que indique GitHub.
5. Abre **Settings → Pages**. En **Build and deployment**, selecciona **Deploy from a branch**. En **Branch**, elige `main` y carpeta `/ (root)`. Pulsa **Save**.
6. Espera a que termine la publicación. En **Settings → Pages** aparecerá el enlace público, normalmente `https://TU-USUARIO.github.io/democeu/`.
7. Para actualizar la web, abre el archivo que quieras en GitHub y pulsa el lápiz (**Edit**) para cambiar texto/código, o vuelve a **Add file → Upload files** para subir imágenes/audio. Confirma con **Commit changes**. GitHub Pages publicará la actualización automáticamente al cabo de unos minutos.

## Cambiar productos, precios e imágenes

Abre `script.js` y busca `const PRODUCTS = [...]` al principio. Cada objeto tiene:

- `id`: identificador único (no repetirlo).
- `category`: `cat1`, `cat2` o `cat3`.
- `image`: ruta a la imagen, por ejemplo `assets/producto-01.svg`.
- `emoji`: icono de respaldo (opcional).
- `name`: nombre en `es`, `ca` y `en`.
- `description`: descripción en los tres idiomas.
- `price`: precio que se muestra.

Para usar una foto real, súbela a `assets` (JPG, PNG o WebP) y cambia el valor de `image`. Por ejemplo: `image:'assets/llavero-azul.jpg'`. Repite los cambios de nombre y descripción en los tres idiomas para que el catálogo siga completamente traducido. Puedes duplicar un objeto para añadir más productos.

Las imágenes SVG incluidas son solo marcadores provisionales. Sustituidlas por fotos reales cuando tengáis el catálogo definitivo.

## Conectar el formulario de recomendaciones (Formspree)

GitHub Pages solo sirve archivos estáticos: no recibe ni almacena formularios por sí mismo. Para recibir recomendaciones sin montar un servidor, se ha preparado una integración con **Formspree**.

1. Entra en [https://formspree.io/](https://formspree.io/) y crea una cuenta.
2. Crea un formulario nuevo y configura el correo receptor del grupo/docente. Verifica la dirección si el servicio lo solicita.
3. Copia el endpoint que te facilita Formspree, con formato `https://formspree.io/f/xxxxxxxx`.
4. Abre `config.js` y cambia la línea para poner tu endpoint real, por ejemplo:
   `window.DEMOCEU_FORM_ENDPOINT = 'https://formspree.io/f/abcdefgh';`
5. Guarda y vuelve a subir `config.js` al repositorio.

Hasta que no se configure el endpoint, el formulario muestra un aviso y **no finge que se ha enviado nada**. Una vez conectado, solo mostrará la confirmación si Formspree devuelve una respuesta correcta. Revisa las condiciones y límites del plan gratuito de Formspree.

## Temas, idiomas y accesibilidad

- El tema, idioma, tipografía accesible y lista de deseados se guardan en `localStorage` del navegador del visitante.
- Los tres idiomas están centralizados en el objeto `I18N` de `script.js`.
- Los textos visibles, botones, avisos, lista de deseados, categorías, ajustes, recomendaciones y horarios se traducen.
- La opción de tipografía accesible usa **Atkinson Hyperlegible**, cargada desde Google Fonts. Si prefieres alojarla localmente, descarga los archivos de fuente permitidos y decláralos con `@font-face` en `styles.css`.
- La bandera catalana se representa con el emoji de bandera de Cataluña; la apariencia puede variar según el sistema operativo.

## Música y autoplay

La web intenta iniciar la música al cargar, pero los navegadores suelen bloquear autoplay con sonido. El botón flotante permite activarla manualmente y silenciarla; al primer toque/clic en la página también se vuelve a intentar la reproducción. El estado de silencio se conserva localmente. El MP3 se reproduce en bucle.

## Pruebas rápidas

- Menú: botón «Menú», X y clic en el fondo para cerrar.
- Navegación: inicio, categorías, recomendaciones, horarios, ajustes y lista.
- Tema: alterna rojo/negro y blanco/rosa; comprueba la transición.
- Idioma: cambia con banderas y desde Ajustes; comprueba cada sección.
- Lista: añade y elimina productos; recarga para comprobar persistencia.
- Accesibilidad: activa/desactiva la tipografía desde Ajustes.
- Formulario: sin endpoint debe mostrar aviso de configuración; tras conectarlo, prueba un envío real.
- Música: comprueba el botón de sonido después de permitir la reproducción.

> Nota: al ser una web estática, no hay carrito de compra, pagos ni pedidos. La lista de deseados se guarda únicamente en el dispositivo/navegador del visitante; no se comparte entre dispositivos.
