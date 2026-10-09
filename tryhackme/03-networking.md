![Networking](img/networking.png)

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

