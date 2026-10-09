![Networking](img/networkingconcepts.png)

# Modelo OSI

El modelo **OSI** (*Open Systems Interconnection*, Interconexión de Sistemas Abiertos) es un modelo conceptual desarrollado por la Organización Internacional de Normalización (**ISO**) que describe cómo deben producirse las comunicaciones en una red informática. Dicho de otro modo, el modelo OSI define un marco de trabajo para las comunicaciones en redes de computadoras.

Aunque este modelo es teórico, es fundamental aprenderlo y comprenderlo, ya que ayuda a entender los conceptos de redes en mayor profundidad. El modelo OSI se compone de **siete capas**:

| Capa | Descripción |
| ---- | ----------- |
| **Capa física** | Se ocupa de la transmisión por hardware (cables, switches). |
| **Capa de enlace de datos** | Garantiza una transferencia de datos sin errores entre dos nodos de la misma red. |
| **Capa de red** | Se encarga de enrutar los paquetes entre distintas redes (direcciones IP). |
| **Capa de transporte** | Ofrece transferencia de datos fiable o no fiable (TCP/UDP). |
| **Capa de sesión** | Gestiona las sesiones entre aplicaciones. |
| **Capa de presentación** | Da formato a los datos para la capa de aplicación (cifrado, compresión). |
| **Capa de aplicación** | Interactúa directamente con las aplicaciones del usuario (HTTP, FTP). |

### Responde a las siguientes preguntas

### Pregunta 1

**¿Qué capa es responsable de conectar una aplicación con otra?**

**Respuesta:** `Layer 4` 

### Pregunta 2

**¿Qué capa es responsable de enrutar los paquetes a la red adecuada?**

**Respuesta:** `Layer 3`

### Pregunta 3

**En el modelo OSI, ¿qué capa es responsable de codificar los datos de la aplicación?**

**Respuesta:** `Layer 6` 

### Pregunta 4

**¿Qué capa es responsable de transferir datos entre hosts del mismo segmento de red?**

**Respuesta:** `Layer 2`

### Resumen

| N.º de capa | Nombre de la capa | Función principal | Ejemplos de protocolos y estándares |
| ----------- | ----------------- | ----------------- | ----------------------------------- |
| **Capa 7** | Capa de aplicación | Proporcionar servicios e interfaces a las aplicaciones. | HTTP, FTP, DNS, POP3, SMTP, IMAP |
| **Capa 6** | Capa de presentación | Codificación, cifrado y compresión de datos. | Unicode, MIME, JPEG, PNG, MPEG |
| **Capa 5** | Capa de sesión | Establecer, mantener y sincronizar sesiones. | NFS, RPC |
| **Capa 4** | Capa de transporte | Comunicación de extremo a extremo y segmentación de datos. | UDP, TCP |
| **Capa 3** | Capa de red | Direccionamiento lógico y enrutamiento entre redes. | IP, ICMP, IPSec |
| **Capa 2** | Capa de enlace de datos | Transferencia fiable de datos entre nodos adyacentes. | Ethernet (802.3), WiFi (802.11) |
| **Capa 1** | Capa física | Medios físicos de transmisión de datos. | Señales eléctricas, ópticas e inalámbricas |

## Modelo TCP/IP

TCP/IP significa *Transmission Control Protocol/Internet Protocol* (Protocolo de Control de Transmisión/Protocolo de Internet) y fue desarrollado en la década de 1970 por el Departamento de Defensa de EE. UU. (**DoD**).

## Las capas del modelo TCP/IP

Al presentar el modelo ISO OSI fuimos de abajo arriba, de la capa 1 a la capa 7. En esta tarea veremos las cosas desde otra perspectiva: **de arriba abajo**. 

| Capa | Descripción |
| ---- | ----------- |
| **Capa de aplicación** | Las capas de aplicación, presentación y sesión del modelo OSI (capas 5, 6 y 7) se agrupan en la capa de aplicación del modelo TCP/IP. |
| **Capa de transporte** | Es la capa 4. |
| **Capa de Internet** | Es la capa 3. La capa de red del modelo OSI se llama capa de Internet en el modelo TCP/IP. |
| **Capa de enlace** | Es la capa 2. |

## Correspondencia entre OSI y TCP/IP

La siguiente tabla muestra cómo se corresponden las capas del modelo TCP/IP con las del modelo ISO/OSI.

| N.º de capa | Modelo ISO OSI | Modelo TCP/IP (RFC 1122) | Protocolos |
| ----------- | -------------- | ------------------------ | ---------- |
| **7** | Capa de aplicación | Capa de aplicación | HTTP, HTTPS, FTP, POP3, SMTP, IMAP, Telnet, SSH |
| **6** | Capa de presentación | *(incluida en la capa de aplicación)* | |
| **5** | Capa de sesión | *(incluida en la capa de aplicación)* | |
| **4** | Capa de transporte | Capa de transporte | TCP, UDP |
| **3** | Capa de red | Capa de Internet | IP, ICMP, IPSec |
| **2** | Capa de enlace de datos | Capa de enlace | Ethernet 802.3, WiFi 802.11 |
| **1** | Capa física | *(incluida en la capa de enlace)* | |

## TCP/IP en cinco capas

Muchos libros modernos de redes presentan el modelo TCP/IP con **cinco capas** en lugar de cuatro. Por ejemplo, en *Computer Networking: A Top-Down Approach* (8.ª edición), Kurose y Ross describen la siguiente pila de protocolos de Internet de cinco capas, que incluye la capa física:

1. **Aplicación** (*Application*)
2. **Transporte** (*Transport*)
3. **Red** (*Network*)
4. **Enlace** (*Link*)
5. **Física** (*Physical*)

## Direcciones IP y subredes

Cada host de la red necesita un identificador único para que otros hosts puedan comunicarse con él. Sin un identificador único, no se puede encontrar al host sin ambigüedad. Al usar el conjunto de protocolos TCP/IP, necesitamos asignar una dirección IP a cada dispositivo conectado a la red.

## ¿Cómo está formada una dirección IP?

Una dirección IP se compone de **cuatro octetos**, es decir, **32 bits**. Al ser de 8 bits, un octeto permite representar un número decimal entre 0 y 255.

*Una dirección IP está formada por 4 octetos o bytes, y cada octeto representa un número decimal entre 0 y 255.*

A riesgo de simplificar demasiado, el `0` y el `255` están reservados para las direcciones de **red** y de **difusión** (*broadcast*), respectivamente. Es decir, `192.168.1.0` es la dirección de red, mientras que `192.168.1.255` es la dirección de difusión. Enviar datos a la dirección de difusión los dirige a todos los hosts de la red.

Con un cálculo sencillo, puedes concluir que no puede haber más de 4000 millones de direcciones IPv4 únicas, son aproximadamente 2<sup>32</sup>, porque tenemos 32 bits. Es una cifra aproximada porque no hemos tenido en cuenta las direcciones de red y de difusión.
## Consultar tu configuración de red

Puedes consultar tu dirección IP en la línea de comandos de MS Windows con el comando `ipconfig`. En Linux y en sistemas basados en UNIX, puedes usar `ifconfig` o `ip address show`, que se puede escribir como `ip a s`. 

**Terminal**

```
user@TryHackMe$ ifconfig
[...]
wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.66.89  netmask 255.255.255.0  broadcast 192.168.66.255
        inet6 fe80::73e1:ca5e:3f93:b1b3  prefixlen 64  scopeid 0x20<link>
        ether cc:5e:f8:02:21:a7  txqueuelen 1000  (Ethernet)
        RX packets 19684680  bytes 18865072842 (17.5 GiB)
        RX errors 0  dropped 364  overruns 0  frame 0
        TX packets 14439678  bytes 8773200951 (8.1 GiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

La salida anterior indica lo siguiente:

- La dirección IP del host (portátil) es `192.168.66.89`.
- La máscara de subred es `255.255.255.0`.
- La dirección de difusión es `192.168.66.255`.

Usemos ahora `ip a s` para comparar cómo se presenta la dirección IP de la tarjeta de red.

**Terminal**

```
user@TryHackMe$ ip a s
[...]
4: wlo1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether cc:5e:f8:02:21:a7 brd ff:ff:ff:ff:ff:ff
    altname wlp3s0
    inet 192.168.66.89/24 brd 192.168.66.255 scope global dynamic noprefixroute wlo1
       valid_lft 36795sec preferred_lft 36795sec
    inet6 fe80::73e1:ca5e:3f93:b1b3/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```

La salida anterior indica lo siguiente:

- La dirección IP del host (portátil) es `192.168.66.89/24`.
- La dirección de difusión es `192.168.66.255`.

## Máscara de subred y notación `/24`

Si te lo estás preguntando, una máscara de subred `255.255.255.0` también se puede escribir como `/24`. El `/24` significa que los 24 bits más a la izquierda de la dirección IP no cambian en toda la red, es decir, en la subred. Dicho de otro modo, los tres octetos de la izquierda son iguales en toda la subred; por lo tanto, podemos esperar direcciones que van desde `192.168.66.1` hasta `192.168.66.254`. Como se mencionó antes, `192.168.66.0` y `192.168.66.255` son las direcciones de red y de difusión, respectivamente.

## Direcciones privadas

Ya que estamos explicando las direcciones IP, conviene mencionar que, para la mayoría de los fines prácticos, hay dos tipos de direcciones IP:

- Direcciones IP **públicas**.
- Direcciones IP **privadas**.

La **RFC 1918** define los siguientes tres rangos de direcciones IP privadas:

| Rango | Notación CIDR |
| ----- | ------------- |
| `10.0.0.0` – `10.255.255.255` | `10/8` |
| `172.16.0.0` – `172.31.255.255` | `172.16/12` |
| `192.168.0.0` – `192.168.255.255` | `192.168/16` |

Antes presentamos una analogía que decía que una dirección IP pública es como tu dirección postal. Una dirección IP privada es diferente: la idea original es que no puede llegar al mundo exterior ni ser alcanzada desde él. Es como una ciudad aislada o un complejo residencial, donde todas las casas y apartamentos están numerados de forma sistemática y pueden intercambiar correo fácilmente entre sí, pero no con el mundo exterior.

Para que una dirección IP privada pueda acceder a internet, el router debe tener una dirección IP pública y admitir la **traducción de direcciones de red** (*Network Address Translation*, **NAT**). 

## Enrutamiento

Un router reenvía los paquetes de datos a la red adecuada. Normalmente, un paquete de datos pasa por varios routers antes de llegar a su destino final. El router funciona en la **capa 3**: inspecciona la dirección IP y reenvía el paquete a la mejor red (router), de modo que el paquete se acerque a su destino.

## Ejercicio: 

**¿Cuál de las siguientes direcciones IP no es una dirección IP privada?**

- `192.168.250.125`
- `10.20.141.132` 
- `49.69.147.197` 
- `172.23.182.251` 

**Respuesta:** `49.69.147.197` 

### Explicación 

Según la RFC 1918, los rangos de direcciones privadas son: 

| Dirección | ¿Privada? | Motivo | | --------- | --------- | ------ | 
| `192.168.250.125` | Sí | Está en `192.168.0.0/16`. | 
| `10.20.141.132` | Sí | Está en `10.0.0.0/8`. | 
| `49.69.147.197` | **No** | No está en ningún rango privado, es **pública**. | 
| `172.23.182.251` | Sí | Está en `172.16.0.0/12` (de `172.16.0.0` a `172.31.255.255`). |

**¿Cuál de las siguientes direcciones IP no es una dirección IP válida?**

- `192.168.250.15`
- `192.168.254.17`
- `192.168.305.19`
- `192.168.199.13`

**Respuesta:** `192.168.305.19`

### Explicación

Una dirección IPv4 se compone de cuatro octetos, y cada uno debe estar entre `0` y `255`.

