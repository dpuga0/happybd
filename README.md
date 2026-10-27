# happybd · Una carta para Danna

Página personal de cumpleaños creada por Diego para Danna. Presenta un mensaje de bienvenida y una carta que se abre en un modal, con una estética de tonos rosados, pétalos animados y un diseño de una sola columna pensado para pantallas pequeñas.

La aplicación está contenida en [`index.html`](index.html): HTML, CSS y JavaScript sin frameworks ni proceso de compilación.

## Alcance de la verificación

Esta documentación se basa en la lectura de `index.html` en la rama `main` el 27 de octubre de 2026, con SHA de archivo `c4bcd62bd04a2f9de53d9f39bb67db3e38df9f73`.

**Confirmado en el código:**

- Idioma `es`, codificación UTF-8 y metadatos `viewport`, `theme-color`, `description` y `title`.
- Botón **Abrir carta**, modal y cierre mediante **×**, clic o toque en el fondo exterior y tecla **Escape**.
- Bloqueo del desplazamiento del cuerpo al abrir la carta y foco inicial en el botón de cierre.
- Animaciones CSS, ajuste a pantallas de hasta 390 px y respeto de `prefers-reduced-motion`.
- Estilos y lógica integrados en el HTML. No se referencian scripts, hojas de estilo, fuentes remotas, API, analítica ni servicios externos. No hay formularios funcionales, almacenamiento de datos ni backend en este archivo.

**Informado por el propietario, sin verificación independiente en esta revisión:**

- El repositorio estaba compuesto únicamente por `index.html` y está publicado en GitHub Pages.

**Pendiente de verificar:**

- Configuración efectiva de Pages, rama de publicación, dominio y disponibilidad del sitio desplegado.
- Funcionamiento real en iPhone y escritorio, rendimiento, contraste y experiencia con lectores de pantalla. La presencia de reglas responsive y atributos ARIA no equivale a una certificación de compatibilidad o accesibilidad.

## Archivos y estructura

| Archivo | Función |
| --- | --- |
| `index.html` | Página completa y su comportamiento. |
| `README.md` | Documentación de uso, personalización, despliegue y pruebas. |

Dentro de `index.html`:

| Bloque | Contenido |
| --- | --- |
| `<head>` | Metadatos y título de la pestaña. |
| `<style>` | Variables en `:root`, colores, tipografías, tarjetas, modal, animaciones y media queries. |
| `.petals` | Seis elementos decorativos, ocultos a tecnologías de asistencia con `aria-hidden="true"`. |
| `main.page` | Portada `.hero`, panel, botón, mensaje visible, recordatorios y firma. |
| `#letter-overlay` | Fondo del modal y carta `.letter`, con título, mensaje, firma y cierre. |
| `<script>` | Referencias a botones y overlay, funciones `openLetter()` y `closeLetter()`, y eventos de clic y teclado. |

Existen estilos para `input`, `label` y `.secondary`, pero no controles correspondientes en el HTML actual. El mensaje `#message-box` ya incluye `is-visible`; no se genera dinámicamente.

## Abrir en local

1. Descarga el repositorio o clónalo si tienes Git:

   ```bash
   git clone https://github.com/dpuga0/happybd.git
   cd happybd
   ```

2. Abre `index.html` en un navegador con JavaScript habilitado.
3. Edita el archivo en un editor de texto y recarga la página.

No se requiere instalar paquetes ni ejecutar un build. Como alternativa, si tienes Python 3, puedes iniciar un servidor local desde la carpeta del proyecto:

```bash
python -m http.server 8000
```

Abre [http://localhost:8000](http://localhost:8000). Este servidor es una herramienta opcional para desarrollo, no una dependencia de la página.

## Personalizar la carta

Edita los textos directamente en el HTML; no existe un panel de configuración.

| Qué cambiar | Dónde |
| --- | --- |
| Nombre de la destinataria | `<title>Para Danna</title>`, `<h1>Para Danna</h1>` y saludo dentro de `#message-box`. Busca también apodos y menciones en la carta. |
| Introducción y mensaje breve | `.lead`, texto introductorio de `.panel` y `#message-box`. |
| Carta completa | Contenido de `<p id="letter-body">`. |
| Título del modal | `#letter-title`. |
| Recordatorios y emojis | Elementos `.detail`. |
| Autor y despedida | `.signature` y `.letter-sign`. |
| Descripción de la página | `<meta name="description">`. |

El cuerpo de la carta usa `white-space: pre-line`: los saltos de línea escritos dentro de `#letter-body` se reflejan en la presentación. Conserva la etiqueta de apertura y cierre. Si necesitas mostrar caracteres como `<` o `&` literalmente, utiliza `&lt;` o `&amp;`.

Mantén los identificadores `open-letter`, `close-letter` y `letter-overlay`, porque el JavaScript los utiliza. Conserva también la relación entre `aria-labelledby` y los títulos correspondientes.

### Colores, tipografía y dimensiones

- Ajusta las variables de `:root`, especialmente `--rose`, `--rose-deep`, `--wine`, `--ink`, `--muted`, `--card`, sombras y radios.
- Hay colores escritos directamente en degradados, bordes y fondos. Cambiar únicamente las variables no recolorea toda la página. Algunas variables declaradas no se utilizan.
- Actualiza `theme-color` por separado si cambias el color principal.
- Las fuentes se definen en `body` y `h1, h2`; son familias locales con alternativas, por lo que su apariencia puede variar entre dispositivos.
- `.page` limita el ancho a 460 px y `.letter` a 440 px. En escritorio se conserva la composición estrecha centrada.
- La media query `max-width: 390px` coloca los recordatorios en una columna.
- Ajusta `floatBlob`, `petalFall` y sus duraciones para cambiar las animaciones. Conserva el bloque de movimiento reducido.

## Publicar en GitHub Pages

Estas son instrucciones para publicar desde una rama; no describen una configuración de Pages comprobada para este repositorio.

1. Guarda `index.html` en la raíz de la rama que quieras publicar.
2. En GitHub abre **Settings → Pages**.
3. En **Build and deployment → Source**, selecciona **Deploy from a branch**.
4. Selecciona la rama que contiene el archivo —`main` si corresponde— y la carpeta **/(root)**; guarda.
5. Espera a que termine el despliegue y abre la dirección mostrada por GitHub. Si falla, revisa la ejecución correspondiente en **Actions**.
6. Para actualizar la página, sube los cambios a esa misma rama y espera el nuevo despliegue.

Sin dominio personalizado, la dirección esperada para este repositorio es [https://dpuga0.github.io/happybd/](https://dpuga0.github.io/happybd/); su disponibilidad no se comprobó en esta revisión. Si Pages ya está configurado, revisa su origen antes de cambiarlo.

Referencia: [documentación oficial de GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

## Pruebas manuales recomendadas

**Estado: lista pendiente de ejecución; no representa pruebas aprobadas.** Registra dispositivo, sistema, navegador, fecha y resultado. Repite las pruebas después de cambiar textos extensos, estilos o interacción.

### iPhone · Safari

- [ ] Abrir la URL publicada y comprobar acentos, emojis, título y textos personalizados.
- [ ] Revisar orientación vertical y horizontal: sin texto cortado ni desplazamiento horizontal; controles accesibles cerca del notch y del indicador de inicio.
- [ ] Probar anchos a ambos lados de 390 px, con dispositivos o emulación, y comprobar el cambio de distribución de los recordatorios.
- [ ] Tocar **Abrir carta**, recorrer todo el mensaje y alcanzar la despedida y el cierre. Comprobar también el modal con la barra de Safari expandida y contraída.
- [ ] Cerrar con **×** y tocando fuera; tocar dentro no debe cerrar. Abrir y cerrar varias veces.
- [ ] Comprobar que el fondo no se desplaza mientras el modal está abierto y vuelve a desplazarse al cerrarlo.
- [ ] Activar **Reducir movimiento** y verificar que desaparecen animaciones y transiciones.
- [ ] Probar zoom y VoiceOver: lectura comprensible, nombre del diálogo y acceso al botón de cierre.

### Escritorio · navegadores disponibles

- [ ] Probar Chrome, Firefox, Edge o Safari, registrando cuáles se utilizaron.
- [ ] Revisar la composición centrada en una ventana amplia y al reducir su ancho.
- [ ] Abrir y cerrar con ratón; comprobar que solo el fondo exterior cierra la carta.
- [ ] Navegar con **Tab**, activar botones con **Enter/Espacio** y cerrar con **Escape**. Revisar la visibilidad del foco.
- [ ] Leer toda la carta con zoom al 200 %, sin perder contenido ni controles.
- [ ] Revisar la consola: sin errores de JavaScript al cargar, abrir o cerrar.
- [ ] Recargar la versión publicada y verificar que muestra el último contenido.

### Limitaciones conocidas de accesibilidad

El modal declara `role="dialog"`, `aria-modal="true"` y un título asociado; al abrirlo, el código enfoca el cierre. Sin embargo, no implementa un ciclo de foco dentro del diálogo, no vuelve inerte el contenido de fondo y no devuelve explícitamente el foco a **Abrir carta** al cerrar. Estas limitaciones se observan en el código y deben tenerse en cuenta durante las pruebas de teclado y VoiceOver.

Los márgenes de zona segura se aplican a `.page`; el modal usa su propio padding y una altura basada en `100vh`. Su comportamiento en Safari móvil requiere comprobación real.
