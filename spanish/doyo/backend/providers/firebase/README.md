# Firebase
Firebase ofrece un conjunto de herramientas para desarrolladores de apps y páginas web que les permite integrar un 'backend' sin necesidad de disponer de conocimientos de programación 'backend'.
<br>
<br>

**Más información:**
[https://firebase.com](https://firebase.com)
<br>
<br>


# Configuración
Para integrar Firebase, se usan los parámetros siguientes:
  
  
| Nombre | Descripción |
| ------------- | ------------- |
| Private Key | Clave privada de la cuenta de servicio de Google |
| Service Account Email | Email de la cuenta de servicio de Google |
| Project ID | ID del proyecto en Firebase |
  

Estos valores se obtienen en la configuración del proyecto en Firebase. En la pestaña 'General' se encuentra el 'project ID'.
  
Para obtener la clave privada y el email de la cuenta de servicio, hay que ir a la pestaña 'Cuentas de Servicio' y buscar el botón de 'Generar nueva clave privada'. Eso descargará un archivo JSON que contendrá tanto la clave privada como el email de la cuenta de servicio.
  


# Métodos
<br>
Los métodos ofrecidos para el proveedor Firebase se agrupan en:

<br>
<br>
  
Esta es la lista de `providers` disponibles:
<br>
  
| Nombre  | Descripción |
| ------------- | ------------- |
| [messaging](messaging) | Envío de notificaciones push. |