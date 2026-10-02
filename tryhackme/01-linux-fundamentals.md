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

## Descarga de archivos con `wget`

Este comando permite descargar archivos de la web mediante HTTP, igual que si accedieras al archivo desde tu navegador. Solo necesitas indicar la dirección del recurso que quieres descargar. Por ejemplo, si quisieras descargar un archivo llamado `myfile.txt` y conocieras su dirección web, el comando sería así:

```bash
wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.txt
```
---

## Transferir archivos desde tu equipo con SCP (SSH)

**SCP** (*Secure Copy*) es, como su nombre indica, una forma segura de copiar archivos. A diferencia del comando `cp`, que trabaja de forma local, `scp` permite transferir archivos entre dos equipos usando el protocolo SSH, que proporciona tanto autenticación como cifrado.

SCP funciona con un modelo de **ORIGEN** y **DESTINO**, y permite:

- Copiar archivos y directorios desde tu sistema actual a un sistema remoto.
- Copiar archivos y directorios desde un sistema remoto a tu sistema actual.

Para ello, es necesario conocer las credenciales (usuario y contraseña) de un usuario en el sistema local y de otro en el sistema remoto.

### Ejemplo 1: copiar un archivo del equipo local al remoto

Usaremos los siguientes datos:

| Variable                                               | Valor          |
| ------------------------------------------------------ | -------------- |
| Dirección IP del sistema remoto                        | `192.168.1.30` |
| Usuario en el sistema remoto                           | `ubuntu`       |
| Nombre del archivo en el sistema local                 | `important.txt` |
| Nombre con el que se guardará en el sistema remoto     | `transferred.txt` |

Con esta información, armamos el comando recordando que el formato de SCP es simplemente ORIGEN y DESTINO:

```bash
scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt
```

### Ejemplo 2: copiar un archivo del equipo remoto al local

Ahora hagamos lo inverso: copiar un archivo desde un equipo remoto en el que no hemos iniciado sesión.

| Variable                                               | Valor          |
| ------------------------------------------------------ | -------------- |
| Dirección IP del sistema remoto                        | `192.168.1.30` |
| Usuario en el sistema remoto                           | `ubuntu`       |
| Nombre del archivo en el sistema remoto                | `documents.txt` |
| Nombre con el que se guardará en nuestro sistema       | `notes.txt`    |

El comando queda así:

```bash
scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt
```
---

## Compartir archivos desde tu equipo con un servidor web

Las máquinas Ubuntu vienen con `python3` preinstalado. Python incluye un módulo ligero y fácil de usar llamado `http.server` (*HTTPServer*), que convierte tu equipo en un servidor web básico. Con él puedes compartir tus propios archivos para que otro equipo los descargue con herramientas como `curl` o `wget`.

Por defecto, el servidor comparte los archivos del directorio desde el que ejecutas el comando, aunque esto se puede cambiar con las opciones descritas en las páginas del manual. Para iniciar el módulo, basta con ejecutar en la terminal:

```bash
python3 -m http.server
```

En el siguiente ejemplo se comparte un directorio llamado `webserver`, que contiene un único archivo llamado `file`:

**Iniciar un servidor web con Python**

```bash
tryhackme@linux3:/webserver# python3 -m http.server
Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
```

Ahora usemos `wget` para descargar el archivo indicando la dirección `MACHINE_IP` y el nombre del archivo. Como el servidor de Python escucha en el puerto `8000`, debes especificarlo en el comando:

**Ejemplo de `wget` contra un servidor web en el puerto 8000**

```bash
tryhackme@mymachine:~# wget http://MACHINE_IP:8000/myfile
```

> **Nota:** necesitarás abrir una **nueva terminal** para ejecutar `wget` y dejar abierta la terminal donde iniciaste el servidor. Esto se debe a que el servidor de Python se mantiene en ejecución en esa terminal hasta que lo canceles.

Veamos un ejemplo de la descarga de un archivo desde nuestro servidor con `wget`:

**Descargar un archivo desde nuestro servidor con `wget`**

```bash
tryhackme@linux3:/tmp# wget http://MACHINE_IP:8000/file

2021-05-04 14:26:16  http://127.0.0.1:8000/file
Connecting to http://127.0.0.1:8000... connected.
HTTP request sent, awaiting response... 200 OK
Length: 51095 (50K) [text]
Saving to: ‘file’

file                    100%[=================================================>]  49.90K  --.-KB/s    in 0.04s

2021-05-04 14:26:16 (1.31 MB/s) - ‘file’ saved [51095/51095]
```

Recuerda que debes ejecutar `wget` en otra terminal, manteniendo activa la que ejecuta el servidor de Python.

### Limitación del módulo

Este módulo tiene un inconveniente: no ofrece ningún tipo de índice o listado, por lo que debes conocer el nombre y la ubicación exactos del archivo que quieres descargar. Por eso personalmente prefiero usar **Updog**. Es un servidor web más avanzado, pero igualmente ligero. 


## Visualizar procesos

Podemos usar el comando `ps` para obtener una lista de los procesos que se ejecutan en la sesión de nuestro usuario, junto con información adicional como su código de estado, la sesión que lo ejecuta, cuánto tiempo de CPU consume y el nombre del programa o comando que se está ejecutando.

> Fíjate en que, en la captura anterior, el segundo proceso (`ps`) tiene el PID `204` y, en el comando siguiente, este se incrementa a `205`.

Para ver los procesos de otros usuarios y los que no se ejecutan desde una sesión (es decir, los procesos del sistema), debemos añadir `aux` al comando `ps`:

```bash
ps aux
```

> Observa que ahora vemos un total de 5 procesos, y que aparecen tanto el usuario `root` como `cmnatic`.

Otro comando muy útil es `top`, que muestra estadísticas en tiempo real de los procesos que se ejecutan en tu sistema, en lugar de una vista puntual. Estas estadísticas se actualizan cada 10 segundos, y también cuando usas las flechas del teclado para desplazarte por las filas. Es una excelente forma de conocer el estado de tu sistema.

```bash
top
```

---

## Gestionar procesos

Podemos enviar señales para terminar procesos. Existen distintos tipos de señales, que determinan con qué "limpieza" trata el kernel al proceso. Para terminar un proceso usamos el comando `kill` junto con el PID correspondiente. Por ejemplo, para terminar el proceso con PID 1337, ejecutaríamos:

```bash
kill 1337
```

Estas son algunas de las señales que podemos enviar a un proceso:

| Señal     | Descripción                                                                  |
| --------- | ---------------------------------------------------------------------------- |
| `SIGTERM` | Termina el proceso, permitiéndole realizar tareas de limpieza antes de cerrar. |
| `SIGKILL` | Termina el proceso de inmediato, sin realizar ninguna limpieza posterior.    |
| `SIGSTOP` | Detiene o suspende el proceso.                                               |

---

## ¿Cómo se inician los procesos?

Empecemos hablando de los **namespaces** (espacios de nombres). El sistema operativo (SO) los utiliza para dividir los recursos disponibles del equipo (como CPU, RAM y prioridad) entre los procesos. Piensa en ello como cortar tu equipo en porciones, igual que un pastel: los procesos dentro de una porción tienen acceso a una cantidad determinada de potencia de cómputo, que es solo una pequeña parte de lo que realmente está disponible para el conjunto de procesos.

Los namespaces son excelentes para la seguridad, ya que aíslan los procesos entre sí: solo los que están en el mismo namespace pueden verse unos a otros.

Antes vimos cómo funciona el PID, y aquí es donde entra en juego. El proceso con ID 0 es el que se inicia cuando arranca el sistema. En Ubuntu, este proceso es el `init` del sistema, como **systemd**, que ofrece una forma de gestionar los procesos de un usuario y se sitúa entre el sistema operativo y el usuario.

Por ejemplo, una vez que el sistema arranca y se inicializa, `systemd` es uno de los primeros procesos en iniciarse. Cualquier programa o software que queramos ejecutar se iniciará como un **proceso hijo** de `systemd`. Esto significa que está controlado por `systemd`, pero se ejecuta como un proceso independiente (aunque comparte recursos con `systemd`), lo que facilita su identificación y gestión.

---

## Iniciar procesos y servicios durante el arranque

Algunas aplicaciones pueden iniciarse automáticamente al arrancar el sistema. Por ejemplo, servidores web, servidores de bases de datos o servidores de transferencia de archivos. Este software suele ser crítico, y los administradores suelen configurarlo para que se inicie durante el arranque.

En este ejemplo, vamos a iniciar manualmente el servidor web Apache y luego indicar al sistema que lance `apache2` en el arranque.

Para ello usamos `systemctl`, un comando que nos permite interactuar con el proceso (demonio) `systemd`. Es fácil de usar y tiene el siguiente formato:

```bash
systemctl [opción] [servicio]
```

Por ejemplo, para iniciar Apache usamos:

```bash
systemctl start apache2
```

Parece sencillo, ¿verdad? Si quisiéramos detenerlo, bastaría con reemplazar `[opción]` por `stop` en lugar de `start`.

Con `systemctl` podemos usar cinco opciones:

- `start`
- `stop`
- `enable`
- `disable`
- `status`

---

## Introducción a procesos en segundo plano y en primer plano

Los procesos pueden ejecutarse en dos estados: **en segundo plano** (*background*) y **en primer plano** (*foreground*). Por ejemplo, los comandos que ejecutas en tu terminal, como `echo`, se ejecutan en primer plano, ya que es el único comando que no se ha indicado que corra en segundo plano. `echo` es un buen ejemplo porque su salida se te devuelve en primer plano, pero no ocurriría lo mismo en segundo plano; observa la captura siguiente.

Aquí ejecutamos `echo "Hi THM"`, y esperamos que la salida se nos devuelva, como ocurre al principio. Pero al añadir el operador `&` al comando, lo único que recibimos es el ID del proceso de `echo` en lugar de la salida real, porque se está ejecutando en segundo plano.

```bash
echo "Hi THM" &
```

Esto es muy útil para comandos como la copia de archivos, ya que podemos ejecutarlos en segundo plano y seguir con otros comandos sin tener que esperar a que termine la copia.

Podemos hacer lo mismo al ejecutar scripts. En lugar de usar el operador `&`, podemos pulsar `Ctrl + Z` en el teclado para enviar un proceso a segundo plano. También es una forma eficaz de "pausar" la ejecución de un script o comando, como en el siguiente ejemplo.

Este script repetirá "This will keep on looping until I stop!" hasta que detengamos o suspendamos el proceso. Al pulsar `Ctrl + Z` (se muestra como `^Z`), nuestra terminal deja de llenarse de mensajes, hasta que lo traigamos de vuelta a primer plano, como veremos a continuación.

---

## Traer un proceso a primer plano

Ahora que tenemos un proceso en segundo plano, por ejemplo nuestro script `background.sh` (lo cual podemos confirmar con `ps aux`), podemos traerlo de vuelta al primer plano para interactuar con él.

Con el proceso en segundo plano, ya sea mediante `Ctrl + Z` o el operador `&`, usamos `fg` para devolverlo al foco, como se ve a continuación: el comando `fg` trae el proceso de vuelta a la terminal y la salida del script vuelve a mostrarse.

```bash
fg
```

## Mantenimiento del sistema: automatización

Es posible que los usuarios quieran programar una acción o tarea para que se ejecute automáticamente una vez que el sistema ha arrancado. Por ejemplo, ejecutar comandos, hacer copias de seguridad de archivos o abrir tus programas favoritos, como Spotify o Google Chrome.

Vamos a hablar del proceso **cron** y, más concretamente, de cómo interactuar con él mediante los **crontabs**. Cron es uno de los procesos que se inician durante el arranque y se encarga de facilitar y gestionar las tareas programadas (*cron jobs*).

---

## ¿Qué es un crontab?

Un crontab es simplemente un archivo especial, con un formato que el proceso cron reconoce, que se ejecuta línea por línea. Cada línea requiere 6 valores:

| Valor | Descripción                                   |
| ----- | --------------------------------------------- |
| `MIN` | En qué minuto se ejecuta                      |
| `HOUR` | En qué hora se ejecuta                       |
| `DOM` | En qué día del mes se ejecuta (*Day Of Month*) |
| `MON` | En qué mes del año se ejecuta                 |
| `DOW` | En qué día de la semana se ejecuta (*Day Of Week*) |
| `CMD` | El comando que se ejecutará                   |

---

## Ejemplo: copia de seguridad de archivos

Supongamos que quieres hacer una copia de seguridad de la carpeta `Documents` del usuario `cmnatic` cada 12 horas. Usaríamos el siguiente formato:

```bash
0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/
```

Una característica interesante de los crontabs es que admiten el **comodín** o asterisco (`*`). Si no queremos especificar un valor para un campo concreto (por ejemplo, si no nos importa el mes, el día o el día de la semana, y solo queremos que se ejecute cada 12 horas), simplemente colocamos un asterisco.

---

## Herramientas de ayuda

Al principio esto puede resultar confuso, por eso existen recursos muy útiles como el **Crontab Generator**, una aplicación online sencilla que genera el formato por ti, y el sitio **Cron Guru**.

---

## Editar tu crontab

Los crontabs se editan con el siguiente comando, que te permite elegir un editor (como Nano) para modificarlo:

```bash
crontab -e
```

## Mantenimiento del sistema: gestión de paquetes

Cuando los desarrolladores quieren ofrecer su software a la comunidad, lo publican en un repositorio de **apt**. Si es aprobado, sus programas y herramientas quedan disponibles para cualquiera. Aquí se ven dos de las mayores virtudes de Linux: la accesibilidad para el usuario y el valor de las herramientas de código abierto.

En Ubuntu, la lista de repositorios configurados se guarda en archivos que sirven como registro del software disponible. Puedes consultarlos con:

```bash
ls /etc/apt/sources.list.d/
cat /etc/apt/sources.list
```

> **Nota:** desde Ubuntu 24.04, los repositorios oficiales se definen en `/etc/apt/sources.list.d/ubuntu.sources` (formato *deb822*), y el archivo clásico `/etc/apt/sources.list` queda prácticamente vacío.

Aunque los fabricantes de sistemas operativos mantienen sus propios repositorios, también puedes añadir repositorios de la comunidad para ampliar las capacidades de tu sistema. Se pueden agregar con el comando `add-apt-repository` o indicando otro proveedor. Por ejemplo, algunos proveedores ofrecen un repositorio más cercano a tu ubicación geográfica (un *mirror*).

---

## Gestionar tus repositorios (añadir y eliminar)

Normalmente usamos el comando `apt` para instalar software en Ubuntu. Este comando forma parte del software de gestión de paquetes que también se llama **apt**, un conjunto de herramientas para administrar paquetes y fuentes de software, e instalar o eliminar programas.

Una forma de añadir repositorios es `add-apt-repository`, pero aquí vamos a hacerlo **manualmente**. Aunque se puede instalar software con instaladores como `dpkg`, la ventaja de `apt` es que, cada vez que actualizamos el sistema, también se comprueban las actualizaciones de los repositorios que hemos añadido.

En este ejemplo añadiremos el editor de texto **Sublime Text** como repositorio, ya que no forma parte de los repositorios predeterminados de Ubuntu.

Al añadir software, la integridad de lo que descargamos se garantiza mediante **claves GPG** (*GNU Privacy Guard*). Son una verificación de seguridad de los desarrolladores: si la clave no coincide con la que tu sistema considera de confianza, el software no se descargará.

> **Nota:** las instancias de TryHackMe no tienen acceso a internet, por lo que no se espera que añadas este repositorio a la máquina desplegada, ya que fallaría.

### Cambio importante: `apt-key` está obsoleto

Antes, la clave GPG se añadía con `apt-key`, que la marcaba como de confianza **para todos** los repositorios del sistema. Ese comando está **obsoleto**. El método actual consiste en guardar la clave en `/etc/apt/keyrings/` y vincularla **solo al repositorio que le corresponde** mediante la opción `Signed-By`.

### Paso 1: descargar y guardar la clave GPG

Creamos el directorio de claves (si no existe) y guardamos la clave de Sublime Text:

```bash
sudo mkdir -p /etc/apt/keyrings
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo tee /etc/apt/keyrings/sublimehq-pub.asc > /dev/null
```

> Si `wget` no está instalado, puedes instalarlo con `sudo apt install wget`.

### Paso 2: añadir el repositorio a las fuentes de apt

Una buena práctica es tener un archivo independiente para cada repositorio de terceros. Crearemos `sublime-text.sources` en `/etc/apt/sources.list.d/`, usando el canal **estable** (*stable*):

```bash
echo -e 'Types: deb\nURIs: https://download.sublimetext.com/\nSuites: apt/stable/\nSigned-By: /etc/apt/keyrings/sublimehq-pub.asc' | sudo tee /etc/apt/sources.list.d/sublime-text.sources
```

El archivo resultante tiene este contenido, que también puedes crear a mano con Nano (`sudo nano /etc/apt/sources.list.d/sublime-text.sources`):

```text
Types: deb
URIs: https://download.sublimetext.com/
Suites: apt/stable/
Signed-By: /etc/apt/keyrings/sublimehq-pub.asc
```

> **Canales disponibles:** `apt/stable/` ofrece las versiones estables y `apt/dev/` las versiones de desarrollo, que pueden ser menos estables.

### Paso 3: actualizar apt

Tras añadir la entrada, actualizamos el índice de paquetes para que apt reconozca el nuevo repositorio:

```bash
sudo apt update
```

### Paso 4: instalar el software

Una vez actualizado correctamente, instalamos el software:

```bash
sudo apt install sublime-text
```

> **Nota:** el tutorial original usaba Sublime Text 3. Actualmente el repositorio ofrece Sublime Text 4.

---

## Eliminar paquetes y repositorios

Eliminar es tan fácil como hacer el proceso inverso.

**1. Desinstalar el software:**

```bash
sudo apt remove sublime-text
```

**2. Eliminar el repositorio.** Si lo añadiste a mano, borra su archivo y la clave asociada:

```bash
sudo rm /etc/apt/sources.list.d/sublime-text.sources
sudo rm /etc/apt/keyrings/sublimehq-pub.asc
sudo apt update
```

Si lo añadiste con un PPA, usa:

```bash
sudo add-apt-repository --remove ppa:PPA_Name/ppa
```

> **Consejo:** `apt remove` conserva los archivos de configuración. Si quieres eliminarlos también, usa `sudo apt purge sublime-text`, y después `sudo apt autoremove` para quitar dependencias que ya no se necesitan.
