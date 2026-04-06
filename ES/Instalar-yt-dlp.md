
## 📱 ¿Qué es Termux?

**Termux** es un entorno de terminal 🖥️ (línea de comandos ≡ CLI) que simula un sistema Linux dentro de Android 🤖.

Gracias a Termux podemos instalar herramientas poderosas como:

* 🧲 `yt-dlp` → Descargar videos y audios
* 🎞️ `ffmpeg` → Convertir y fusionar formatos
* 🐍 `python` → Ejecutar scripts

---

## 🎯 ¿Qué es yt-dlp?

`yt-dlp` es una **bifurcación (fork)** de `youtube-dl`.

📌 Es decir:

> Es una versión mejorada ➕ optimizada ➕ mantenida activamente.

### 🔎 ¿Qué mejora yt-dlp?

✔️ Soporte para más sitios web
✔️ Mejor extracción de video/audio
✔️ Más opciones avanzadas ⚙️
✔️ Mejor mantenimiento

Es una herramienta potente 💪 para descargar y gestionar contenido multimedia de forma eficiente y flexible.

---

## 📚 Antes de continuar

Te recomiendo ver mi tutorial previo:

🔗 **Tutorial: Uso de Git en Termux para Android**
[https://github.com/wachin/Instalar-git-en-Android-con-Termux](https://github.com/wachin/Instalar-git-en-Android-con-Termux)

Una vez instalado `git`, puedes continuar con `yt-dlp`. (git no es un requisito, pero una vez que lo tengas instalado ya podrás instalar el resto)

---

# 🔄 Actualizar repositorios en Termux

Primero actualizamos el sistema:

```bash
pkg update
```

Luego:

```bash
pkg upgrade
```

**Nota:** En algunas instalaciones de Termux, ejemplo en los celulares modernos Xiaomi puede venir una versión híbrida en la que el comando que se usa para actualizar los repositorios, éste al mismo tiempo aplica los cambios, en tal caso ya no es necesario usar`pkg upgrade` (además de que es mejor no hacerlo para que no se cambien los repositorios)


⚠️ Te hará varias preguntas.
Responde con:

```
y
```

varias veces hasta que termine ✔️

---

# 🛠️ Instalar dependencias necesarias

```bash
pkg install python ffmpeg -y
```

Luego instalar yt-dlp:

```bash
python -m pip install yt-dlp mutagen
```

### 📌 ¿Para qué sirve cada cosa?

* 🐍 `python` → Ejecuta `yt-dlp`
* 🎞️ `ffmpeg` → Fusiona audio + video
* 🎵 `mutagen` → Gestiona metadatos

---

# 🔄 Actualizar yt-dlp

```bash
python3 -m pip install -U "yt-dlp[default]"
```

---

# 🔎 Ver versión instalada

```bash
yt-dlp --version
```

---

# 🔎 Revisar repositorio activo en Termux

Se recomienda usar **un solo repositorio** (según el manual anterior).

---

# 🔍 Zoom en Termux

Si la letra es pequeña:

🤏 Usa dos dedos y haz zoom hacia dentro o hacia afuera.

---

# 💾 Acceder al almacenamiento interno

Primero:

```bash
termux-setup-storage
```

Aceptar permisos ✔️

Luego:

```bash
cd storage
ls
cd shared
```

---

## 🚀 Método abreviado

```bash
cd /sdcard
```

Ambos métodos llevan al almacenamiento compartido.

---

# 📍 Saber en qué ruta estás

```bash
pwd
```

### 📌 Ruta inicial si es la primera vez:

```
/data/data/com.termux/files/home
```

### 📌 Si estás en memoria interna:

```
/sdcard $
```

---

# 📂 Crear carpeta para descargas (opcional)

Solo si lo desean pueden crear una carpeta especial para entrar allí y guardar las descargas:

```bash
mkdir descargas-yt
cd descargas-yt
```

Sino nomás guarden en sdcard (el Almacenamiento Interno).

---

# 🎬 Descargar videos con yt-dlp

## 1️⃣ Descargar video + audio en MP4

```bash
yt-dlp -f "bv*+ba" -S ext:mp4 --merge-output-format mp4 <URL_DEL_VIDEO>
```

### 🧠 Explicación del comando:

* `-f "bv*+ba"` → Mejor video ➕ mejor audio
* `-S ext:mp4` → Prioriza formato MP4
* `--merge-output-format mp4` → Fuerza salida en MP4
* `<URL_DEL_VIDEO>` → Reemplazar por la URL

---

## 2️⃣ Ejemplo práctico

```bash
yt-dlp -f "bv*+ba" -S ext:mp4 --merge-output-format mp4 https://youtu.be/CITtmHVmNIg
```

---

## 🎥 Descargar de Odysee

```bash
yt-dlp https://odysee.com/@FernandoJV:6/20200919-Rancho-Bariloche-Comusav:6
```

---

## 📂 Verificar descarga

```bash
ls
```

También puedes usar el administrador de archivos 📁.

---

# 🎵 Descargar MP3 con carátula

```bash
yt-dlp -x --audio-format mp3 --embed-thumbnail --add-metadata URL
```

✔️ Extrae solo audio
✔️ Inserta miniatura 🖼️
✔️ Añade metadatos

---

# 🎼 Descargar M4A con carátula

```bash
yt-dlp -x --audio-format m4a --embed-thumbnail --add-metadata URL
```

Otros formatos disponibles:

aac • alac • flac • opus • vorbis • wav

---

# 📘 Descargar MP4 de Facebook

```bash
yt-dlp -v -f "bv*+ba" -S ext:mp4 --merge-output-format mp4 URL
```

---

# 🌐 Descargar de otros sitios web

```bash
yt-dlp -o "%(title)s.%(ext)s" "https://www.example.com/video"
```

---

# 📝 Descargar subtítulos

## 📋 Ver subtítulos disponibles

```bash
yt-dlp --list-subs URL
```

---

# ℹ️ Más información

```bash
yt-dlp --help
```

---

# 📚 Consultas y referencias

🔗 Termux Setup Storage
[https://wiki.termux.com/wiki/Termux-setup-storage](https://wiki.termux.com/wiki/Termux-setup-storage)

🔗 yt-dlp en Termux (Reddit)
[https://www.reddit.com/r/youtubedl/comments/pr7ruk/ytdlp_on_termux/](https://www.reddit.com/r/youtubedl/comments/pr7ruk/ytdlp_on_termux/)

---

# Resumen listo para usar

El siguiente es el resumen de lo que más yo uso. Este resumen lo tengo en el App Google Keep, pues allí solo cogo y reemplazo:

✔️ PARA ACTUALIZAR YT-DLP

python3 -m pip install -U "yt-dlp[default]"

✔️ DESCARGAR MP3 de YouTube
Para esto hay k user opciones especificas:

yt-dlp -x --audio-format mp3 --embed-thumbnail --add-metadata https://youtu.be/cdhrdKNuYLU?si=-1Fp9bj1YeFybjMS

✔️ DESCARGAR MP4 de Facebook

yt-dlp -v -f "bv*+ba" -S ext:mp4 https://www.facebook.com/share/r/16z82WRt4e/

✔️ DESCARGAR MP4 DE YOUTUBE

yt-dlp -f "bv*+ba" -S ext:mp4 --merge-output-format mp4 https://youtu.be/T-_HZQydPL4?si=09-n7Uc6kZIiUP-s
