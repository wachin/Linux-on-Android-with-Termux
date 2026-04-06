# Termux en Android para instalar programas de terminal de Linux como: git, yt-dlp, nnn, tree, y otros

**Actualizado: 2026**

Termux es un emulador de terminal y entorno Linux para Android que permite instalar y usar git como lo haríamos desde una terminal de Linux. También se pueden instalar otros programas como yt-dlp (para descargar videos de YouTube), nnn (Administrador de Archivos), tree, y otros que se puedan usar desde la terminal.

Antes de seguir, si ustedes no van a usar git, no lean las partes de este tutorial en las que se explican uso, y configuraciones de git, pero si lo piden instalar aunque no lo vayan a usar, lo que pasa es que para mí es una manera de verificar que puedan instalar otros programas de terminal en Termux.

## Instalar yt-dlp
Después de instalar Termux y git podrán instalar yt-dlp, dejo aparte la instalación:

- [yt-dlp](/ES/Instalar-yt-dlp.md)



## El porqué de este tutorial

En Linux (MX Linux 21) estoy usando git como un tipo de almacenamiento en la nube, similar a:

- Dropbox
- MEGA
- Google Drive

Esto mismo se puede hacer con git desde un celular Android usando Termux para tener archivos offline.

**Ejemplo:** He creado un cancionero con acordes de guitarra para usarlo desde el celular con Android y desde el ordenador con Linux:

[https://github.com/wachin/Cancionero](https://github.com/wachin/Cancionero)

> Nota: Con la app de GitHub de Microsoft en la Play Store no se puede hacer todo lo que se puede hacer con git desde la terminal de Termux.
>

### Pros
- Archivos offline en el celular

### Contras
- Sincronización manual
- Un repo de git contiene una copia de sus archivos en la carpeta oculta .git, por lo cual ocupará el doble de espacio o más
- Para usuarios avanzados que sepan de control de versiones con git
- Usar la terminal
- Si no tiene cuidado si editar un archivo el repositorio se puede dañar.

#### Como evitar que mi repositorio se dañe al editar un archivo

Cuando edites un archivo de un repositorio que haya si clonado en el Almacenamiento Interno:

- El teléfono no debe estar en modo ahorro
- Después de editar el archivo hay que cerrar el App antes de enviar los cambios al repositorio
- Si usas mucho un repositorio para editar los mismos archivos en el celular y en el ordenador, mejor usa **git worktree**, como se explica más abajo para usar Obsidian en Android en Termux así nunca se corromperá un repositorio.

### Requerimientos
- Teléfono con Android
- Repositorio en github.com o gitlab.com

### Archivos usables
Se pueden usar archivos para control de versiones como: .txt, .md, u otros.

En los archivos compatibles con control de versiones solo se aumentará el tamaño del archivo donde se edite y agregue información.

Como dato importante LibreOffice tiene un archivo para control de versiones: .fodt
[FODT en LibreOffice](https://facilitarelsoftwarelibre.blogspot.com/2020/06/que-es-un-archivo-fodt-fodt-flat-open.html)
pero para este no hay un editor en la Play Store.

## Qué más se puede hacer con git, instalar Obsidian para tener tus notas y conocimientos en el celular
- Se puede usar Obsidian para editar un repositorio de github que también se pueda usar en Linux, solo que el App Obsidian con Mucha frecuencia daña el repositorio, pero la solución aquí está:
[Sincronizar git en Android en Termux sin que se dañe el repositorio](/ES/Sincronizar-git-en-desde-Android-en-Termux.md)
Pero para que no se corrompa el repositorio hay que usar **git worktree**, allí en este tutorial está todo explicado:

- Se puede hacer push, fetch, merge y todos los demás comandos para mantener sincronizado el repo
- Se puede trabajar con los archivos desde:
  - Android a Linux y viceversa
  - Android a Windows y viceversa
  - Android a MAC y viceversa

> Nota: Los 2 últimos no los he probado, pero sé que existen.

## Compatibilidad entre Android y Linux

En el video "Aprende GIT Ahora! Curso completo gratis desde cero" ([https://youtu.be/VdGzPZ31ts8](https://youtu.be/VdGzPZ31ts8)), Nicolás Schurmann explica que si sincronizan un repositorio desde Windows a "Linux o MAC" deben configurar el fin de línea para enviar ediciones en código de texto. Sin embargo, en este tutorial no es necesario hacerlo ya que usar git desde Termux es como usarlo en Linux.

Este tutorial no pretende enseñar a usar git. Si no sabe usarlo, puede buscar en Google las palabras "aprende git cursos" y encontrará recursos en Udemy, Platzi, devcode, ed.team, Coursera, o [https://github.com/JJ/aprende-git](https://github.com/JJ/aprende-git), Youtube, etc.

# Instalando Termux en Android

A continuación elija la opción que necesite:
## Instalando Termux y git en Android 7, 8, 9, 10, 11, 12, 13, 14+

Le dejo opciones, como se me perdió mi Xiaomi y me compré un SAMSUNG GALAXY A15 ahora uso la 3er opción:

### 1ra Opción: Instalación con Google Play Store

En la Play Store hay una versión de Termux actualizada que dice allí en la información del App en la misma Google Play a la fecha 2024 en la que se puede instalar Termux y allí git, la cuál la probé pero no se puede instalar yt-dlp pues no existe ese paquete, y puede que no se puedan instalar más cosas, pero si solo van a instalar git bien lo pueden usar, también si no desean instalar Apps de otros sitios estará bien para ustedes (a mi me parece que es una versión con paquetes limitados de Termux).

También lea:

[https://github.com/termux/termux-app](https://github.com/termux/termux-app)

### 2da Opción: Instalación con Xiaomi

Si Usted tiene un celular Xiaomi, busque en la tienda de aplicaciones:

- Mi Picks
- o GetApps

Busque "Termux", instálelo. Ellos tienen a la fecha que se me perdió mi Xiaomi 2024 la versión Termux 0.119, instalelo y ábralo.

**Actualizar y automáticamente buscar un repositorio y actualizar**

Si solo va a usar git en Termux, se le facilita todo. Solo ponga:

```
pkg update
```

>Nota: En la versión 0.119 de ellos no es necesario usar `pkg ugrade` porque `pkg update` es una especie de híbrido que hace las dos cosas

Aparecerá un mensaje que dice: "Testing the available mirrors:"

También aparecerá un mensaje:

```
Calculating upgrade... Done
The following NEW packages will be installed:
```

Le preguntará:

```
Do you want to continue? [Y/n]
```

Responda:

```
y
```

y presione ENTER. Esté atento porque luego le volverá a preguntar, hay que poner como 5 veces: y

Ahora instale git con:

```
pkg install git
```

Además les

Para que Termux tenga acceso a su almacenamiento interno, escriba:

```
termux-setup-storage
```

y presione Enter y acepte. Así lo he usado en un Redmi Xiaomi Note 11 que trae Termux 0.119 (versión que solo ellos tienen a esta hecha que hago el tutorial 2024). 

Aparte, si Ud quisiera elegir un repositorio de los disponibles, más abajo indico cómo.

### 3ra Opción: F-Droid

Entre en:

[https://f-droid.org/](https://f-droid.org/).

F-Droid es un repositorio de aplicaciones de software libre para dispositivos Android. Funciona como una alternativa a Google Play Store, proporcionando aplicaciones que son de código abierto y, en muchos casos, centradas en la privacidad.

Descargue e instale F-Droid

Y para que ustedes tengan tranquilidad, carguen el Apk descargada a:

virustotal.com

está limpia, instalar 

luego abra F-Droid y en la lupa verde que está abajo a la izquierda busque: "Termux Emulador de terminal con paquetes" e instálelo.

En esta versión si he usado `pkg update` y `pkg upgrade` porque no es un híbrido.

### 4ta Opción: Paquete apk desde F-Droid

Puede descargar si deseas sólo el APK de Termux desde:

[https://f-droid.org/en/packages/com.termux/](https://f-droid.org/en/packages/com.termux/)


Y para que ustedes tengan tranquilidad, carguen el Apk descargada a:

virustotal.com

está limpia

e instalarla

## Zoom en Termux

Si la letra de Termux es muy pequeña, hágalo más grande usando los dos dedos haciendo zoom hacia afuera, y luego corrige había dentro.

## Para instalar Termux en Android 5, 6

Vea las instrucciones en el siguiente enlace:
[https://youtu.be/eKhjvaLIPnI](https://youtu.be/eKhjvaLIPnI)

Aunque podría ya no servir para nadie, pero lo dejo como consulta.

## Desactivar el proceso fantasma en Android para que funcione correctamente Termux  
Si algun celular con Android tiene habilitado el proceso fantastama, cerrará algún proceso que se esté ejecutando de fondo, esto puede ser negativo si el usuario a instalado algún Linux en Termux, o alguna aplicación que necesite estar funcionando de fondo; para desabilitar eso primero hay que habilitar las opciones para desarrollador:

**Cómo habilitar las Opciones para desarrolladores**  
[https://developer.android.com/studio/debug/dev-options?hl=es-419](https://developer.android.com/studio/debug/dev-options?hl=es-419)

y dejo un video pero está en inglés sobre cómo desabilitar el proceso fantasma:

**Fix Termux Error [Process completed (signal 9) - Disable Phantom Process Killer In Android 12 & 13**  
[https://youtu.be/w10I_3-Qaqw?si=VxFhe7d68SVst3QB](https://youtu.be/w10I_3-Qaqw?si=VxFhe7d68SVst3QB)

Y las siguientes son consultas en español:

**Android 13 quiere que exprimas al máximo la potencia de tu teléfono. ¿Cómo lo hará?**  
[https://cincodias.elpais.com/smartlife/2021/12/14/lifestyle/1639489577_351730.html](https://cincodias.elpais.com/smartlife/2021/12/14/lifestyle/1639489577_351730.html)

**Android 13 permitirá deshabilitar la estricta gestión de procesos fantasmas de Android 12**  
[https://www.xatakandroid.com/sistema-operativo/android-13-permitira-deshabilitar-estricta-gestion-procesos-fantasmas-android-12](https://www.xatakandroid.com/sistema-operativo/android-13-permitira-deshabilitar-estricta-gestion-procesos-fantasmas-android-12)

según eso la monitorización de los procesos fantasma puede ser desactivada desde las opciones de Configuración > Opciones de desarrollador > Banderas de características.

## Eligiendo un repositorio

Cuando he instalado Termux desde F-Droid lo siguiente es lo que hago porque quiero que los paquetes que se descarguen siempre sean exactamente los mismos y que no estén unos más actualizados o contengan pequeñas diferencias que otros paquetes, para evitar algún mal funcionamiento, ejemplo, cuando son muchas las dependencias a usar como en programas escritos en python que son bastantes delicados con sus bibliotecas y a veces por un cambio en versiones ya no funcionan. Esto es, personalmente, lo que yo pienso: Usar si está disponible siempre un repositorio, o si se llegara a caer, usar algún otro, pero siempre sabiendo cuál es y que sea de los que nunca o de los que menos se caen.

**Tutorial probado en:**  

- **Termux 0.119.0 en Xiaomi Redmi Note 11**
- **Termux 0.119.0 desde [https://f-droid.org/en/packages/com.termux/](https://f-droid.org/en/packages/com.termux/) en SAMSUNG GALAXY A15, pero se descarga como com.termux_1022.apk**

**Nota:** Este tutorial lo reviso en 2026 enero

### termux-change-repo

Para elegir un repositorio, poner:

```bash
termux-change-repo
```

Las siguientes indicaciones las he visto así a la hecha 2024, pero con nuevas versiones que salgan en el futuro puede que varíen, pero el principio es el mismo, siempre lean (está en inglés) las instrucciones con atención, y son dos, la una es que el programa elija entre todos los repositorios uno disponible, y la otra es que ustedes elijan uno (que es lo que yo hago).

Cuando es la primera vez que uno usa este comando en Termux 0.119, aparece así:

```
Which repositories do you want to edit? Select with space.
[*] Main repository termux-packages
│  <  OK  >    <Cancel> │
```

**Nota:** Puede seleccionar con las flechas más barra espaciadora

O con clic y darle Ok

Pero si te sale así:

```
┌────────────────termux-change-repo──────────────────┐
│ Do you want to choose a mirror group or a single   │
│ mirror? Select with space.                         │
│ ┌────────────────────────────────────────────────┐ │
│ │(*) Mirror groupRotate between several mirrors (│ │
│ │( ) Single mirroChoose a single mirror to use   │ │
│ │                                                │ │
│ │                                                │ │
│ │                                                │ │
│ └────────────────────────────────────────────────┘ │
├────────────────────────────────────────────────────┤  │             <  OK  >       <Cancel>
```

Elije en de abajo: 

```
(* ) Single mirroChoose a single mirror
```

Y cuando te salsa así: 

```
┌──────────termux-change-repo────────────┐
│ Which group of mirrors do you want to  │  │ use? Select with space.                │
│ ┌────────────────────────────────────┐ │
│ │(*) All mirrors All in the entire world│ │
│ │( ) Mirrors in AAll in Asia (excl. C│ │
│ │( ) Mirrors in CAll in Chinese Mainl│ │
│ │( ) Mirrors in EAll in Europe       │ │
│ │( ) Mirrors in NAll in North America│ │
│ │( ) Mirrors in OAll in Oceania      │ │
│ │( ) Mirrors in RAll in Russia       │ │
│ │                                    │ │
│ │                                    │ │
│ └────────────────────────────────────┘ │
├────────────────────────────────────────┤
│         <  OK  >     <Cancel>
```

Yo aplasté Enter en la primera opción: 

(*) All mirrors All in the entire world

Que significa: 

(*) Todos los espejos Todo en el mundo entero

Pero se podía elegir alguna en especial si uno quiere un mirror de alguna de esas zonas y se ahorraría tiempo en estar buscando

Si es la segunda vez (estas opciones pueden variar de una versión a otra de Termux) que hacen este proceso puede que les aparezca así: 

```
Do you want to choose a mirror group  
│ or a single mirror? Select with space.
│(*) Mirror grRotate between several │
│( ) Single miChoose a single mirror┤
│         <  OK  >     <Cancel>
```

en este caso haga clic en la segunda opción para que esa que marcada (lo mismo que antes descrito): 

(*) Single miChoose a single mirror

cuya traducción es: 

(*) Escoja un solo espejo

y de clic en ok

Aparecerá una lista, para moverse hacia abajo o arriba puedan usar en termux las flechas o Página arriba (PGUP) o Página abajo (PGDN)

## Repositorios Disponibles (no los he visto caídos)

En la versión de Termux k está en el instalador de los celulares Xiaomi "Mi Picks" he visto k se cargan bastante los siguientes repos:

### Grimler
(Henrik Grimler https://github.com/grimler91)
Alojado en Helsinki, Finlandia.
Bifurcado desde el nodo principal
Actualizado cada hora
https://grimler.se/termux-packages-24

### BFSU 
(Beijing Foreign Studies University)(http://www.bfsu.edu.cn/)(China)
https://mirrors.bfsu.edu.cn/termux/apt/termux-main

### Karibu
(karibu@freedif.com)
Alojado en Singapore (Asia) 
Actualizado cada hora
https://mirror.freedif.org/termux/termux-main

### mwt
(Matthew W. Thomas | Economist at FTC | Northwestern University Economics PhD https://github.com/mwt)
Alojado en la costa este/oeste de EE. UU. y Europa (a través de CDN)
Actualizado 4 veces al día
https://mirror.mwt.me/termux/main

### Purde
Grupo de usuarios de Linux de la Universidad de Purdue
Alojado en Indiana, EE. UU.
Actualizado 4 veces al día https://plug-mirror.rcac.purdue.edu/termux/termux-main

### a1batross
(https://github.com/a1batross)
Actualizado 4 veces al día https://termux.mentality.rip/termux-main

### Librehat
(https://github.com/librehat)
Actualizado 4 veces al día https://termux.librehat.com/apt/termux-main

### CloudFlare
CDN endpoint https://packages-cf.termux.org/apt/termux-main


## Repositorios caídos con frecuencia
Y he visto caídos a:

### sahilister
https://termux.sahilister.in/apt/termux-main: bad

### kcubeterm
https://dl.kcubeterm.com/termux-main: bad

### Astra
https://termux.astra.in.ua/apt/termux-main: bad

**CONSEJO**  
Yo uso Grimler, nunca lo he visto caído, tampoco a BFSU (solo es de observar, los que se caen tienen: bad)

La description de los repos las he visto en: 

[Termux Packages Mirrors](https://github.com/termux/termux-packages/wiki/Mirrors)

Para elegir uno, con la flecha hacia abajo diríjase hasta:

```
( ) Mirrors by Grimler . . . 
```

o:

```
( ) Mirrors by BFSU . . . 
```

O también puede elegir otro.

Ejemplo, voy a seleccionar Grimler, asi que con la flecha abajo me pongo allí y doy barra espaciadora en el teclado para marcarlo, k kede así: 

```
( * ) Mirrors by Grimler . . .
```

y Enter

Esperar a que termine, y poner: 

```
pkg update
```

so le have unas preguntas, ponga: 

```
y
```

Además explico que en la versión de Termux 0.118 después de usar pkg update hay que usar: 

```
pkg upgrade
```

(pero como les explicaba más arriba, en la versión 0,119 de Xiaomi no es necesario porque pkg update es una especie de híbrido que hace las dos cosas) 

esté atento y ponga la: "y" varias veces.

## Aparecerán más opciones en termux-change-repo después de actualizar

Si Ud x algún motivo desea usar otra vez el comando: 

```
termux-change-repo
```

Le aparecerán más opciones.

si hacen como yo elijan la opción que es para escoger manualmente uno, y luego:

```
pkg update
```
además, este comando le aconsejo usarlo con alguna frecuencia, puede ser cada mes, es para tener actualizados los parquetes (en Termux 0.119 solo con este basta, y con 0.118 luego hay que usar pkg upgrade)

## Instalando git

```
pkg install git
```

cuando ponga este comando vea allí cuál repo aparece, en caso de que se haya cambiado el repo cancele con "Ctrl + C" y cambielo usando otra vez `termux-change-repo` xq sino empezará a buscar aleatoriamente otro repo


Para ver la versión que tiene instalada de git ponga en Termux:

```
git --version
```

## Acceder al Almacenamiento Interno

Para que Termux tenga acceso a su almacenamiento interno, escriba:

```
termux-setup-storage
```

y presione Enter y acepte.

Para clonar un repositorio en la memoria interna primero hay que llegar allí. En Termux escriba:

```
cd storage
```

Luego escriba:

```
ls
```

para ver los repositorios disponibles.

Luego elija la memoria compartida:

```
cd shared
```

Comando especial: También se pueden abreviar los pasos 1 y 2 solo con:

```bash
cd /sdcard
```

Con cualquiera de los dos métodos llegará a la memoria interna compartida.

Para saber en qué ruta está ubicado, escriba en Termux:

```bash
pwd
```

y presione Enter.

Nota: Si es la primera vez que abre Termux estará en la carpeta de configuraciones de Termux (es una especie de emulación del HOME de Linux para que Termux tenga allí sus archivos como si estuviera en Linux):

```
/data/data/com.termux/files/home
```

y si ya está en la memoria interna y para llegar allí usó cd shared aparece así:

```
~/storage/shared $
```
y si uso: cd /sdcard así:
```
/sdcard $
```

>**Nota**: Siempre es importante saber dónde está ubicado porque puede ser que sin querer clonó un repositorio dentro del espacio de configuraciones de Termux o en storage, y en caso de pasar algún día eso, puede usar el comando mover "mv" para mover la carpeta que haya clonado desde el espacio de las configuraciones de Termux a storage y luego usar otra vez "mv" para mover la carpeta a "shared". Para esto es necesario saber que si estoy en "/data/data/com.termux/files/home" (que es por defecto donde uno está ubicado cuando recién abre Termux) fuera de este está "storage", y si estoy en "storage" fuera de este está "shared", entonces si cloné un repo llamado "mirepo" estando en ".../home" primero debo pasarlo a "storage" poniendo allí: `mv su-repo storage` y luego para pasarlo al Almacenamiento Interno poner: `mv su-repo shared` y listo solucionado; y si solo por error lo clonó en storage solo ponga: `mv su-repo shared`. Por cierto, si usted está en "shared" y desea ir a ".../home" ponga `cd`.



## Crear y usar un token como contraseña en github.com

(Si ya tiene el token omita este paso)

Para poder explicar mejor usaré la siguiente cuenta:
[https://github.com/mamimeli](https://github.com/mamimeli)

Entre en la siguiente dirección:
[https://github.com/settings/](https://github.com/settings/)

Allí haga clic en:

1. Developer Settings
2. Personal Access Token
3. Tokens (classic)
4. Generate New Token (Classic)

O también directamente en la dirección:
[https://github.com/settings/tokens](https://github.com/settings/tokens)

Allí en "**Note**" póngale algún nombre.

En "**Expiration**" seleccione un tiempo de expiración (Github aconseja poner un tiempo de expiración: [https://bit.ly/3BrIvA9](https://bit.ly/3BrIvA9))

En "**Select scopes**" marque "**repo**" (pero si necesita algún otro permiso márquelo) y al final de la página haga clic en "**Generate token**".

Copie inmediatamente el código generado y téngalo en un lugar seguro o en un gestor de contraseñas.


## Clonar un repositorio

Una vez que esté en el Almacenamiento Interno Compartido (llamado shared o /sdcard -si utilizo el segundo método para llegar allí-) clone un Repositorio, por ejemplo:

```bash
git clone https://github.com/mamimeli/Cancion
```

## Evitar problemas con caracteres tipográficos al clonar un repositorio 
Cuando clones un repositorio este no tiene que tener en los nombres de archivos o carpetas los siguientes caracteres no permitidos en Android no Linux pues tienen ciertas restricciones :

1. **Dos puntos `:`**
2. **Asterisco `*`**
3. **Signo de interrogación `?`**
4. **Comillas `"`**
5. **Menor que `<` y mayor que `>`**
6. **Barra vertical `|`**
7. **Barra invertida `\`**
8. **Barra diagonal `/`**

Además, evita nombres que terminen en un espacio o punto, ya que también pueden causar problemas en algunos sistemas de archivos compatibles con Android. Y si alguna vez comentes el error de hacer fetch o pull de un repositorio con esos caracteres, revisa más abajo la sección de resolver conflictos al hacer merge.

### Recomendación
Para evitar estos errores, utiliza caracteres comunes como letras, números, guiones `-`, y guiones bajos `_`, que son compatibles tanto en Android como en otros sistemas de archivos.


## Identificarse en git (y que no pida otra vez el token)

Escriba en Termux (reemplace con sus datos):

```bash
git config --global user.name suusuario
git config --global user.email sucorreo@servicio.com
```

Y el siguiente comando es para que git almacene el Token:

```bash
git config --global credential.helper store
```

Y entre en el repositorio con cd, en mi caso así:

```bash
cd Cancion
```

Ahora haga:

```bash
git status
```

y aparecerá el siguiente mensaje:

```
/sdcard/Cancionero $ git status
fatal: detected dubious ownership in repository at '/storage/emulated/0/Cancion'
To add an exception for this directory, call:
        git config --global --add safe.directory /storage/emulated/0/Cancion
```

Allí dice que ha detectado un dueño dudoso y que añada una excepción a ese directorio para aceptarlo como seguro. En mi caso (usted debe poner lo que le aparezca) lo que tengo que poner es eso que me dice allí mismo:

```bash
git config --global --add safe.directory /storage/emulated/0/Cancion
```

Solucionado (eso deberá hacerlo en cada Repositorio)

## Edite algún archivo o carpeta 

Ahora edite algún archivo o carpeta desde algún Administrador de archivos de Android que permita (Nota: El administrador de Xiaomi y el de Samsung no funcionan para esto) ver no solo las carpetas del sistema sino los repositorios que uno clone, esto, para agregar un cambio en el repositorio, ejemplo con (algunos de los administradores de archivos tienen un editor de texto incorporado): 

- Gestor de archivos | File Manager Plus (gratis)
- Super Explorador de archivos | ESTRONGS LIMITED (gratis con publicidad)
- Solid Explorer File Manager| NetBeans (prueba gratis por algunos días)
- MiXplorer Silver | Hootan Parsa (de pago)
- MiXplorer (gratis)
- Editor de textos QuickEdit (gratis con publicidad)
- CodeFusion: Code Editor (gratis)
- WPS Office (gratis, de pago exporta a PDF)
- Microsoft 365 (Office) + OneDrive (gratis, exporta a PDF con internet)
- Microsoft Word + OneDrive (gratis, exporta a PDF con internet)
- Documentos de Google + Google Drive (gratis, exporta a PDF con internet)
- AndrOpen Office (gratis, de pago exporta a PDF)
- nano o Vim para editar archivos de texto desde la línea de comandos

vea todas las explicaciones de cómo usarlos en este apartado:

[Editar archivos de repositorios git en Android desde editores o administradores de archivos Apps](file:///ES/Editar-desde-editor-o-administrador-de-archivos.md)

ahora agregelo y súba el cambio a GitHub con ejemplo con las siguientes indicaciones:

### Añadiendo el cambio con git add .

Sea como sea que haya hecho el cambio a algún archivo de su repositorio, añada el cambio que ha hecho en git ejemplo con:

```bash
git add .
```

y debemos hacer un commit, ejemplo:

```bash
git commit -m "Nombre del commit"
```

Y luego envíe los cambios al remoto:

```bash
git push
```

y cuando le pregunte por su Usuario póngalo, y cuando le pregunte por el Password ponga su **Token** (si hizo bien siguiendo la secuencia la proxima vez no le pedirá el token).

Se creará el archivo (eso es interno, no lo verá usted):

.git-credentials

se creará dentro del HOME que Termux emula, el archivo que contendrá el Token.

> **Nota:** Si luego desean usar otro usuario de github o gitlab deben ingresarlo y se cambiará, y si desean regresar al anterior deben ingresarlo otra vez, es decir, siempre estará activo el último usuario ingresado.

Y con eso ya podemos hacer:

git status  
push  
fetch  
merge  
pull, etc  

# Usando editores de texto para terminal como Nano o Vim
Usando Termux llegará el momento que tenga que usar algún editor de texto de línea de comandos como "Nano" que me vino instalado en el Termux de "Mi Picks" de Xiaomi, pero si no está instalado, instálelo así:

```bash
pkg install nano
```

o si usa Vim (no confundir con vi que es una versión que puede estar instalada pero es limitada, Vim es la versión completa)

```
pkg install vim
```

Para ver la versión de nano escriba:

```bash
nano --version
```

o para Vim

```
vim --version
```

## Cómo poner por defecto a nano u otro editor de terminal
Si por un caso instalan otro editor de texto de terminal y luego nano u otro que usen ya no es el editor por defecto, vuelvanlo a poner poniendo:

```
update-alternatives --config editor
```

allí aparecerá la lista de los editores instalados para uno poder elegir el que estará por defecto, dependiendo de los que estén instalados, ejem si son tres se mostrará:

0  

1  

2  

y debe escribir el número que corresponda y de Enter.

## Editar texto con Nano

Para editar, por ejemplo, el archivo de configuración de las credenciales de git, escriba:

```bash
nano ~/.git-credentials
```

Para editar texto es muy sencillo, solo tiene que ubicarse en la posición adecuada con las flechas de Termux y comenzar a escribir (o pegar) texto.

Para guardar cambios: Nano abrevia CTRL con ^, así CTRL + O es igual a:

^O

y en nano aparece así:

^O Guardar

Así, para guardar presione:

CTRL + O

y aparecerá un mensaje que dice algo así:

```
Nombre del fichero a escribir: nombre-del-archivo.txt
```

y presione ENTER.

> Nota: Es importante hacer notar que es la letra O, no es cero.

### Cómo salir de Nano: 

Presione CTRL + X para salir, pues Nano abrevia CTRL con ^, así CTRL + X es igual a: ^X que es para Salir.
(Nota: Si usted está escribiendo algo y ha presionado CTRL + O la opción CTRL + X no estará disponible hasta que usted presione ENTER) y saldrá de nano.

Al hacer eso aparecerá en medio de Termux:

```
File Name to Write:<tconfig
```

Esa es la abreviatura del archivo: .gitconfig. Usted no cambie nada y solo presione ENTER (Si usted cambia el nombre y presiona ENTER se creará otro archivo conteniendo lo que haya editado).

Además si desea puede ver un tutorial que hice:

**Cómo usar nano en la terminal de Linux para editar archivos de texto**  
[https://facilitarelsoftwarelibre.blogspot.com/2024/08/como-usar-nano-en-linux.html](https://facilitarelsoftwarelibre.blogspot.com/2024/08/como-usar-nano-en-linux.html)  

## Modificar gitconfig con Vim

Para usar Vim ejemplo para editar el archivo .gitconfig

Para editar el archivo de configuración de git escriba:

```bash
vim ~/.gitconfig
```

Advertencia: Debe tener cuidado de no borrar algo del código pues si lo hace se le dañará git. Si eso llegara a pasar escriba:

```bash
rm ~/.gitconfig
```

y vuelva a identificarse.

Editando: Una vez que aparece el entorno del editor Vim estaremos por defecto en el modo de comando, y si queremos editar presionemos una vez la tecla:

i

al hacerlo se cambiará al modo de edición y edite.
Una vez que ya no quiera seguir editando presione:

ESC

que es para cambiar al modo de comandos.

Para guardar presione:

```
:w
```

> **Nota:** Esa w significa write = escribir

y presione:

ENTER

Para dejar de escribir o salir de Vim, use el comando:

```
:q
```

y presione ENTER.

Para guardar un archivo y salir de Vim simultáneamente, use el comando:

```
:wq
```

y presione ENTER

o el comando:

```
:x
```

Además si desea puede ver un tutorial que hice:

**Cómo instalar y usar Vim editor de archivos para terminal, en Linux**  
[https://facilitarelsoftwarelibre.blogspot.com/2025/04/como-instalar-y-usar-vim-editor-de-texto-de-terminal.html](https://facilitarelsoftwarelibre.blogspot.com/2025/04/como-instalar-y-usar-vim-editor-de-texto-de-terminal.html)

## Para moverse a la izquierda o derecha en Vim y Nano

En Termux en las versiones modernas ya se incluyen flechas para moverse, pero también se puede teniendo presionado el botón para subir el volumen y las teclas, para:

Moverse a la Izquierda:
Volumen Arriba + A

o para:

Moverse a la derecha:
Volumen Arriba + D

# Git Merge

Necesitará usar Nano o Vim dentro de Termux para poder hacer un Merge. También puedes revisar el siguiente tutorial:

**Cómo hacer merge con git**
[https://github.com/wachin/como-hacer-merge-con-git](https://github.com/wachin/como-hacer-merge-con-git)

# Cómo actualizar el Token

Si usted, por ejemplo, le puso expiración de 90 días tendrá que generar otro token y reemplazar el anterior, porque le saldrá este error si hace push, fetch u otro comando:

```
$ git fetch
remote: Invalid username or password.
fatal: Authentication failed for 'https://github.com/wachin/wid2/'
/sdcard/wid2 $
```

hasta que usted no lo cambie. Para cambiarlo escriba:

```bash
nano ~/.git-credentials
```

y arreglar la siguiente línea:

```
https://usuario:ghp_yjikgsrtG3hjkrt4uihfhjk6G7KvhW8werOHKGRY@github.com
```

Cambie usuario por su usuario, cambie el token por su token, guarde el cambio y salga, y vuelva a hacer lo que estaba haciendo y funcionará.

# Errores comunes

## Error "dpkg was interrupted"

Es posible que le salga este error algún día:

```
list --upgradable' to see them.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

Escriba:

```bash
dpkg --configure -a
```

## Error "Unmet dependencies"

```
.0) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

Escriba:

```bash
apt --fix-broken install
```

---

Att. Washington Indacochea Delgado
linuxfrontier@proton.me
2024

Dios les bendiga

# Consultas

- [Termux Setup Storage](https://wiki.termux.com/wiki/Termux-setup-storage)
- [How to exit vi editor in Termux](https://whys.video/12605_fdroid_termux/684819_How_do_I_exit_vi_editor_in_Termux)
- [Vi](https://en.m.wikipedia.org/wiki/Vi)
- [How to change working directory in Termux](https://bit.ly/36sFQuI)
- [Cómo cambiar el directorio de trabajo en Termux](https://stackoverflow.com/a/68806210)
- [How to Fix Git Always Asking For User Credentials For HTTP(S) Authentication](https://bit.ly/3qBS5vS)
  Imagen: https://bit.ly/3urispG
- ['CANNOT LINK EXECUTABLE "node": library "libcrypto.so.3" not found](https://stackoverflow.com/questions/71337612/cannot-link-executable-node-library-libcrypto-so-3-not-found)
