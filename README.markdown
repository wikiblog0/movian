Movian mediaplayer
==================

(c) 2006 - 2018 Lonelycoder AB

[![Build status](https://doozer.io/badge/andoma/movian/buildstatus/master)](https://doozer.io/user/andoma/movian)

Para mas informacion acerca de la aplicacion, por favor visitar:

[https://movian.tv/](https://movian.tv/)

Este repositorio aloja el codigo fuente del port para Wii y la ultima version del codigo fuente de Movian alojado en el github oficial. Por lo que he visto el codigo fuente actualizado a la ultima version oficial de Movian que es la 5.0.548 esta alojado en la pagina web de la aplicacion, en este enlace podran verlo: https://movian.tv/projects/movian/repository?utf8=%E2%9C%93&rev=master

## Como crear tu distribucion en Wii

Para hacer tu distribucion de Wii con el codigo fuente existente (fixwii) necesitas:

- devkitPro:
    devkitPPC r21
    libogc 1.8.3
    libfat-ogc 1.0.5
- freetype cross-compiled for PPC.

Para tu conveniencia hay un script que descarga/crea todo lo necesario. Para ejecutarlo solo escribe:

$ support/wiisetup

Haga esto directamente desde el directorio raíz de Showtime. Esto descargará, descomprimira, creara e instalara todo lo necesario en el directorio wiisupport
Por defecto configure.wii buscará en estos directorios para devkitPro y freetype, así que todo lo que tiene que hacer ahora es: 

$ ./configure.wii
$ make

Si tiene devkitpro y/o freetype en otro directorio, puede configurar la ruta de ellos en configure.wii (ver ./configure.wii --help para más detalles)

Nota: el valor predeterminado de libogc es un máximo de 16 threads. Esto está al borde de la aplicacion movian (showtime nombre anterior). Por lo tanto, el script wiisetup instalara una nueva versión de lwp_config.h (consulte support/lwp_config.h) antes de compilar libogc. Si tiene la intención de usar un stock libogc, debe tener en cuenta este hecho.

# Paquete Homebrew

El sistema makefile puede construir un paquete homebrew. Para hacer esto, escriba:

$ make homebrew

La salida residirá en "build.wii/bundle/". Tanto un directorio para aplicaciones
y un archivo zip es lo que generara.

## Observaciones

A pesar que dejo las instrucciones de como compilar la version existente del port de Wii, el principal objetivo es actualizar la aplicacion a la ultima version de Movian para que sea compatible con los plugins disponibles que hay en la actualidad y los que puedan aparecer para asi habilitar servicios de streaming que habian en Wii y Wii U como youtube o Netflix o que nunca hubieron como Twitch. Para este caso necesitan agregar las ultimas novedades que tiene la ultima version del codigo fuente que esta alojado en la pagina web de Movian: https://movian.tv/projects/movian/repository?utf8=%E2%9C%93&rev=master o en caso que la pagina este caida pueden usar el codigo fuente que dejare en la seccion de release sin embargo como mencione anteriormente ese codigo fuente no es la ultima version.

En la seccion de programacion dejare los enlaces de las herramientas necesarias para que puedan actualizar las librerias utilizadas por el port de Wii para que estas sean compatibles con la virtual wii de Wii U y se pueda usar el gamepad y el overclock para mejorar el desempeño de la aplicacion.

Por ultimo, el segundo objetivo que tengo con este repositorio es que el programador o programadores que quieran retomar el proyecto y actualizar la aplicacion con las ultimas librerias disponibles, es que una vez que la version de wii/virtual wii de Wii U sea estable se pueda hacer un port nativo a Wii U para aprovechar la resolucion hd de la consola y ademas de enriquecer el homebrew de Wii U con un centro multimedia digno que ayude a habilitar los servicios de streaming que habian en Wii U y de enriquecer con otros servicios que no estaban pero que serian provechos tenerlos en Wii U. Para esto es necesario que el programador aprenda a crear plugins para los servicios de streaming que la comunidad o el quiera traer para Wii o Wii U. Aqui dejo el link de la guia para crear plugins para movian: https://movian.tv/projects/movian/wiki/PluginDevelopment 
Dejo la guia de como publicar tus plugins, link: https://movian.tv/projects/movian/wiki/PluginPublishing 

# Programacion

En esta seccion dejare los links de las herramientas necesarias para Wii/virtual wii y Wii U:

## Wii/Virtual wii

- [devkitpro installer](https://github.com/devkitPro/installer/releases) este sirve para instalar y actualizar las herramientas y librerias que proporciona devkitpro.
- [libogc](https://github.com/devkitPro/libogc/releases) Libreria en lenguaje c para aplicaciones homebrew de Wii y Gamecube.
- [libwiidrc](https://github.com/FIX94/libwiidrc/releases)Libreria especial para hacer compatible la Wii U gamepad en aplicaciones homebrew de Wii U.
- [pacman](https://github.com/devkitPro/pacman/releases) Libreria de devkitpro que descarga la sublibreria de devkitppc necesaria para crear la distribucion de wii.

## Librerias que se van a ocupar para hacer el port de Wii U
- [pacman](https://github.com/devkitPro/pacman/releases) Libreria de devkitpro que descarga la sublibreria de devkitppc que va ser necesaria para hacer el port de 
Wii U.
- [Wii U Toolkit (WUT)](https://github.com/devkitPro/wut/releases) libreria para crear los ejecutables de las aplicaciones homebrew de Wii U rpx/rpl
- [SDL](https://github.com/yawut/SDL/releases) port de la libreria sdl2 para su uso en homebrew de Wii U.

## Posibles herramientas que se puedan ocupar en Wii U:
- [gx2textureShader](https://github.com/rw-r-r-0644/gx2textureShader) es una simple aplicacion para renderizar graficos 2D en Wii U.
- [librw](https://github.com/GaryOderNichts/librw) reimplementacion de la RenderWare Graphics engine en los renderizados 3D de los graficos gx2 de la Wii U. Esta libreria se utilizo para renderizar los graficos de los ports de Wii U de los GTA 3 y GTA Vice City.

## Para las herramientas de devkitpro dejo los siguientes enlaces que le serviran de guia para su uso: 
- https://devkitpro.org/wiki/Getting_Started
- https://devkitpro.org/wiki/devkitPro_pacman

## Para hacer pruebas al ejecutable rpx/rpl de Wii U se ocupan estas herramientas:
- [RPL Studio](https://github.com/BullyWiiPlaza/RPL-Studio)
- [RPL2elf](https://gbatemp.net/threads/tutorial-how-to-decompress-and-repack-rpx-rpl-files.399934/) Para mas informacion visitar este link:https://github.com/Relys/rpl2elf
- [RPXReader](https://github.com/phacoxcll/RPXReader)

# Notas finales para los programadores que quieran hacer el port de Wii U:
Para los usuarios de Wii U o emulador CEMU que tengan conocimiento en programacion y quieren entrar al mundo de desarrollo de aplicaciones o emuladores homebrew de Wii U, les dejo el link a la guia de programacion de Yawt donde se explica al detalle como comenzar a programar y lo que se necesita. 
Link: https://github.com/yawut/ProgrammingOnTheU/blob/master/tutorial/Chapter%201.md 

Finalmente  les dejo el blog de Clownacy donde explica de manera general como hacer ports de aplicaciones o juegos android a Wii U. Link: https://clownacy.wordpress.com/2021/02/12/porting-sonic-cd-2011-to-the-wii-u/
