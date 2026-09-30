# Linux - Introducción a la terminal

Uno de los primeros comandos que podemos ejecutar es `whoami`. Esto es importante en ciberseguridad porque con frecuencia vas a cambiar de usuario dentro de una máquina, lo que determina qué cosas podés y no podés hacer.

| Comando | Descripción |
|---|---|
| `whoami` | Indica quién sos en el sistema. |

También podemos pedirle a Linux que muestre un texto específico.

| Comando | Descripción |
|---|---|
| `echo` | Muestra el texto específico que se le proporciona. |

### Ejemplos

```bash
whoami
```
Podría devolver:
juanito

Esto indica que el usuario actual del sistema es juanito.

```bash
echo "Hola Linux"
```
Devuelve:
Hola Linux

## Navegación por el sistema de archivos

Para navegar por los archivos del sistema utilizando la terminal. Hay cuatro comandos que permiten realizar casi todas las tareas básicas de navegación:

| **Comando** | **Descripción** |
|---|---|
| **`ls`** | Lista lo que hay en la carpeta actual. |
| **`cd`** | Cambia de directorio — permite entrar en una carpeta. |
| **`cat`** | Muestra el contenido de un archivo. |
| **`pwd`** | Muestra el directorio de trabajo actual — "¿dónde estoy?" |

## Buscar archivos y contenido

| **Comando** | **Descripción** |
|---|---|
| **`find`** | Busca archivos por su nombre. Por ejemplo, `find -name passwords.txt` |
| **`grep`** | Busca texto *dentro* de los archivos. Por ejemplo, `grep "password123" passwords.txt` |

## Combinar comandos y capturar su salida

Son caracteres especiales que permiten combinar comandos. Estos se conocen como **"operadores"** y le indican a Linux cómo debe procesar los comandos.

Podemos utilizarlos para combinar comandos entre sí o para realizar lo que se conoce como **redirección**, es decir, enviar la salida de un comando a otro lugar. Veamos algunos de ellos:

| **Operador** | **Descripción** |
|---|---|
| **`&`** | Ejecuta el comando, pero no espera a que termine antes de permitirte hacer otra cosa. El comando se ejecuta en segundo plano. Es útil para comandos que pueden tardar en completarse o que querés mantener ejecutándose. |
| **`&&`** | Ejecuta ambos comandos, pero espera a que termine el primero antes de ejecutar el siguiente. |
| **`>`** | Se utiliza para redirigir la salida. Permite tomar la salida de un comando y enviarla a un archivo. Este operador sobrescribe cualquier contenido que ya exista en el archivo. |
| **`>>`** | También redirige la salida, pero en lugar de sobrescribir el contenido existente, agrega la nueva salida al final del archivo. |

## ¿Qué es SSH y cómo funciona?

**Secure Shell (SSH)** es un protocolo que permite establecer una conexión segura entre dispositivos mediante una comunicación cifrada.

Utilizando **criptografía**, cualquier información que enviamos en un formato legible para las personas es cifrada antes de viajar a través de una red. Una vez que llega a la máquina remota, la información es descifrada.

- **SSH permite ejecutar comandos de forma remota en otro dispositivo.**
- **Los datos enviados entre los dispositivos se cifran cuando viajan a través de una red**, como Internet.

## Usar SSH para iniciar sesión en tu máquina Linux

La sintaxis para utilizar **SSH** es muy sencilla. Solo necesitamos proporcionar dos cosas:

1. La **dirección IP** de la máquina remota.
2. Las **credenciales correctas** de una cuenta válida para iniciar sesión en la máquina remota.

### Sintaxis

```bash
ssh usuario@direccion_IP
```

![Ejemplo de conexión SSH](https://cdn-images.tryhackme.com/user-uploads/6241db5522713b00497f96ac/room-content/6241db5522713b00497f96ac-1781538836713.png)

## Usar `ls` para ver el contenido de un directorio

Podemos utilizar el comando `ls` para ver el contenido de un directorio.

```bash
tryhackme@linux2:~$ ls
folder1
tryhackme@linux2:~$
```

## Usar `ls` para ver carpetas ocultas

```bash
tryhackme@linux2:~$ ls -a
.hiddenfolder folder1
tryhackme@linux2:~$
```

## Listing the options we can use with `ls`

```bash
tryhackme@linux2:~$ ls --help
Usage: ls [OPTION]... [FILE]...
List information about the FILEs (the current directory by default).
Sort entries alphabetically if none of -cftuvSUX nor --sort is specified.

Mandatory arguments to long options are mandatory for short options too.
  -a, --all                  do not ignore entries starting with .
  -A, --almost-all           do not list implied . and ..
      --author               with -l, print the author of each file
  -b, --escape               print C-style escapes for nongraphic characters
      --block-size=SIZE      with -l, scale sizes by SIZE when printing them;
                               e.g., '--block-size=M'; see SIZE format below
  -B, --ignore-backups       do not list implied entries ending with ~
  -c                         with -lt: sort by, and show, ctime (time of last
                               modification of file status information);
                               with -l: show ctime and sort by name;
                               otherwise: sort by ctime, newest first
  -C                         list entries by columns
      --color[=WHEN]         colorize the output; WHEN can be 'always' (default
                               if omitted), 'auto', or 'never'; more info below
  -d, --directory            list directories themselves, not their contents
  -D, --dired                generate output designed for Emacs' dired mode
  -f                         do not sort, enable -aU, disable -ls --color
  -F, --classify             append indicator (one of */=>@|) to entries
      --file-type            likewise, except do not append '*'
      --format=WORD          across -x, commas -m, horizontal -x, long -l,
                               single-column -1, verbose -l, vertical -C
      --full-time            like -l --time-style=full-iso
  -g                         like -l, but do not list owner
      --group-directories-first
tryhackme@linux2:~$
```
        
```bash
tryhackme@linux2:~$ man ls
NAME
       ls - list directory contents

SYNOPSIS
       ls [OPTION]... [FILE]...

DESCRIPTION
       List  information  about the FILEs (the current directory by default).  Sort entries alphabetically if none of
       -cftuvSUX nor --sort is specified.

       Mandatory arguments to long options are mandatory for short options too.

       -a, --all
              do not ignore entries starting with .

       -A, --almost-all
              do not list implied . and ..

       --author
              with -l, print the author of each file

       -b, --escape
              print C-style escapes for nongraphic characters

       --block-size=SIZE
              with -l, scale sizes by SIZE when printing them; e.g., '--block-size=M'; see SIZE format below

 Manual page ls(1) line 1 (press h for help or q to quit)
```
        

## Más comandos para interactuar con el sistema de archivos

Existen más comandos que podemos utilizar para interactuar con el **sistema de archivos**. Entre ellos, podemos:

- Crear archivos y carpetas.
- Mover archivos y carpetas.
- Eliminar archivos y carpetas.

Más específicamente, podemos utilizar los siguientes comandos:

| **Comando** | **Nombre completo** | **Propósito** |
|---|---|---|
| `touch` | touch | Crear un archivo. |
| `mkdir` | make directory | Crear una carpeta. |
| `cp` | copy | Copiar un archivo o carpeta. |
| `mv` | move | Mover un archivo o carpeta. |
| `rm` | remove | Eliminar un archivo o carpeta. |
| `file` | file | Determinar el tipo de un archivo. |

## Eliminar archivos y carpetas (`rm`)

Para eliminar archivos simplemente utilizando `rm` seguido del nombre del archivo que querés eliminar.

Sin embargo, para eliminar una carpeta, necesitás utilizar la opción `-R` junto con el nombre del directorio que querés eliminar.

## Usar `rm` para eliminar un archivo

```bash
tryhackme@linux2:~$ rm note
tryhackme@linux2:~$ ls
folder1 mydirectory
```

## Using rm recursively to remove a directory

```bash
tryhackme@linux2:~$ rm -R mydirectory
tryhackme@linux2:~$ ls           
folder1
```
        
## Copiar y mover archivos y carpetas (`cp`, `mv`)

Copiar con `cp`, este comando recibe dos argumentos:

1. El nombre del archivo existente.
2. El nombre que queremos asignarle al nuevo archivo al realizar la copia.

`cp` copia todo el contenido del archivo existente dentro del nuevo archivo.

En el ejemplo, se copia el archivo `note` y creando una copia llamada `note2`.

```bash
tryhackme@linux2:~$ cp note note2
tryhackme@linux2:~$ ls           
folder1 note note2
```

## Mover y renombrar archivos (`mv`)

Mover un archivo requiere dos argumentos, al igual que el comando `cp`.

Sin embargo, en lugar de copiar y/o crear un archivo nuevo, `mv` mueve o modifica el segundo archivo que proporcionamos como argumento.

Se utiliza `mv` para:

- Mover un archivo a una carpeta diferente.
- Renombrar un archivo.
- Renombrar una carpeta.

Por ejemplo, en el siguiente caso, estamos cambiando el nombre del archivo `note2` a `note3`.

El archivo `note3` tendrá ahora el mismo contenido que tenía `note2`.

## Usar `mv` para mover o renombrar un archivo

```bash
tryhackme@linux2:~$ mv note2 note3
tryhackme@linux2:~$ ls
folder1 note note3
```

## Determinar el tipo de archivo (`file`)

Hasta ahora, los archivos que hemos utilizado en nuestros ejemplos no tenían ninguna extensión. Sin conocer el contexto de por qué existe un archivo, realmente no podemos saber cuál es su propósito o qué tipo de contenido contiene.

El comando `file` recibe un argumento y nos permite determinar qué tipo de archivo tenemos.

```bash
tryhackme@linux2:~$ file note
note: ASCII text
```

## Using ls -lh to list the permissions of all files in the directory

```bash
tryhackme@linux2:~$ ls -lh
-rw-r--r-- 1 cmnatic cmnatic 0 Feb 19 10:37 file1
-rw-r--r-- 8 cmnatic cmnatic 0 Feb 19 10:37 file2
```

## Using su to switch to user2 interactively
      
```bash
tryhackme@linux2:~$ su user2
Password:
user2@linux2:/home/tryhackme$
```

## Permisos de archivos en formato numérico

En Linux, cada archivo y directorio tiene un conjunto de permisos que controlan quién puede leerlo, escribirlo o ejecutarlo. Estos permisos suelen mostrarse en formato simbólico, por ejemplo:

```bash
rwxrwxrwx
```

Este formato se divide en tres grupos: 
| Sección | Se aplica a | Ejemplo | 
|-----------|--------------|---------| 
| Primeros 3 | Propietario | `rwx` | 
| Siguientes 3 | Grupo | `rwx` | 
| Últimos 3 | Otros | `rwx` | 

Cada letra representa un permiso específico: 
- `r` = lectura (*read*) 
- `w` = escritura (*write*) 
- `x` = ejecución (*execute*)

## Convertir permisos simbólicos a números 

Cada permiso tiene un valor numérico: 
| Permiso | Valor | 
|---------------|-------| 
| Lectura (`r`) | 4 | 
| Escritura (`w`) | 2 | 
| Ejecución (`x`) | 1 | 

Para calcular el valor numérico, se suman los valores de cada grupo. 

### Ejemplo: `rwxrwxrwx` 

Desglose: 

| Grupo | Permisos | Cálculo | Valor | 
|-------------|----------|-----------|-------| 
| Propietario | `rwx` | 4 + 2 + 1 | 7 | 
| Grupo | `rwx` | 4 + 2 + 1 | 7 | 
| Otros | `rwx` | 4 + 2 + 1 | 7 | 

Por lo tanto: rwxrwxrwx = 777

## Más ejemplos comunes

| Simbólico   | Numérico | Significado |
|-------------|----------|-------------|
| `rwxr-xr-x` | 755      | El propietario puede hacer todo; los demás pueden leer y ejecutar |
| `rw-r--r--` | 644      | El propietario puede leer y escribir; los demás solo pueden leer |
| `rwx------` | 700      | Solo el propietario tiene acceso |

## Por qué es importante

Entender los permisos numéricos es importante porque:

- Muchos comandos de Linux usan valores numéricos (por ejemplo, `chmod 755 archivo`)
- Permite identificar rápidamente riesgos de seguridad
- Permite controlar quién puede acceder a archivos sensibles

Por ejemplo: chmod 750 system_overview.txt

Esto significa:

- **Propietario:** acceso total
- **Grupo:** lectura + ejecución
- **Otros:** sin acceso

Ejemplos de comandos:

- Saber quien es el autor de un archivo: `ls -l filename`
- Switch de user a "user2”: `su user2`

## Directorios importantes del sistema Linux

Linux organiza su sistema de archivos a partir de un directorio raíz (`/`). Estos son cuatro directorios clave, especialmente en ciberseguridad y pentesting.

## `/etc`

El nombre viene de *etcetera*. Aquí se guardan los **archivos de configuración del sistema** que utiliza el sistema operativo.

Archivos destacados:

| Archivo   | Función |
|-----------|---------|
| `sudoers` | Define qué usuarios y grupos pueden ejecutar comandos como `root` mediante `sudo` |
| `passwd`  | Contiene la lista de usuarios del sistema |
| `shadow`  | Almacena las contraseñas de cada usuario de forma cifrada (hash **sha512**) |

Ejemplo:

```bash
tryhackme@linux2:/etc$ ls
shadow passwd sudoers sudoers.d
```

`passwd` y `shadow` son especialmente relevantes en seguridad: el primero lista los usuarios y el segundo guarda sus contraseñas hasheadas.

## `/var`

Viene de *variable data* (datos variables). Almacena información que los servicios y aplicaciones **escriben o consultan con frecuencia**, y que no pertenece a un usuario en particular.

Ejemplos de contenido:

- **Logs** de servicios y aplicaciones, en `/var/log`
- Bases de datos
- Copias de seguridad (`backups`)

```bash
tryhackme@linux2:/var$ ls
backups log opt tmp
```

## `/root`

Es el **directorio personal del usuario `root`** (el superusuario).

A diferencia del resto de usuarios, cuyos directorios están dentro de `/home`, el de `root` **no** está en `/home/root`, sino directamente en `/root`.

```bash
root@linux2:~# ls
myfile myfolder passwords.xlsx
```

## `/tmp`

Viene de *temporary* (temporal). Guarda datos que solo se necesitan una o dos veces y es un directorio **volátil**: su contenido se borra al reiniciar el equipo, de forma similar a la memoria RAM.

**Por qué importa en pentesting:** cualquier usuario puede escribir en `/tmp` por defecto. Por eso, una vez dentro de una máquina, es un buen lugar para guardar scripts de enumeración y otras herramientas.

```bash
root@linux2:/tmp# ls
todelete trash.txt rubbish.bin
```

## Editores de texto en la terminal

## Los operadores de redirección (`>` y `>>`)

Normalmente el resultado de un comando se muestra en pantalla. Los operadores de redirección **lo envían a un archivo** en lugar de mostrarlo.

| Operador | Qué hace                        | Comportamiento                               |
|----------|---------------------------------|----------------------------------------------|
| `>`      | Redirige la salida a un archivo | **Sobrescribe** el contenido anterior        |
| `>>`     | Redirige la salida a un archivo | **Agrega** al final, sin borrar lo anterior  |

### Ejemplo paso a paso

**1. Crear un archivo con `>`:**

```bash
$ echo "Primera línea" > notas.txt
```

Ahora `notas.txt` contiene: `Primera línea`

**2. Agregar otra línea con `>>`:**

```bash
$ echo "Segunda línea" >> notas.txt
```

Ahora `notas.txt` contiene:

```
Primera línea
Segunda línea
```

**3. Cuidado: usar `>` otra vez borra todo lo anterior:**

```bash
$ echo "Texto nuevo" > notas.txt
```

Ahora `notas.txt` contiene solo: `Texto nuevo`

Hasta ahora hemos guardado texto en archivos usando solo el comando `echo` junto con los operadores de redirección (`>` y `>>`). Esto funciona, pero **no es eficiente** cuando trabajas con archivos de varias líneas o con mucho contenido.

Para eso existen los **editores de texto de terminal**. Hay varias opciones, con distintos niveles de facilidad y potencia. Aquí veremos `nano` y una alternativa más avanzada llamada `VIM`.

## Nano

`nano` es el editor más sencillo para empezar. Para crear o editar un archivo, usa:

```bash
nano nombre_del_archivo
```

Reemplaza `nombre_del_archivo` por el nombre del archivo que quieras editar. Si no existe, se creará al guardar.

### Abrir Nano

```bash
tryhackme@linux3:/tmp# nano myfile
  GNU nano 4.8                                             myfile                                                       

^G Get Help    ^O Write Out   ^W Where Is    ^K Cut Text    ^J Justify     ^C Cur Pos     M-U Undo       M-A Mark Text
^X Exit        ^R Read File   ^\ Replace     ^U Paste Text  ^T To Spell    ^_ Go To Line  M-E Redo       M-6 Copy Text
```

Al presionar `Enter`, se abrirá `nano` y podrás empezar a escribir o modificar el texto. Te mueves entre líneas con las flechas **arriba** y **abajo**, y creas una línea nueva con `Enter`.

### Escribir texto en Nano

```bash
tryhackme@linux3:/tmp# nano myfile
  GNU nano 4.8                                             myfile                                             Modified  

Hello TryHackMe
I can write things into "myfile"


^G Get Help    ^O Write Out   ^W Where Is    ^K Cut Text    ^J Justify     ^C Cur Pos     M-U Undo       M-A Mark Text
^X Exit        ^R Read File   ^\ Replace     ^U Paste Text  ^T To Spell    ^_ Go To Line  M-E Redo       M-6 Copy Text
```

Fíjate en la indicación `Modified` en la parte superior: significa que el archivo tiene cambios sin guardar.

### Funciones principales

`nano` incluye lo esencial que se espera de un editor:

- Buscar texto
- Copiar y pegar
- Saltar a un número de línea
- Ver en qué línea te encuentras

Se usan con la tecla `Ctrl` (representada como `^` en pantalla) combinada con una letra. Por ejemplo, para salir de `nano` presiona `Ctrl + X`.

### Atajos más útiles

| Atajo      | Acción                          |
|------------|---------------------------------|
| `Ctrl + O` | Guardar el archivo (*Write Out*) |
| `Ctrl + X` | Salir del editor                |
| `Ctrl + W` | Buscar texto (*Where Is*)       |
| `Ctrl + K` | Cortar línea                    |
| `Ctrl + U` | Pegar texto                     |
| `Ctrl + \` | Buscar y reemplazar             |
| `Ctrl + _` | Ir a un número de línea         |
| `Ctrl + G` | Mostrar la ayuda                |

En la parte inferior de `nano` siempre verás la lista de atajos disponibles, así que no necesitas memorizarlos al principio.

## VIM

`VIM` es un editor **mucho más avanzado**. No se espera que domines todas sus funciones, pero conviene conocerlo para mejorar tus habilidades en Linux.

Aunque requiere bastante más tiempo para aprenderlo, ofrece ventajas importantes:

- **Personalizable:** puedes modificar los atajos de teclado a tu gusto.
- **Resaltado de sintaxis:** muy útil para escribir o mantener código, por lo que es popular entre desarrolladores.
- **Disponibilidad:** funciona en terminales donde `nano` podría no estar instalado.
- **Muchos recursos:** existen [hojas de referencia (cheatsheets)](https://vim.rtorr.com/), tutoriales y más material de apoyo.

## Comparativa

| Característica       | `nano`            | `VIM`                     |
|----------------------|-------------------|---------------------------|
| Dificultad           | Fácil             | Avanzada                  |
| Curva de aprendizaje | Muy corta         | Larga                     |
| Personalización      | Limitada          | Muy alta                  |
| Resaltado de sintaxis| Básico            | Completo                  |
| Ideal para           | Ediciones rápidas | Programar y uso intensivo |




