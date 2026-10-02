# Windows Command Line

Solo podemos ejecutar aquellos que se encuentren dentro de las rutas definidas en el `Path` de Windows. Puedes usar el comando `set` para consultar tu `Path` desde la línea de comandos. La salida de la terminal siguiente muestra las rutas en las que MS Windows buscará y ejecutará los comandos, indicadas en la línea que empieza por `Path=`.

**Terminal**

```bash
C:\>set
ALLUSERSPROFILE=C:\ProgramData
[...]
LOGNAME=strategos
NUMBER_OF_PROCESSORS=2
OS=Windows_NT
Path=C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem;C:\Windows\System32\WindowsPowerShell\v1.0\;C:\Windows\System32\OpenSSH\;C:\Windows\system32\config\systemprofile\AppData\Local\Microsoft\WindowsApps;C:\Users\strategos\AppData\Local\Microsoft\WindowsApps;
[...]
```

## Versión del sistema operativo: `ver`

Usemos el comando `ver` para conocer la versión del sistema operativo (SO). La siguiente terminal muestra un ejemplo de salida.

**Terminal**

```bash
C:\>ver
Microsoft Windows [Version 10.0.17763.1821]
```

## Información del sistema: `systeminfo`

Podemos ejecutar el comando `systeminfo` para listar datos del sistema como la información del SO, los detalles del equipo, el procesador y la memoria. 

**Terminal**

```bash
C:\>systeminfo

Host Name:                 WIN-SRV-2019
OS Name:                   Microsoft Windows Server 2019 Datacenter
OS Version:                10.0.17763 N/A Build 17763
OS Manufacturer:           Microsoft Corporation
OS Configuration:          Standalone Server
OS Build Type:             Multiprocessor Free
[...]
```

## Un par de trucos

Antes de continuar, conviene mencionar un par de trucos.

**1. Paginar la salida con `more`.** Si la salida es demasiado larga, puedes canalizarla (*pipe*) a través de `more` para verla página a página pulsando la barra espaciadora. Para comprobarlo, prueba a ejecutar `driverquery` y compáralo con `driverquery | more`. En el segundo caso, la salida se muestra página por página y puedes salir con `CTRL + C`.

```bash
C:\>driverquery | more
```

**2. Comandos de ayuda y limpieza:**

| Comando | Descripción                                             |
| ------- | ------------------------------------------------------- |
| `help`  | Muestra información de ayuda sobre un comando concreto. |
| `cls`   | Limpia la pantalla del Símbolo del sistema.             |

## Configuración de red

Puedes consultar tu información de red con `ipconfig`. La salida de la terminal siguiente muestra nuestra dirección IP, la máscara de subred y la puerta de enlace predeterminada.

**Terminal**

```bash
C:\>ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : eu-west-1.compute.internal
   Link-local IPv6 Address . . . . . : fe80::90df:4861:ba40:f2a8%4
   IPv4 Address. . . . . . . . . . . : 10.10.230.237
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Default Gateway . . . . . . . . . : 10.10.0.1
```

También puedes usar `ipconfig /all` para obtener más información sobre tu configuración de red. Como se muestra en la siguiente terminal, podemos ver nuestros servidores DNS y confirmar que DHCP está habilitado.

**Terminal**

```bash
C:\>ipconfig /all

Ethernet adapter Ethernet 3:

   Connection-specific DNS Suffix  . : eu-west-1.compute.internal
   Description . . . . . . . . . . . : Amazon Elastic Network Adapter
   Physical Address. . . . . . . . . : 02-B7-DF-1D-0D-99
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::90df:4861:ba40:f2a8%4(Preferred) 
   IPv4 Address. . . . . . . . . . . : 10.10.230.237(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Lease Obtained. . . . . . . . . . : Wednesday, May 1, 2024 2:38:05 PM
   Lease Expires . . . . . . . . . . : Wednesday, May 1, 2024 4:08:07 PM
   Default Gateway . . . . . . . . . : 10.10.0.1
   DHCP Server . . . . . . . . . . . : 10.10.0.1
   DHCPv6 IAID . . . . . . . . . . . : 134353458
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-27-E3-D1-2B-0E-F8-30-D0-72-3F
   DNS Servers . . . . . . . . . . . : 10.0.0.2
   NetBIOS over Tcpip. . . . . . . . : Enabled
```

## `ping`

Una tarea habitual de diagnóstico es comprobar si el equipo puede acceder a un servidor concreto de Internet. La sintaxis del comando es `ping nombre_del_destino`. Inspirado en el ping-pong, enviamos un paquete ICMP específico y esperamos una respuesta. Si la recibimos, sabemos que podemos alcanzar el destino y que este puede alcanzarnos a nosotros.

Comprobemos si llegamos a `example.com`. En la salida de la terminal siguiente vemos que hemos recibido cuatro respuestas con éxito. Además, obtenemos algunas estadísticas; por ejemplo, el tiempo medio de ida y vuelta (*round trip time*) es de 78 milisegundos.

**Terminal**

```bash
C:\>ping example.com

Pinging example.com [93.184.215.14] with 32 bytes of data:
Reply from 93.184.215.14: bytes=32 time=78ms TTL=52
Reply from 93.184.215.14: bytes=32 time=78ms TTL=52
Reply from 93.184.215.14: bytes=32 time=78ms TTL=52
Reply from 93.184.215.14: bytes=32 time=78ms TTL=52

Ping statistics for 93.184.215.14:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 78ms, Maximum = 78ms, Average = 78ms
```

## `tracert`

Otra herramienta muy valiosa para el diagnóstico es `tracert` (de *trace route*, rastreo de ruta). El comando `tracert nombre_del_destino` traza la ruta de red que se recorre para llegar al destino. Sin entrar en demasiados detalles, funciona esperando que los routers del camino nos avisen cuando descartan un paquete porque su tiempo de vida (*TTL*, *time-to-live*) ha llegado a cero. La salida de la terminal siguiente muestra que hemos pasado por 15 routers antes de llegar a nuestro destino.

**Terminal**

```bash
C:\>tracert example.com

Tracing route to example.com [93.184.215.14]
over a maximum of 30 hops:

  1    59 ms    32 ms    42 ms  ec2-3-248-240-3.eu-west-1.compute.amazonaws.com [3.248.240.3]
  2     *        *        *     Request timed out.
  3     *        *        *     Request timed out.
  4     *        *        *     Request timed out.
  5     *        *        *     Request timed out.
  6     *        *        *     Request timed out.
  7     *        *        *     Request timed out.
  8     *        *        *     Request timed out.
  9    <1 ms    13 ms    <1 ms  100.100.2.56
 10    15 ms    11 ms    11 ms  ae-42.a03.londen12.uk.bb.gin.ntt.net [131.103.117.104]
 11    17 ms    11 ms    12 ms  ae-14.r20.londen12.uk.bb.gin.ntt.net [129.250.3.248]
 12    81 ms    80 ms    80 ms  ae-7.r20.nwrknj03.us.bb.gin.ntt.net [129.250.6.147]
 13    83 ms    83 ms    86 ms  ae-0.a02.nycmny17.us.bb.gin.ntt.net [129.250.3.9]
 14    79 ms    79 ms    96 ms  ce-0-3-0.a02.nycmny17.us.ce.gin.ntt.net [128.241.1.14]
 15    81 ms    86 ms    79 ms  ae-67.core1.nyd.edgecastcdn.net [152.195.68.135]
 16    78 ms    78 ms    78 ms  93.184.215.14

Trace complete.
```

## `nslookup`

Un comando de red que conviene conocer es `nslookup`. Consulta un host o dominio y devuelve su dirección IP. La sintaxis `nslookup example.com` consulta `example.com` usando el servidor de nombres predeterminado, mientras que `nslookup example.com 1.1.1.1` usa el servidor de nombres `one.one.one.one`. La terminal siguiente muestra la salida de ambos comandos. Los resultados son idénticos, pero se aprecia que las respuestas se obtuvieron de servidores de nombres distintos.

**Terminal**

```bash
C:\>nslookup example.com
Server:  ip-10-0-0-2.eu-west-1.compute.internal
Address:  10.0.0.2

Non-authoritative answer:
Name:    example.com
Addresses:  2606:2800:21f:cb07:6820:80da:af6b:8b2c
          93.184.215.14

C:>nslookup example.com 1.1.1.1
Server:  one.one.one.one
Address:  1.1.1.1

Non-authoritative answer:
Name:    example.com
Addresses:  2606:2800:21f:cb07:6820:80da:af6b:8b2c
          93.184.215.14
```

## `netstat`

Este comando muestra las conexiones de red actuales y los puertos en escucha. Un `netstat` básico, sin argumentos, muestra las conexiones establecidas, como se ve a continuación. En este caso solo tenemos una conexión SSH; sabemos que es SSH porque está vinculada al puerto 22.

**Terminal**

```bash
C:\>netstat

Active Connections

  Proto  Local Address          Foreign Address        State
  TCP    10.10.230.237:22       ip-10-11-81-126:53486  ESTABLISHED
```

Si tienes curiosidad por las demás opciones, puedes ejecutar `netstat -h`, donde `-h` muestra la página de ayuda. Nosotros hemos elegido las siguientes opciones:

| Opción | Descripción                                                                                   |
| ------ | --------------------------------------------------------------------------------------------- |
| `-a`   | Muestra todas las conexiones establecidas y los puertos en escucha.                           |
| `-b`   | Muestra el programa asociado a cada puerto en escucha y a cada conexión establecida.          |
| `-o`   | Muestra el ID de proceso (PID) asociado a la conexión.                                        |
| `-n`   | Usa la forma numérica para las direcciones y los números de puerto.                           |

Combinamos estas cuatro opciones y ejecutamos `netstat -abon`. El resultado es bastante largo, pero en la terminal siguiente mostramos las primeras líneas. Ahora queda claro que el ejecutable `sshd.exe` es el responsable de escuchar las conexiones entrantes en el puerto 22, como se ve en la primera línea. También podemos ver el ID de proceso (PID) asociado a cada conexión.

**Terminal**

```bash
C:\>netstat -abon

Active Connections

  Proto  Local Address          Foreign Address        State           PID 
  TCP    0.0.0.0:22             0.0.0.0:0              LISTENING       2116
 [sshd.exe]
  TCP    0.0.0.0:135            0.0.0.0:0              LISTENING       820
  RpcSs 
 [svchost.exe]
[...]
  TCP    0.0.0.0:49669          0.0.0.0:0              LISTENING       2036
 [spoolsv.exe]
  TCP    0.0.0.0:49670          0.0.0.0:0              LISTENING       584 
 Can not obtain ownership information
  TCP    0.0.0.0:49686          0.0.0.0:0              LISTENING       592
 [lsass.exe]
  TCP    10.10.230.237:22       10.11.81.126:53486     ESTABLISHED     2116 
 [sshd.exe]
 [...]
```

## Trabajar con directorios

Puedes usar `cd` sin parámetros para mostrar la unidad y el directorio actuales. Es el equivalente a preguntarle al sistema: ¿dónde estoy?.

Puedes ver los directorios hijos con `dir`.

**Terminal**

```bash
C:\Users\strategos>cd
C:\Users\strategos

C:\Users\strategos>dir 
 Volume in drive C has no label. 
 Volume Serial Number is A8A4-C362

 Directory of C:\Users\strategos

05/01/2024  02:40 PM    <DIR>          .
05/01/2024  02:40 PM    <DIR>          ..
11/14/2018  06:56 AM    <DIR>          Desktop
05/01/2024  02:40 PM    <DIR>          Documents
09/15/2018  07:19 AM    <DIR>          Downloads
09/15/2018  07:19 AM    <DIR>          Favorites
09/15/2018  07:19 AM    <DIR>          Links
09/15/2018  07:19 AM    <DIR>          Music
09/15/2018  07:19 AM    <DIR>          Pictures
09/15/2018  07:19 AM    <DIR>          Saved Games
09/15/2018  07:19 AM    <DIR>          Videos
               0 File(s)              0 bytes
              11 Dir(s)  14,984,953,856 bytes free
```

Ten en cuenta que puedes usar las siguientes opciones con `dir`:

| Comando   | Descripción                                                                    |
| --------- | ------------------------------------------------------------------------------ |
| `dir /a`  | Muestra también los archivos ocultos y de sistema.                             |
| `dir /s`  | Muestra los archivos del directorio actual y de todos sus subdirectorios.      |

## Representar la estructura con `tree`

Puedes escribir `tree` para representar visualmente los directorios hijos y subdirectorios.

**Terminal**

```bash
C:\Users\strategos>tree
Folder PATH listing
Volume serial number is A8A4-C362
C:.
├───Desktop
├───Documents
├───Downloads
├───Favorites
├───Links
├───Music
├───Pictures
├───Saved Games
└───Videos
```

## Cambiar de directorio con `cd`

Puedes cambiar a cualquier directorio con el comando `cd directorio_destino`; es el equivalente a hacer doble clic sobre ese directorio en el escritorio. Además, puedes usar `cd ..` para subir un nivel. En la salida de la terminal siguiente se muestra un ejemplo.

**Terminal**

```bash
C:\>cd
C:\

C:\>cd Users

C:\Users>cd 
C:\Users 

C:\Users>cd .. 

C:\>cd 
C:\ 
```

## Crear y eliminar directorios

Para crear un directorio, usa `mkdir nombre_directorio` (*make directory*). Para eliminarlo, usa `rmdir nombre_directorio` (*remove directory*). La salida de la terminal siguiente muestra cómo crear y eliminar un directorio.

**Terminal**

```bash
C:\example>mkdir backup_files

strategos@WIN-SRV-2019 C:\example>dir
 Directory of C:\example

05/02/2024  07:36 AM    <DIR>          .
05/02/2024  07:36 AM    <DIR>          ..
05/02/2024  07:36 AM    <DIR>          backup_files
               0 File(s)              0 bytes
               3 Dir(s)  14,984,724,480 bytes free

C:\example>rmdir backup_files

C:\example>dir 
 Directory of C:\example

05/02/2024  07:36 AM    <DIR>          .
05/02/2024  07:36 AM    <DIR>          ..
               0 File(s)              0 bytes
               2 Dir(s)  14,984,724,480 bytes free
```

## Ver el contenido: `type` y `more`

Estás trabajando en la línea de comandos y sientes curiosidad por el contenido de un archivo de texto. Puedes verlo fácilmente con el comando `type`, que vuelca el contenido del archivo en pantalla; es muy cómodo para archivos que caben en la ventana de la terminal.

Para archivos de texto más largos, conviene usar `more`. Este comando muestra el contenido suficiente para llenar la ventana de la terminal. Es decir, en archivos largos, `more` muestra una página y espera a que pulses la **barra espaciadora** para avanzar una página, o **Enter** para avanzar una línea.

## Copiar archivos: `copy`

El comando `copy` permite copiar archivos de una ubicación a otra. La siguiente salida de terminal muestra un ejemplo.

**Terminal**

```bash
C:\example>dir
 Directory of C:\example

05/02/2024  08:12 AM    <DIR>          .
05/02/2024  08:12 AM    <DIR>          ..
05/02/2024  07:57 AM                17 test.txt
               1 File(s)             17 bytes
               2 Dir(s)  14,983,409,664 bytes free

C:\example>copy test.txt test2.txt
        1 file(s) copied.

C:\example>dir
 Directory of C:\example

05/02/2024  08:12 AM    <DIR>          .
05/02/2024  08:12 AM    <DIR>          ..
05/02/2024  07:57 AM                17 test.txt
05/02/2024  07:57 AM                17 test2.txt
               2 File(s)             34 bytes
               2 Dir(s)  14,983,409,664 bytes free
```

## Mover archivos: `move`

De forma similar, puedes mover archivos con el comando `move`. En la salida de la terminal siguiente se muestra un ejemplo.

**Terminal**

```bash
C:\example>dir
 Directory of C:\example

05/02/2024  08:12 AM    <DIR>          .
05/02/2024  08:12 AM    <DIR>          ..
05/02/2024  07:57 AM                17 test.txt
05/02/2024  07:57 AM                17 test2.txt
               2 File(s)             34 bytes
               2 Dir(s)  14,983,409,664 bytes free

C:\example>move test2.txt .. 
        1 file(s) moved. 

C:\example>dir 
 Directory of C:\example

05/02/2024  08:13 AM    <DIR>          .
05/02/2024  08:13 AM    <DIR>          ..
05/02/2024  07:57 AM                17 test.txt
               1 File(s)             17 bytes
               2 Dir(s)  14,983,409,664 bytes free
```

## Eliminar archivos: `del` o `erase`

Por último, podemos eliminar un archivo con `del` o `erase`.

**Terminal**

```bash
C:\example>dir
 Directory of C:\example

05/02/2024  08:16 AM    <DIR>          .
05/02/2024  08:16 AM    <DIR>          ..
05/02/2024  07:57 AM                17 test.txt
05/02/2024  07:57 AM                17 test2.txt
               2 File(s)             34 bytes
               2 Dir(s)  14,983,409,664 bytes free

C:\example>erase test2.txt

C:\example>dir 
 Directory of C:\example

05/02/2024  08:16 AM    <DIR>          .
05/02/2024  08:16 AM    <DIR>          ..
05/02/2024  07:57 AM                17 test.txt
               1 File(s)             17 bytes
               2 Dir(s)  14,983,409,664 bytes free
```

## El carácter comodín `*`

Podemos usar el carácter comodín `*` para referirnos a varios archivos a la vez. Por ejemplo, el siguiente comando copiará todos los archivos con extensión `md` al directorio `C:\Markdown`:

```bash
C:\>copy *.md C:\Markdown
```

## Listar procesos: `tasklist`

Podemos listar los procesos en ejecución con `tasklist`.

**Terminal**

```bash
C:\>tasklist

Image Name                     PID Session Name        Session#    Mem Usage 
========================= ======== ================ =========== ============
System Idle Process              0 Services                   0          8 K
System                           4 Services                   0         88 K
Registry                        84 Services                   0     50,700 K
smss.exe                       276 Services                   0      1,132 K
csrss.exe                      372 Services                   0      5,264 K
wininit.exe                    448 Services                   0      6,892 K
csrss.exe                      456 Console                    1      5,028 K
winlogon.exe                   516 Console                    1     11,144 K
services.exe                   584 Services                   0      7,492 K
lsass.exe                      592 Services                   0     16,108 K
svchost.exe                    704 Services                   0     23,432 K
fontdrvhost.exe                736 Console                    1      4,256 K
[...]
```

## Filtrar la salida

Como la salida suele ser muy larga, resulta útil filtrarla. Puedes consultar todos los filtros disponibles en la página de ayuda con `tasklist /?`.

Supongamos que queremos buscar las tareas relacionadas con `sshd.exe`. Podemos hacerlo con el siguiente comando:

```bash
C:\>tasklist /FI "imagename eq sshd.exe"
```

Ten en cuenta que `/FI` sirve para establecer un filtro (*filter*), en este caso, que el nombre de la imagen sea igual a `sshd.exe`.

**Terminal**

```bash
C:\>tasklist /FI "imagename eq sshd.exe"

Image Name                     PID Session Name        Session#    Mem Usage
========================= ======== ================ =========== ============
sshd.exe                      2116 Services                   0      6,992 K
sshd.exe                      2712 Services                   0      7,668 K
sshd.exe                      4752 Services                   0      7,372 K
```

## Terminar procesos: `taskkill`

Una vez conocido el ID de proceso (PID), podemos terminar cualquier tarea con `taskkill /PID pid_destino`. Por ejemplo, si queremos terminar el proceso con PID 4567, ejecutaríamos:

```bash
C:\>taskkill /PID 4567
```
## Otro comandos:

| Comando         | Descripción                                                                                  |
| --------------- | -------------------------------------------------------------------------------------------- |
| `chkdsk`        | Comprueba el sistema de archivos y los volúmenes de disco en busca de errores y sectores defectuosos. |
| `driverquery`   | Muestra una lista de los controladores de dispositivo instalados.                            |
| `sfc /scannow`  | Analiza los archivos del sistema en busca de daños y los repara si es posible.               |
| `shutdown /r`   | Apaga el equipo y luego lo reinicia.  |
| `shutdown /a`  | Cancela un apagado o reinicio del sistema que esté pendiente.
|

Además, es igual de importante saber que `/?` se puede usar con la mayoría de los comandos para mostrar su página de ayuda.

## Dos usos de `more`

En esta sala usamos el comando `more` de dos maneras:

- **Mostrar archivos de texto:**

```bash
  C:\>more file.txt
```

- **Canalizar (*pipe*) una salida larga para verla página a página:**

```bash
  C:\>algun_comando | more
```

Con estos conocimientos, ya sabemos cómo mostrar la página de ayuda de un comando nuevo y cómo visualizar una salida larga una página cada vez.

# Windows PowerShell

PowerShell se puede iniciar de varias maneras, según tus necesidades y tu entorno. Si trabajas en un sistema Windows desde la interfaz gráfica (GUI), estas son algunas de las formas posibles:

| Método | Descripción |
| ------ | ----------- |
| **Menú Inicio** | Escribe `powershell` en la barra de búsqueda del menú Inicio y haz clic en *Windows PowerShell* o *PowerShell* en los resultados. |
| **Ejecutar** | Pulsa `Win + R` para abrir el cuadro de diálogo Ejecutar, escribe `powershell` y pulsa Enter. |
| **Explorador de archivos** | Navega a cualquier carpeta, escribe `powershell` en la barra de direcciones y pulsa Enter. Así se abre PowerShell en ese directorio concreto. |
| **Administrador de tareas** | Abre el Administrador de tareas, ve a *Archivo > Ejecutar nueva tarea*, escribe `powershell` y pulsa Enter. |

Alternativamente, PowerShell se puede iniciar desde el Símbolo del sistema (`cmd.exe`) escribiendo `powershell` y pulsando Enter.

En nuestro caso, como solo tenemos acceso al Símbolo del sistema de la máquina virtual objetivo, este es el método que usaremos.

**Terminal**

```
captain@THEBLACKPEARL C:\Users\captain>powershell
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

Install the latest PowerShell for new features and improvements! https://aka.ms/PSWindows

PS C:\Users\captain> 
```

Una vez iniciado PowerShell, se nos presenta un prompt `PS` (de *PowerShell*) en el directorio de trabajo actual.

## Sintaxis básica: Verbo-Sustantivo

Como ya se mencionó, los comandos de PowerShell se conocen como **cmdlets** (se pronuncia *command-lets*). Son mucho más potentes que los comandos tradicionales de Windows y permiten una manipulación de datos más avanzada.

Los cmdlets siguen una convención de nombres coherente: **Verbo-Sustantivo** (*Verb-Noun*). Esta estructura facilita entender qué hace cada cmdlet. El verbo describe la acción y el sustantivo especifica el objeto sobre el que se realiza. Por ejemplo:

| Cmdlet | Descripción |
| ------ | ----------- |
| `Get-Content` | Obtiene el contenido de un archivo y lo muestra en la consola. |
| `Set-Location` | Cambia el directorio de trabajo actual. |

## `Get-Command`

Para listar todos los cmdlets, funciones, alias y scripts que se pueden ejecutar en la sesión actual de PowerShell, podemos usar `Get-Command`. Es una herramienta esencial para descubrir qué comandos podemos utilizar.

**Terminal**

```
PS C:\Users\captain> Get-Command

CommandType     Name                                               Version    Source 
-----------     ----                                               -------    ------ 

Alias           Add-AppPackage                                     2.0.1.0    Appx                                                                                                                                       
Alias           Add-AppPackageVolume                               2.0.1.0    Appx                                                                                                                                       
Alias           Add-AppProvisionedPackage                          3.0        Dism                                                                                                                                       
[...]
Function        A:
Function        Add-BCDataCacheExtension                           1.0.0.0    BranchCache                                                                                                                                
Function        Add-DnsClientDohServerAddress                      1.0.0.0    DnsClient
[...]
Cmdlet          Add-AppxPackage                                    2.0.1.0    Appx
Cmdlet          Add-AppxProvisionedPackage                         3.0        Dism                                                                                                                                       
Cmdlet          Add-AppxVolume                                     2.0.1.0    Appx
[...]
```

Por cada objeto `CommandInfo` que recupera el cmdlet, se muestra en la consola cierta información esencial (propiedades). Es posible filtrar la lista de comandos según los valores de las propiedades mostradas. Por ejemplo, si queremos mostrar solo los comandos de tipo función, podemos usar `-CommandType "Function"`, como se muestra a continuación:

**Terminal**

```
PS C:\Users\captain> Get-Command -CommandType "Function"

CommandType     Name                                               Version    Source                                                                                                                                     
-----------     ----                                               -------    ------
Function        A:
Function        Add-BCDataCacheExtension                           1.0.0.0    BranchCache
Function        Add-DnsClientDohServerAddress                      1.0.0.0    DnsClient
Function        Add-DnsClientNrptRule                              1.0.0.0    DnsClient
[...]
```

**Ejemplo:** Para obtener una lista de los comandos que empiezan por el verbo Remove: Get-Command -Name Remove

## `Get-Help`

Otro cmdlet esencial para tener a mano es `Get-Help`: proporciona información detallada sobre los cmdlets, incluyendo su uso, parámetros y ejemplos. Es el recurso de referencia para aprender a usar los comandos de PowerShell.

**Terminal**

```
PS C:\Users\captain> Get-Help Get-Date

NAME
    Get-Date

SYNOPSIS
    Gets the current date and time.

SYNTAX
    Get-Date [[-Date] <System.DateTime>] [-Day <System.Int32>] [-DisplayHint {Date | Time | DateTime}] [-Format <System.String>] [-Hour <System.Int32>] [-Millisecond <System.Int32>] [-Minute <System.Int32>] [-Month <System.Int32>] [-Second <System.Int32>] [-Year <System.Int32>] [<CommonParameters>]

    Get-Date [[-Date] <System.DateTime>] [-Day <System.Int32>] [-DisplayHint {Date | Time | DateTime}] [-Hour <System.Int32>] [-Millisecond <System.Int32>] [-Minute <System.Int32>] [-Month <System.Int32>] [-Second <System.Int32>] [-UFormat <System.String>] [-Year <System.Int32>] [<CommonParameters>]

DESCRIPTION
        The `Get-Date` cmdlet gets a DateTime object that represents the current date or a date that you specify. `Get-Date` can format the date and time in several .NET and UNIX formats. You can use `Get-Date` to generate a date or time character string, and then send the string to other cmdlets or programs.
        
        `Get-Date` uses the current culture settings of the operating system to determine how the output is formatted. To view your computer's settings, use `(Get-Culture).DateTimeFormat`.

RELATED LINKS
    Online Version: https://learn.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-5.1&WT.mc_id=ps-gethelp
    ForEach-Object
    Get-Culture
    Get-Member
    New-Item
    New-TimeSpan
    Set-Date
    Set-Culture xref:International.Set-Culture

REMARKS
    To see the examples, type: "get-help Get-Date -examples".
    For more information, type: "get-help Get-Date -detailed".
    For technical information, type: "get-help Get-Date -full".
    For online help, type: "get-help Get-Date -online".
```

Como muestran los resultados anteriores, `Get-Help` nos indica que podemos obtener otra información útil sobre un cmdlet añadiendo algunas opciones a la sintaxis básica. Por ejemplo, si añadimos `-examples` al comando mostrado arriba, se nos mostrará una lista de las formas más comunes de usar ese cmdlet:

```
PS C:\Users\captain> Get-Help Get-Date -examples
```

## `Get-Alias`

Para facilitar la transición de los profesionales de TI, PowerShell incluye **alias** (atajos o nombres alternativos de los cmdlets) para muchos comandos tradicionales de Windows. Son indispensables para quienes ya conocen otras herramientas de línea de comandos, y `Get-Alias` lista todos los alias disponibles. Por ejemplo, `dir` es un alias de `Get-ChildItem` y `cd` es un alias de `Set-Location`.

**Terminal**

```
PS C:\Users\captain> Get-Alias

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           asnp -> Add-PSSnapin
Alias           cat -> Get-Content
Alias           cd -> Set-Location
Alias           CFS -> ConvertFrom-String                          3.1.0.0    Microsoft.PowerShell.Utility
Alias           chdir -> Set-Location 
Alias           clc -> Clear-Content
Alias           clear -> Clear-Host
[...]
```

## Dónde encontrar y descargar cmdlets

Otra característica potente de PowerShell es la posibilidad de ampliar su funcionalidad descargando cmdlets adicionales desde repositorios en línea.

> **Nota:** los cmdlets de esta sección requieren una conexión a internet activa para consultar los repositorios en línea. La máquina adjunta no tiene acceso a internet, por lo que estos comandos no funcionarán en este entorno.

## `Find-Module`

Para buscar **módulos** (colecciones de cmdlets) en repositorios en línea como la *PowerShell Gallery*, podemos usar `Find-Module`. A veces, si no conocemos el nombre exacto del módulo, resulta útil buscar módulos con un nombre parecido. Lo logramos filtrando la propiedad `Name` y añadiendo un comodín (`*`) al nombre parcial del módulo, con la siguiente sintaxis estándar de PowerShell:

```
Cmdlet -Propiedad "patrón*"
```

**Terminal**

```
PS C:\Users\captain> Find-Module -Name "PowerShell*"   

Version    Name                                Repository           Description 
-------    ----                                ----------           ----------- 
0.4.7      powershell-yaml                     PSGallery            Powershell module for serializing and deserializing YAML

2.2.5      PowerShellGet                       PSGallery            PowerShell module with commands for discovering, installing, updating and publishing the PowerShell artifacts like Modules, DSC Resources, Role Capabilities and Scripts.                                                   
1.0.80.0   PowerShell.Module.InvokeWinGet      PSGallery            Module to Invoke WinGet and parse the output in PSOjects

0.17.0     PowerShellForGitHub                 PSGallery            PowerShell wrapper for GitHub API  
```

## `Install-Module`

Una vez identificados, los módulos se pueden descargar e instalar desde el repositorio con `Install-Module`, lo que hace disponibles los nuevos cmdlets que contiene el módulo.

**Terminal**

```
PS C:\Users\captain> Install-Module -Name "PowerShellGet"

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```
El cmdlet tiene como alias a su equivalente tradicional `echo` es Write-Output. Puedes comprobarlo con:

```
Get-Alias -Name echo
```
Debería mostrar echo -> Write-Output.

El comando para obtener ejemplos de uso del cmdlet `New-LocalUser`: 
```
Get-Help New-LocalUser -Examples
```

## Listar contenido: `Get-ChildItem`

De forma similar al comando `dir` del Símbolo del sistema (o a `ls` en sistemas tipo Unix), `Get-ChildItem` lista los archivos y directorios de una ubicación especificada con el parámetro `-Path`. Se puede usar para explorar directorios y ver su contenido. Si no se especifica ninguna ruta, el cmdlet mostrará el contenido del directorio de trabajo actual.

**Terminal**

```
PS C:\Users\captain> Get-ChildItem 

    Directory: C:\Users\captain

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-r---          5/8/2021   9:15 AM                Desktop
d-r---          9/4/2024  10:58 AM                Documents
d-r---          5/8/2021   9:15 AM                Downloads
d-r---          5/8/2021   9:15 AM                Favorites
d-r---          5/8/2021   9:15 AM                Links
d-r---          5/8/2021   9:15 AM                Music
d-r---          5/8/2021   9:15 AM                Pictures
d-----          5/8/2021   9:15 AM                Saved Games
d-r---          5/8/2021   9:15 AM                Videos
```

**Ejemplo:** El comando para mostrar el contenido del directorio C:\Users?:
```
Get-ChildItem -Path C:\Users
```

## Contar elementos con `Measure-Object`
El comando `Get-Command -Name Remove*` mostrará varios elementos, pero para saber el número exacto puedes canalizarlo (*pipe*) a `Measure-Object`, así:
```
Get-Command -Name Remove* | Measure-Object
```

Esto te dará el recuento de cuántos elementos coinciden con ese patrón. La cifra aparece en la propiedad `Count` de la salida.

> **Nota:** el resultado depende de los módulos cargados en la máquina, por lo que conviene ejecutarlo en la VM de la sala.

## Cambiar de directorio: `Set-Location`

Para navegar a un directorio diferente, podemos usar el cmdlet `Set-Location`. Cambia el directorio actual y nos lleva a la ruta especificada, igual que el comando `cd` del Símbolo del sistema.

**Terminal**

```bash
PS C:\Users\captain> Set-Location -Path ".\Documents"
PS C:\Users\captain\Documents> 
```

## Crear elementos: `New-Item`

Mientras que la CLI tradicional de Windows usa comandos distintos para crear y gestionar diferentes elementos, como directorios y archivos, PowerShell simplifica este proceso con un único conjunto de cmdlets para crear y gestionar tanto archivos como directorios.

Para crear un elemento en PowerShell podemos usar `New-Item`. Necesitaremos especificar la ruta del elemento y su tipo (si es un archivo o un directorio).

**Terminal**

```
PS C:\Users\captain\Documents> New-Item -Path ".\captain-cabin\captain-wardrobe" -ItemType "Directory"

    Directory: C:\Users\captain\Documents\captain-cabin

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----          9/4/2024  12:20 PM                captain-wardrobe

PS C:\Users\captain\Documents> New-Item -Path ".\captain-cabin\captain-wardrobe\captain-boots.txt" -ItemType "File"     

    Directory: C:\Users\captain\Documents\captain-cabin\captain-wardrobe

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----          9/4/2024  11:46 AM              0 captain-boots.txt  
```

## Eliminar elementos: `Remove-Item`

De forma similar, el cmdlet `Remove-Item` elimina tanto directorios como archivos, mientras que en la CLI de Windows tenemos comandos separados: `rmdir` y `del`.

**Terminal**

```
PS C:\Users\captain\Documents> Remove-Item -Path ".\captain-cabin\captain-wardrobe\captain-boots.txt"
PS C:\Users\captain\Documents> Remove-Item -Path ".\captain-cabin\captain-wardrobe" 
```

## Copiar y mover elementos: `Copy-Item` y `Move-Item`

Podemos copiar o mover tanto archivos como directorios usando, respectivamente, `Copy-Item` (equivalente a `copy`) y `Move-Item` (equivalente a `move`).

**Terminal**

```
PS C:\Users\captain\Documents> Copy-Item -Path .\captain-cabin\captain-hat.txt -Destination .\captain-cabin\captain-hat2.txt
PS C:\Users\captain\Documents> Get-ChildItem -Path ".\captain-cabin\" 

    Directory: C:\Users\captain\Documents\captain-cabin

Mode                 LastWriteTime         Length Name 
----                 -------------         ------ ----
d-----          9/4/2024  12:50 PM                captain-wardrobe
-a----          9/4/2024  12:50 PM              0 captain-boots.txt
-a----          9/4/2024  12:14 PM            264 captain-hat.txt
-a----          9/4/2024  12:14 PM            264 captain-hat2.txt
-a----          9/4/2024  12:37 PM           2116 ship-flag.txt 
```

## Leer el contenido de un archivo: `Get-Content`

Por último, para leer y mostrar el contenido de un archivo podemos usar el cmdlet `Get-Content`, que funciona de forma similar al comando `type` del Símbolo del sistema (o a `cat` en sistemas tipo Unix).

**Terminal**

```
PS C:\Users\captain\Documents\captain-cabin> Get-Content -Path ".\captain-hat.txt"
 _           _   
| |         | |
| |__   __ _| |_
| '_ \ / _ | __|
| | | | (_| | |_
|_| |_|\__,_|\__|

Don't touch my hat!
```
