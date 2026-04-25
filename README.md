# Termux on Android to install Linux terminal programs like: git, yt-dlp, nnn, tree, and others

**Updated: 2026**

Termux is a terminal emulator and Linux environment for Android that allows you to install and use git as you would from a Linux terminal. You can also install other programs like yt-dlp (for downloading YouTube videos), nnn (File Manager), tree, and others that can be used from the terminal.

Before proceeding, if you are not going to use git, do not read the parts of this tutorial that explain git usage and configurations, but if you want to install it even if you are not going to use it, the thing is that for me it is a way to verify that you can install other terminal programs in Termux.

## Install yt-dlp
After installing Termux and git you can install yt-dlp, I leave the installation separately:

- [yt-dlp](/ES/Instalar-yt-dlp.md)

## Why this tutorial

On Linux (MX Linux 21) I am using git as a type of cloud storage, similar to:

- Dropbox
- MEGA
- Google Drive

The same can be done with git from an Android phone using Termux to have files offline.

**Example:** I have created a songbook with guitar chords to use it from the Android phone and from the Linux computer:

[https://github.com/wachin/Cancionero](https://github.com/wachin/Cancionero)

> Note: With the Microsoft GitHub app in the Play Store, you cannot do everything that can be done with git from the Termux terminal.

### Pros
- Offline files on the phone

### Cons
- Manual synchronization
- A git repo contains a copy of its files in the hidden .git folder, so it will take double the space or more
- For advanced users who know version control with git
- Using the terminal
- If you are not careful when editing a file, the repository can be damaged.

#### How to avoid damaging my repository when editing a file

When you edit a file from a repository that you have cloned in Internal Storage:

- The phone should not be in battery saver mode
- After editing the file, you must close the app before sending the changes to the repository
- If you frequently use a repository to edit the same files on the phone and on the computer, it is better to use **git worktree**, as explained below to use Obsidian on Android in Termux so that the repository never gets corrupted.

### Requirements
- Phone with Android
- Repository on github.com or gitlab.com

### Usable files
You can use files for version control like: .txt, .md, or others.

In version control compatible files, only the size of the file where you edit and add information will increase.

As an important note, LibreOffice has a file for version control: .fodt
[FODT in LibreOffice](https://facilitarelsoftwarelibre.blogspot.com/2020/06/que-es-un-archivo-fodt-fodt-flat-open.html)
but there is no editor for it in the Play Store.

## What else can be done with git, install Obsidian to have your notes and knowledge on the phone
- You can use Obsidian to edit a github repository that can also be used on Linux, but the Obsidian app very frequently damages the repository, but the solution is here:
[Synchronize git on Android in Termux without damaging the repository](/ES/Sincronizar-git-en-desde-Android-en-Termux.md)
But to prevent the repository from being corrupted, you must use **git worktree**, everything is explained in this tutorial there:

- You can do push, fetch, merge and all other commands to keep the repo synchronized
- You can work with the files from:
  - Android to Linux and vice versa
  - Android to Windows and vice versa
  - Android to MAC and vice versa

> Note: I have not tested the last 2, but I know they exist.

## Compatibility between Android and Linux

In the video "Aprende GIT Ahora! Complete free course from scratch" ([https://youtu.be/VdGzPZ31ts8](https://youtu.be/VdGzPZ31ts8)), Nicolás Schurmann explains that if you synchronize a repository from Windows to "Linux or MAC" you must configure the end of line for sending text code edits. However, in this tutorial it is not necessary since using git from Termux is like using it on Linux.

This tutorial does not intend to teach how to use git. If you don't know how to use it, you can search on Google for the words "aprende git cursos" and you will find resources on Udemy, Platzi, devcode, ed.team, Coursera, or [https://github.com/JJ/aprende-git](https://github.com/JJ/aprende-git), YouTube, etc.

# Installing Termux on Android

Next, choose the option you need:
## Installing Termux and git on Android 7, 8, 9, 10, 11, 12, 13, 14+

I leave you options, as I lost my Xiaomi and bought a SAMSUNG GALAXY A15 now I use the 3rd option:

### 1st Option: Installation with Google Play Store

In the Play Store there is an updated version of Termux that says there in the app information in the same Google Play as of 2024 in which you can install Termux and git there, which I tested but you cannot install yt-dlp because that package does not exist, and maybe you cannot install more things, but if you are only going to install git you can use it well, also if you do not want to install apps from other sites it will be fine for you (to me it seems like a version with limited packages of Termux).

Also read:

[https://github.com/termux/termux-app](https://github.com/termux/termux-app)

### 2nd Option: Installation with Xiaomi

If you have a Xiaomi phone, search in the application store:

- Mi Picks
- or GetApps

Search "Termux", install it. They have as of when I lost my Xiaomi 2024 the version Termux 0.119, install it and open it.

**Update and automatically search for a repository and update**

If you are only going to use git in Termux, everything is made easy for you. Just put:

```
pkg update
```

>Note: In their version 0.119 it is not necessary to use `pkg upgrade` because `pkg update` is a kind of hybrid that does both things

A message will appear that says: "Testing the available mirrors:"

Also a message will appear:

```
Calculating upgrade... Done
The following NEW packages will be installed:
```

It will ask you:

```
Do you want to continue? [Y/n]
```

Answer:

```
y
```

and press ENTER. Be attentive because it will ask you again later, you have to put y about 5 times

Now install git with:

```
pkg install git
```

Additionally,

For Termux to have access to its internal storage, write:

```
termux-setup-storage
```

and press Enter and accept. I have used it this way on a Redmi Xiaomi Note 11 that comes with Termux 0.119 (version that only they have up to this date when I make the tutorial 2024).

Apart from that, if you wanted to choose one of the available repositories, below I indicate how.

### 3rd Option: F-Droid

Go to:

[https://f-droid.org/](https://f-droid.org/).

F-Droid is a repository of free software applications for Android devices. It works as an alternative to Google Play Store, providing open-source applications and, in many cases, privacy-focused.

Download and install F-Droid

And for you to have peace of mind, upload the downloaded Apk to:

virustotal.com

it's clean, install

then open F-Droid and in the green magnifying glass that is at the bottom left search: "Termux Terminal emulator with packages" and install it.

In this version I have used `pkg update` and `pkg upgrade` because it is not a hybrid.

### 4th Option: APK package from F-Droid

You can download if you want only the Termux APK from:

[https://f-droid.org/en/packages/com.termux/](https://f-droid.org/en/packages/com.termux/)

And for you to have peace of mind, upload the downloaded Apk to:

virustotal.com

it's clean

and install it

## Zoom in Termux

If the Termux font is very small, make it bigger using two fingers to zoom out, and then correct what was inside.

## To install Termux on Android 5, 6

See the instructions in the following link:
[https://youtu.be/eKhjvaLIPnI](https://youtu.be/eKhjvaLIPnI)

Although it might not work for anyone anymore, but I leave it as a reference.

## Disable the phantom process in Android for Termux to work correctly
If some phone with Android has the phantom process enabled, it will close some process that is running in the background, this can be negative if the user has installed some Linux in Termux, or some application that needs to be running in the background; to disable that first you have to enable the developer options:

**How to enable Developer Options**
[https://developer.android.com/studio/debug/dev-options?hl=es-419](https://developer.android.com/studio/debug/dev-options?hl=es-419)

and I leave a video but it's in English about how to disable the phantom process:

**Fix Termux Error [Process completed (signal 9) - Disable Phantom Process Killer In Android 12 & 13**
[https://youtu.be/w10I_3-Qaqw?si=VxFhe7d68SVst3QB](https://youtu.be/w10I_3-Qaqw?si=VxFhe7d68SVst3QB)

And the following are queries in Spanish:

**Android 13 wants you to squeeze the maximum power from your phone. How will it do it?**
[https://cincodias.elpais.com/smartlife/2021/12/14/lifestyle/1639489577_351730.html](https://cincodias.elpais.com/smartlife/2021/12/14/lifestyle/1639489577_351730.html)

**Android 13 will allow disabling the strict phantom process management of Android 12**
[https://www.xatakandroid.com/sistema-operativo/android-13-permitira-deshabilitar-estricta-gestion-procesos-fantasmas-android-12](https://www.xatakandroid.com/sistema-operativo/android-13-permitira-deshabilitar-estricta-gestion-procesos-fantasmas-android-12)

according to that the phantom process monitoring can be disabled from the Settings > Developer Options > Feature Flags.

## Choosing a repository

When I have installed Termux from F-Droid the next thing I do is because I want the packages that are downloaded to always be exactly the same and not some more updated or contain small differences from other packages, to avoid some malfunction, example, when there are many dependencies to use as in programs written in python that are quite delicate with their libraries and sometimes due to a change in versions they no longer work. This is, personally, what I think: Use if available always a repository, or if it were to fall, use some other, but always knowing which one it is and that it is one of those that never or least fall.

**Tutorial tested on:**

- **Termux 0.119.0 on Xiaomi Redmi Note 11**
- **Termux 0.119.0 from [https://f-droid.org/en/packages/com.termux/](https://f-droid.org/en/packages/com.termux/) on SAMSUNG GALAXY A15, but it downloads as com.termux_1022.apk**

**Note:** This tutorial I review in 2026 January

### termux-change-repo

To choose a repository, put:

```bash
termux-change-repo
```

The following indications I have seen like this as of 2024, but with new versions that come out in the future may vary, but the principle is the same, always read (it's in English) the instructions carefully, and there are two, one is that the program chooses between all the repositories one available, and the other is that you choose one (which is what I do).

When it is the first time that one uses this command in Termux 0.119, it appears like this:

```
Which repositories do you want to edit? Select with space.
[*] Main repository termux-packages
│  <  OK  >    <Cancel> │
```

**Note:** You can select with arrows plus spacebar

Or with click and give Ok

But if it comes out like this:

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

Choose from below:

```
(* ) Single mirroChoose a single mirror
```

And when it comes out like this:

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

I pressed Enter on the first option:

(*) All mirrors All in the entire world

Which means:

(*) All mirrors All in the entire world

But you could choose some special if one wants a mirror from some of those zones and would save time in searching

If it is the second time (these options may vary from one Termux version to another) that you do this process it may appear like this:

```
Do you want to choose a mirror group  
│ or a single mirror? Select with space.
│(*) Mirror grRotate between several │
│( ) Single miChoose a single mirror┤
│         <  OK  >     <Cancel>
```

in this case click on the second option so that that one marked (same as before described):

(*) Single miChoose a single mirror

whose translation is:

(*) Choose a single mirror

and click on ok

A list will appear, to move down or up you can use in termux the arrows or Page Up (PGUP) or Page Down (PGDN)

## Available Repositories (I have not seen them down)

In the version of Termux that is in the installer of Xiaomi phones "Mi Picks" I have seen that the following repos load quite a bit:

### Grimler
(Henrik Grimler https://github.com/grimler91)
Hosted in Helsinki, Finland.
Forked from the main node
Updated every hour
https://grimler.se/termux-packages-24

### BFSU
(Beijing Foreign Studies University)(http://www.bfsu.edu.cn/)(China)
https://mirrors.bfsu.edu.cn/termux/apt/termux-main

### Karibu
(karibu@freedif.com)
Hosted in Singapore (Asia)
Updated every hour
https://mirror.freedif.org/termux/termux-main

### mwt
(Matthew W. Thomas | Economist at FTC | Northwestern University Economics PhD https://github.com/mwt)
Hosted on the east/west coast of US and Europe (via CDN)
Updated 4 times a day
https://mirror.mwt.me/termux/main

### Purde
Purdue University Linux Users Group
Hosted in Indiana, USA.
Updated 4 times a day https://plug-mirror.rcac.purdue.edu/termux/termux-main

### a1batross
(https://github.com/a1batross)
Updated 4 times a day https://termux.mentality.rip/termux-main

### Librehat
(https://github.com/librehat)
Updated 4 times a day https://termux.librehat.com/apt/termux-main

### CloudFlare
CDN endpoint https://packages-cf.termux.org/apt/termux-main

## Repositories that fall frequently
And I have seen fallen to:

### sahilister
https://termux.sahilister.in/apt/termux-main: bad

### kcubeterm
https://dl.kcubeterm.com/termux-main: bad

### Astra
https://termux.astra.in.ua/apt/termux-main: bad

**ADVICE**
I use Grimler, I have never seen it down, neither BFSU (just to observe, those that fall have: bad)

The description of the repos I have seen in:

[Termux Packages Mirrors](https://github.com/termux/termux-packages/wiki/Mirrors)

To choose one, with the down arrow go to:

```
( ) Mirrors by Grimler . . .
```

or:

```
( ) Mirrors by BFSU . . .
```

Or you can also choose another.

Example, I am going to select Grimler, so with the down arrow I put there and give spacebar on the keyboard to mark it, so that it stays like this:

```
( * ) Mirrors by Grimler . . .
```

and Enter

Wait for it to finish, and put:

```
pkg update
```

so you have some questions, put:

```
y
```

In addition I explain that in the Termux version 0.118 after using pkg update you have to use:

```
pkg upgrade
```

(but as I explained above, in the Xiaomi version 0,119 it is not necessary because pkg update is a kind of hybrid that does both things)

be attentive and put the: "y" several times.

## More options will appear in termux-change-repo after updating

If you for some reason want to use the command again:

```
termux-change-repo
```

More options will appear.

if you do like me choose the option that is to manually choose one, and then:

```
pkg update
```

in addition, this command I advise using it with some frequency, it can be every month, it is to have the packages updated (in Termux 0.119 only with this is enough, and with 0.118 then you have to use pkg upgrade)

## Installing git

```
pkg install git
```

when you put this command see there which repo appears, in case the repo has changed cancel with "Ctrl + C" and change it using again `termux-change-repo` because otherwise it will start searching randomly another repo

To see the version you have installed of git put in Termux:

```
git --version
```

## Access Internal Storage

For Termux to have access to its internal storage, write:

```
termux-setup-storage
```

and press Enter and accept.

To clone a repository in internal memory first you have to get there. In Termux write:

```
cd storage
```

Then write:

```
ls
```

to see the available repositories.

Then choose the shared memory:

```
cd shared
```

Special command: You can also abbreviate steps 1 and 2 only with:

```bash
cd /sdcard
```

With either of the two methods you will reach the shared internal memory.

To know in which path you are located, write in Termux:

```bash
pwd
```

and press Enter.

Note: If it is the first time you open Termux you will be in the Termux configuration folder (it is a kind of emulation of the Linux HOME so that Termux has its files there as if it were in Linux):

```
/data/data/com.termux/files/home
```

and if you are already in internal memory and to get there you used cd shared it appears like this:

```
~/storage/shared $
```

and if I use: cd /sdcard like this:

```
/sdcard $
```

>**Note**: It is always important to know where you are located because it may be that without wanting you cloned a repository inside the Termux configuration space or in storage, and in case of passing some day that, you can use the move command "mv" to move the folder that you have cloned from the configuration space of Termux to storage and then use "mv" again to move the folder to "shared". For this it is necessary to know that if I am in "/data/data/com.termux/files/home" (which is by default where you are located when you just open Termux) outside of this is "storage", and if I am in "storage" outside of this is "shared", then if I cloned a repo called "mirepo" being in ".../home" first I must pass it to "storage" putting there: `mv su-repo storage` and then to pass it to Internal Storage put: `mv su-repo shared` and ready solved; and if only by mistake you cloned it in storage just put: `mv su-repo shared`. By the way, if you are in "shared" and want to go to ".../home" put `cd`.

## Create and use a token as password in github.com

(If you already have the token omit this step)

To be able to explain better I will use the following account:
[https://github.com/mamimeli](https://github.com/mamimeli)

Enter the following address:
[https://github.com/settings/](https://github.com/settings/)

There click on:

1. Developer Settings
2. Personal Access Token
3. Tokens (classic)
4. Generate New Token (Classic)

Or also directly in the address:
[https://github.com/settings/tokens](https://github.com/settings/tokens)

There in "**Note**" put some name.

In "**Expiration**" select an expiration time (Github advises to put an expiration time: [https://bit.ly/3BrIvA9](https://bit.ly/3BrIvA9))

In "**Select scopes**" mark "**repo**" (but if you need some other permission mark it) and at the end of the page click on "**Generate token**".

Copy immediately the generated code and have it in a safe place or in a password manager.

## Clone a repository

Once you are in the Shared Internal Storage (called shared or /sdcard -if you use the second method to get there-) clone a Repository, for example:

```bash
git clone https://github.com/mamimeli/Cancion
```

## Avoid problems with typographical characters when cloning a repository
When you clone a repository it must not have in the names of files or folders the following forbidden characters in Android not Linux since they have certain restrictions:

1. **Colon `:`**
2. **Asterisk `*`**
3. **Question mark `?`**
4. **Quotes `"`**
5. **Less than `<` and greater than `>`**
6. **Vertical bar `|`**
7. **Backslash `\`**
8. **Forward slash `/`**

In addition, avoid names that end in a space or period, as they can also cause problems in some Android compatible file systems. And if you ever commit the error of doing fetch or pull of a repository with those characters, check below the section of resolving conflicts when doing merge.

### Recommendation
To avoid these errors, use common characters like letters, numbers, hyphens `-`, and underscores `_`, which are compatible both in Android and in other file systems.

## Identify in git (and that it does not ask for the token again)

Write in Termux (replace with your data):

```bash
git config --global user.name youruser
git config --global user.email youremail@service.com
```

And the next command is for git to store the Token:

```bash
git config --global credential.helper store
```

And enter the repository with cd, in my case like this:

```bash
cd Cancion
```

Now do:

```bash
git status
```

and the following message will appear:

```
/sdcard/Cancionero $ git status
fatal: detected dubious ownership in repository at '/storage/emulated/0/Cancion'
To add an exception for this directory, call:
        git config --global --add safe.directory /storage/emulated/0/Cancion
```

There it says that it has detected a dubious owner and that add an exception to that directory to accept it as safe. In my case (you must put what appears to you) what I have to put is that which it tells me there same:

```bash
git config --global --add safe.directory /storage/emulated/0/Cancion
```

Solved (you will have to do this in each Repository)

## Edit some file or folder

Now edit some file or folder from some Android File Manager that allows (Note: The Xiaomi manager and the Samsung one do not work for this) to see not only the system folders but the repositories that you clone, this, to add a change in the repository, example with (some of the file managers have a built-in text editor):

- File Manager | File Manager Plus (free)
- Super File Explorer | ESTRONGS LIMITED (free with ads)
- Solid Explorer File Manager| NetBeans (free trial for some days)
- MiXplorer Silver | Hootan Parsa (paid)
- MiXplorer (free)
- QuickEdit Text Editor (free with ads)
- CodeFusion: Code Editor (free)
- WPS Office (free, paid exports to PDF)
- Microsoft 365 (Office) + OneDrive (free, exports to PDF with internet)
- Microsoft Word + OneDrive (free, exports to PDF with internet)
- Google Docs + Google Drive (free, exports to PDF with internet)
- AndrOpen Office (free, paid exports to PDF)
- nano or Vim to edit text files from the command line

see all the explanations of how to use them in this section:

[Edit repository files git on Android from editors or file manager Apps](/ES/Editar-desde-editor-o-administrador-de-archivos.md)

now add it and upload the change to GitHub with example with the following indications:

### Adding the change with git add .

No matter how you have made the change to some file of your repository, add the change you have made in git example with:

```bash
git add .
```

and we must make a commit, example:

```bash
git commit -m "Commit name"
```

And then send the changes to the remote:

```bash
git push
```

and when it asks you for your User put it, and when it asks you for the Password put your **Token** (if you did well following the sequence the next time it will not ask for the token).

The file will be created (this is internal, you will not see it):

.git-credentials

it will be created within the HOME that Termux emulates, the file that will contain the Token.

> **Note:** If you then want to use another github or gitlab user you must enter it and it will change, and if you want to return to the previous one you must enter it again, that is, the last entered user will always be active.

And with that we can already do:

git status
push
fetch
merge
pull, etc

# Using terminal text editors like Nano or Vim
Using Termux will come the time that you have to use some command line text editor like "Nano" that came installed in the Xiaomi "Mi Picks" Termux, but if it is not installed, install it like this:

```bash
pkg install nano
```

or if you use Vim (do not confuse with vi which is a version that may be installed but is limited, Vim is the complete version)

```
pkg install vim
```

To see the nano version write:

```bash
nano --version
```

or for Vim

```
vim --version
```

## How to set nano or another terminal editor as default
If by chance you install another terminal text editor and then nano or another that you use is no longer the default editor, make it default again by putting:

```
update-alternatives --config editor
```

there the list of installed editors will appear for one to be able to choose which one will be default, depending on which ones are installed, e.g. if they are three it will show:

0

1

2

and you must write the corresponding number and Enter.

## Edit text with Nano

To edit, for example, the git credentials configuration file, write:

```bash
nano ~/.git-credentials
```

To edit text it is very simple, you just have to position yourself in the appropriate position with the Termux arrows and start writing (or pasting) text.

To save changes: Nano abbreviates CTRL with ^, so CTRL + O is equal to:

^O

and in nano it appears like this:

^O Save

So, to save press:

CTRL + O

and a message will appear that says something like:

```
File name to write: file-name.txt
```

and press ENTER.

> Note: It is important to note that it is the letter O, not zero.

### How to exit Nano:

Press CTRL + X to exit, since Nano abbreviates CTRL with ^, so CTRL + X is equal to: ^X which is to Exit.
(Note: If you are writing something and have pressed CTRL + O the CTRL + X option will not be available until you press ENTER) and you will exit nano.

When doing that it will appear in the middle of Termux:

```
File Name to Write:<tconfig
```

That is the abbreviation of the file: .gitconfig. You do not change anything and just press ENTER (If you change the name and press ENTER another file will be created containing what you have edited).

In addition you can see a tutorial that I made:

**How to use nano in the Linux terminal to edit text files**
[https://facilitarelsoftwarelibre.blogspot.com/2024/08/como-usar-nano-en-linux.html](https://facilitarelsoftwarelibre.blogspot.com/2024/08/como-usar-nano-en-linux.html)

## Modify gitconfig with Vim

To use Vim example to edit the .gitconfig file

To edit the git configuration file write:

```bash
vim ~/.gitconfig
```

Warning: You must be careful not to delete something from the code because if you do it will damage git. If that were to happen write:

```bash
rm ~/.gitconfig
```

and identify yourself again.

Editing: Once the Vim editor environment appears we will be by default in command mode, and if we want to edit press once the key:

i

when doing so it will change to edit mode and edit.
Once you no longer want to continue editing press:

ESC

which is to change to command mode.

To save press:

```
:w
```

> **Note:** That w means write = write

and press:

ENTER

To stop writing or exit Vim, use the command:

```
:q
```

and press ENTER.

To save a file and exit Vim simultaneously, use the command:

```
:wq
```

and press ENTER

or the command:

```
:x
```

In addition you can see a tutorial that I made:

**How to install and use Vim terminal text editor, in Linux**
[https://facilitarelsoftwarelibre.blogspot.com/2025/04/como-instalar-y-usar-vim-editor-de-texto-de-terminal.html](https://facilitarelsoftwarelibre.blogspot.com/2025/04/como-instalar-y-usar-vim-editor-de-texto-de-terminal.html)

## To move left or right in Vim and Nano

In Termux in modern versions arrows are already included to move, but you can also by holding the volume up button and the keys, for:

Move to the Left:
Volume Up + A

or for:

Move to the right:
Volume Up + D

# Git Merge

You will need to use Nano or Vim inside Termux to be able to do a Merge. You can also check the following tutorial:

**How to do merge with git**
[https://github.com/wachin/como-hacer-merge-con-git](https://github.com/wachin/como-hacer-merge-con-git)

# How to update the Token

If you, for example, put an expiration of 90 days you will have to generate another token and replace the previous one, because you will get this error if you do push, fetch or another command:

```
$ git fetch
remote: Invalid username or password.
fatal: Authentication failed for 'https://github.com/wachin/wid2/'
/sdcard/wid2 $
```

until you change it. To change it write:

```bash
nano ~/.git-credentials
```

and fix the following line:

```
https://user:ghp_yjikgsrtG3hjkrt4uihfhjk6G7KvhW8werOHKGRY@github.com
```

Change user for your user, change the token for your token, save the change and exit, and go back to doing what you were doing and it will work.

# Common errors

## Error "dpkg was interrupted"

It is possible that this error comes out to you some day:

```
list --upgradable' to see them.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

Write:

```bash
dpkg --configure -a
```

## Error "Unmet dependencies"

```
.0) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

Write:

```bash
apt --fix-broken install
```

---

Att. Washington Indacochea Delgado
linuxfrontier@proton.me
2024

God bless you

# Queries

- [Termux Setup Storage](https://wiki.termux.com/wiki/Termux-setup-storage)
- [How to exit vi editor in Termux](https://whys.video/12605_fdroid_termux/684819_How_do_I_exit_vi_editor_in_Termux)
- [Vi](https://en.m.wikipedia.org/wiki/Vi)
- [How to change working directory in Termux](https://bit.ly/36sFQuI)
- [Cómo cambiar el directorio de trabajo en Termux](https://stackoverflow.com/a/68806210)
- [How to Fix Git Always Asking For User Credentials For HTTP(S) Authentication](https://bit.ly/3qBS5vS)
  Image: https://bit.ly/3urispG
- ['CANNOT LINK EXECUTABLE "node": library "libcrypto.so.3" not found](https://stackoverflow.com/questions/71337612/cannot-link-executable-node-library-libcrypto-so-3-not-found)