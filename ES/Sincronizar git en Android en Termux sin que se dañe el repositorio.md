Estaba usando **Obsidian en Android 16** el cual tiene mi celular Samsung Galaxy A15 y lo sincronicé (git fetch git add . git etc, etc) con **GitHub usando Termux** (en un repositorio que había creado), y funcionaba, pero después de algunas semanas me pasó un error al hacer la sincronización en Termux con `git push` y me dió un error:

```
object file .git/objects/56/9591fee9c008c9753c01892d86d33a019a98b6 is empty  
fatal: unable to read object  
remote end hung up
```

Esto no es culpa de Git ni de GitHub. Es culpa de **Android**.

En este artículo lograremos entender:

- Por qué Android rompe Git con frecuencia usando Obsidian?
- Cómo evitarlo?
- Y cómo sincronizar tu vault de Obsidian entre Android y Linux de forma profesional

---

## El problema real: Android no es Linux

Android guarda archivos en:

```
/sdcard
```

Pero ese sistema de archivos **no es Linux real**.  
Es un sistema emulado que no soporta bien archivos pequeños ni permisos POSIX, esto es clave para entender por qué todo este problema existe entre Android y Git

# ¿Qué son los **permisos POSIX**?

**POSIX** es un estándar de **cómo funcionan los sistemas tipo Unix/Linux** con archivos y carpetas.

Los **permisos POSIX** son las reglas que dicen:

> **Quién puede leer, escribir o ejecutar cada archivo o carpeta en Linux.**

Se representan así:

```
-rwxr-xr--
```

Cada archivo tiene **tres tipos de permiso**:

| Letra | Significado        | Ejemplo              |
| ----- | ------------------ | -------------------- |
| **r** | read (leer)        | ver el archivo       |
| **w** | write (escribir)   | modificar el archivo |
| **x** | execute (ejecutar) | correr un programa   |

Y se aplican a **tres tipos de usuarios**:

|Posición|Quién es|
|---|---|
|Primer grupo|**dueño** del archivo|
|Segundo grupo|**grupo** del dueño|
|Tercer grupo|**otros usuarios**|

Ejemplo típico:

```
-rwxr-xr--
```


# ¿Qué tiene que ver esto?

Git necesita **permisos POSIX reales** para funcionar bien, por ejemplo:

- Crear miles de archivos pequeños en `.git/objects`
- Cambiar permisos de archivos (`chmod`)
- Mantener consistencia interna

---

# ❌ Por qué `/sdcard` rompe Git en algún momento?

El almacenamiento de Android (`/sdcard`) **NO respeta permisos POSIX**.

Allí:

- Todo es “público”
- No hay dueño real
- No hay permisos finos

Si se clona un repositorio Git, por dentro, guarda miles de archivos pequeños en:

```
.git/objects/
```

Cuando ese `.git` está dentro de `/sdcard`, Android, en algún momento los puede:

- Truncar
- Volver archivos incompletos de 0 bytes
- Corromper

Cuando Android:

- entra en modo ahorro
- la app se suspende
- el sistema sincroniza
- o el usuario cambia de app

**Si se daña un repositorio por tenerlo en /sdcard NO intentes repararlo**
Git NO puede reconstruir objetos vacíos. Un repositorio asi **no es reparable**. Pero los archivos que tengas en el (lo que está dentro de la carpeta .git de dañaría, lo que está al lado no) sí están bien, saquelos manualmente y pongalos en un lugar seguro

---

# Dentro de Termux sí funciona

Cuando se instala Termux, se crea un sistema especial en:

```
/data/data/com.termux/files/home
```

con un **sistema de archivos Linux real (EXT4)** con permisos POSIX completos. Entonces si clonamos un repositorio Git allí dentro funciona perfecto porque dentro de él estará la carpeta .git que contendrá todos sus archivos.

---

## La solución: separar Git de los archivos

La solución profesional es usar una función de Git llamada:

> **git worktree**

Eso permite tener:

- La base de datos Git en Linux real (Termux)
- Los archivos del vault en Android (`/sdcard`)

Así, ejemplo para un repositorio llamado "Obsidian-Android" :

```
/data/data/.../git/Obsidian-Android/.git   ← Carpeta Git real (seguro)
/sdcard/Obsidian-Android                  ← Vault (carpeta) visible para Obsidian (dentro tus archivos, además un archivo .git que explica a Git que sus archivos no están allí sino en el directorio anterior mencionado)
```

Android ve solo archivos  Documentos .docx, Markdown, PDFs, audios, etc, etc.  
Git vive protegido en Linux dentro de Termux 

---

## 🧰 Paso 1 — Clonar el repositorio en Termux
Para ser ordenadores vamos a crear en `/data/data/com.termux/files/home` una carpeta llamada `git` para allí dentro clonar el repositorio u otros repositorios, ejemplo, así:

```bash
cd ~
mkdir git
cd git
git clone https://github.com/wachin/Obsidian-Android.git
```

Eso crea:

```
~/git/Obsidian-Android/.git
```

Ahí vivirá git

---

## 🧰 Paso 2 — Crear el vault visible

```bash
mkdir /sdcard/Obsidian-Android
```

Nota: Le he puesto el mismo nombre del repositorio

---

## 🧰 Paso 3 — Crear una rama especial para Android

```bash
cd ~/git/Obsidian-Android
git branch android
```

---

## 🧰 Paso 4 — Conectar esa rama al vault de Android

```bash
git worktree add /sdcard/Obsidian-Android android
```

Ahora tienes dos espacios de trabajo:

|Carpeta|Rama|
|---|---|
|`~/git/Obsidian-Android`|`main`|
|`/sdcard/Obsidian-Android`|`android`|

---

## 📱 Paso 5 — Abrir Obsidian

En Obsidian en Vault buscar la carpeta "Obsidian-Android" (o el repositorio que usted haya clonado)

---

## 🔄 Cómo sincronizar desde Android

Cuando escribes en el teléfono:

```bash
cd /sdcard/Obsidian-Android
git add .
git commit -m "Update notes from Android"
git push origin android
```

Nunca tocas `main` desde Android, solo la rama del repositorio android

---

## 💻 Cómo sincronizar desde Linux (laptop)

En tu ordenador sigues trabajando igual:

```bash
git pull
git add .
git commit -m "Algo"
git push
```

Eso trabaja en `main`.

---

## 🔀 Cómo unir la rama en Android a la rama en el ordenador

En Termux:

```bash
cd ~/git/Obsidian-Android
git checkout main
git pull
git merge android
git push
```

Git casi siempre hará un **fast-forward**.  
No aparece nano, no hay caos.

---

## 🧨 ¿Y si edito el mismo archivo en ambos?

Entonces Git te dirá:

```
CONFLICT (content)
```

Abres el archivo:

```bash
nano Andro/Biblioteca/Kéfir/Wachin.md
```

Verás algo así:

```text
<<<<<<< HEAD
Texto de la laptop
=======
Texto del teléfono
>>>>>>> android
```

Tú decides qué queda.  
Borras las marcas, guardas:

```
Ctrl + O
Enter
Ctrl + X
```

Y finalizas:

```bash
git add Andro/Biblioteca/Kéfir/Wachin.md
git commit -m "Resolve conflict"
git push
```
o para no escribir tanto, el siguiente añade todos los archivos nuevos: 

```bash
git add .
git commit -m "Resolve conflict"
git push
```

---

## ¿Por qué esto es tan seguro?

Dentro de `/sdcard/Obsidian-Android` existe un archivo llamado `.git`

Pero no es una carpeta.

Es solo un texto que dice algo como:

```
gitdir: /data/data/com.termux/files/home/git/Obsidian-Android/.git/worktrees/android
```

Android no puede ver la base Git.  
No puede corromperla.

---

## Resultado final

| Descripción | Dónde está     |
| ----------- | -------------- |
| Git real    | Linux (Termux) |
| Notas       | Android        |
| Obsidian    | Android        |
Entonces, git sin errores, corrupción imposible

---

## Conclusión

Este método es el mismo que usan desarrolladores móviles profesionales para trabajar con Git en Android.

Ahora puedes usar:

- Obsidian
- Git
- GitHub

en tu teléfono **sin miedo a perder nada**.

Tu conocimiento ahora está protegido por Linux y por Git.

---

# Preguntas y respuestas

## Con que comando se en que rama estoy?

Muy simple. Desde cualquier carpeta que sea un repositorio o worktree:

```bash
git branch
```

Verás algo así:

```
* android
  main
```

El asterisco `*` indica la rama activa.

---

También puedes usar:

```bash
git status
```

Arriba verás algo como:

```
On branch android
(mas mensaje de estado de git)
```

---

Recuerda tu caso:

|Carpeta|Rama|
|---|---|
|`/sdcard/Obsidian-Android`|`android`|
|`~/git/Obsidian-Android`|`main`|

Si estás en duda, haz:

```bash
pwd
git status
```

y lo sabes al instante. 

---

## Como cambio de rama? 

Hay un detalle **importante en el caso con worktrees**

---

### Forma general de cambiar de rama (Git normal)

En un repositorio común se hace así:

```bash
git checkout nombre-de-la-rama
```

o (forma moderna):

```bash
git switch nombre-de-la-rama
```

Ejemplos:

```bash
git checkout main
git checkout android
```

---

### PERO… en la configuración (con `git worktree`) esto cambia

Tú **ya tienes dos espacios de trabajo separados**, y **cada uno pertenece a una rama fija**:

|Carpeta|Rama|
|---|---|
|`/sdcard/Obsidian-Android`|**android**|
|`~/git/Obsidian-Android`|**main**|

👉 **Regla clave:**

> ❌ NO cambias de rama dentro de `/sdcard/Obsidian-Android`  
> ✅ Cambias de carpeta.

Es decir:

### Para trabajar en **android**

Vas aquí:

```bash
cd /sdcard/Obsidian-Android
```

Y automáticamente estás en:

```text
On branch android
```

(No necesitas `git checkout android` ahí).

---

### Para trabajar en **main**

Vas aquí:

```bash
cd ~/git/Obsidian-Android
```

Y estarás en:

```text
On branch main
```

---

### Si quieres comprobarlo

En cualquiera de las dos carpetas ejecuta:

```bash
pwd
git status
```

Ejemplo típico:

```bash
~/git/Obsidian-Android $ git status
On branch main
```

o

```bash
/sdcard/Obsidian-Android $ git status
On branch android
```

---

### Por qué es así

Con `git worktree`:

- **Cada carpeta = una rama fija**
- No “saltas” de rama dentro de la misma carpeta.
- Saltas **entre carpetas**.

Esto es precisamente lo que evita que Android toque tu Git.

---

#  Resumen rápido

|Quieres usar|Haces|
|---|---|
|Rama android|`cd /sdcard/Obsidian-Android`|
|Rama main|`cd ~/git/Obsidian-Android`|
|Ver en qué rama estás|`git status`|

---

# ¿Y qué hago si reinstalo Termux?

Si usas **Obsidian + Git + Termux** con el método de `git worktree` para que Android no dañe tu repositorio, reinstalar Termux puede asustar… pero **tus notas no se pierden**.

Lo que se pierde es **la parte Linux interna de Git**, no tu vault.

Este tutorial explica cómo **reconectar todo** después de reinstalar Termux.

---

## 🧠 ¿Qué pasó realmente al desinstalar Termux?

Android borra completamente esta ruta:

```
/data/data/com.termux/files/home
```

Ahí vivía:

```
~/git/Obsidian-Android/.git
```

Pero tu vault de Obsidian está en:

```
/sdcard/Obsidian-Android
```

Eso **no se borra**.

El problema es que dentro de `/sdcard/Obsidian-Android` hay un archivo `.git` que apuntaba al Git real… que ya no existe.

Por eso, si lo reinstalas a Termux y entras a tu carpeta, si haces ejemplo `git status` aparecerá:

```
fatal: not a git repository
```

---

## ✅ Paso 1 — Borra el puntero Git roto

Tus notas están bien. Solo elimina el `.git` que quedó apuntando a nada:

```bash
rm -f /sdcard/Obsidian-Android/.git
```

---

## ✅ Paso 2 — Reinstala Git y clona el repositorio base

En Termux:

```bash
pkg install git
cd ~
mkdir -p git
cd git
git clone https://github.com/wachin/Obsidian-Android.git
```

Ahora Git vuelve a existir aquí:

```
~/git/Obsidian-Android/.git
```

---

## ✅ Paso 3 — Limpia posibles registros viejos de worktree

```bash
cd ~/git/Obsidian-Android
git worktree prune
```

---

## ✅ Paso 4 — Renombra tu vault actual (temporalmente)

Esto es para que Git pueda crear su estructura:

```bash
mv /sdcard/Obsidian-Android /sdcard/Obsidian-Android.backup
```

---

## ✅ Paso 5 — Vuelve a crear el worktree Android

```bash
git worktree add /sdcard/Obsidian-Android android
```

---

## ✅ Paso 6 — Copia tus notas encima

```bash
cp -r /sdcard/Obsidian-Android.backup/* /sdcard/Obsidian-Android/
```

---

## ⚠️ Si sale “detected dubious ownership”

Eso es normal en `/sdcard`. Haz:

```bash
git config --global --add safe.directory /storage/emulated/0/Obsidian-Android
```

---

## Paso 7 — Sube tus cambios recuperados

```bash
cd /sdcard/Obsidian-Android
git add .
git commit -m "Recover vault after Termux reinstall"
git push origin android
```

Si te dice que la rama está atrás:

```bash
git branch --set-upstream-to=origin/android android
git pull --no-rebase
git push origin android
```

---

## 🔀 Paso 8 — Actualiza la rama principal

```bash
cd ~/git/Obsidian-Android
git checkout main
git pull origin main
git merge android
git push origin main
```

---

## Resultado

Después de esto:

|Cosa|Estado|
|---|---|
|Notas|Recuperadas|
|Git|Reconectado|
|Obsidian|Funciona|
|GitHub|Sincronizado|
|Corrupción|Evitada|

---

## Lección importante

Cuando reinstalas Termux:

|Se pierde|No se pierde|
|---|---|
|Linux interno (`/data/data/...`)|Tus notas en `/sdcard`|
|La base Git|Tu vault|
|Configuración|Archivos de Obsidian|

Por eso solo hay que **recrear la base Git y reconectar el worktree**.

---
