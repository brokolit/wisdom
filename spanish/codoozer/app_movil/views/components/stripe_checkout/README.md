# Componente STRIPE_CHECKOUT

El componente `stripe_checkout` muestra una sesión de checkout de Stripe. Stripe es una de las principales plataformas de pagos a través de Internet. Puedes usarlo dentro de tus apps creadas con Codoozer para la venta de productos físicos y/o servicios. En caso de que tu app la publiques en las appstores de Google o Apple, no puedes usar Stripe para venta de contenido digital. En esos casos, debes hacer uso de las compras in-app, usando la pasarela de pago que dichas appstores ofrecen, también compatibles con Codoozer.

Este componente te facilita la integración de Stripe en Codoozer, pues utiliza el propio backend de Codoozer para realizar las comunicaciones con el API de Stripe, con lo que no te tienes que preocupar de desarrollar tu propio backend. Para ello, es necesario que tu cuenta de Stripe esté conectada a la de Doyo.

Si no quieres utilizar nuestro backend de Stripe, puedes seguir integrando pagos con Stripe a través de tu propio backend, realizando conexiones desde la app mediante la acción `request` y mostrando el checkout con un componente `web`, con lo que no necesitarás usar el componente `stripe_checkout`.


La siguiente tabla muestra los parámetros que puede contener este componente, además de los parámetros comunes a todos los componentes:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | billing_address_collection | Opcional | Puedes especificar que se añada al formulario de checkout una sección con los datos de facturación.|
  | email | Opcional | En caso de que tu app use autenticación y sepas el email del usuario, puedes usarlo en este componente para que ya salga prerellenado en el formulario de checkout. Puedes usar una referencia para obtener el email de forma dinámica.|
  | promotion_codes | Opcional | Si quieres que el formulario de checkout permita intruducir códigos de descuento, debes especificarlo con este parámetro.|

  
 

## Eventos

El componente `image` admite los siguientes eventos:

 | Evento  | Descripción |
  | ------------- | ------------- |
  | onpurchased | Se produce cuando el usuario ha completado el proceso de pago con éxito. |
  | oncancelled | Se produce cuando el usuario pulsa el botón de volver incluido dentro del checkout. |


 
## Configuración de Stripe API

El componente `scanner` permite acceder a ciertas propiedades a través de referencias, usando el siguiente formato:

```
@element.id_del_componente.propiedad
```

Las propiedades de escritura se podrán establecer como parámetro `what` de una función `set`.
Las propiedades de lectura se podrán usar como valor en aquellas funciones que acepten valores en forma de referencias.


 | Propiedad | Modo | Descripción |
  | ------------- | ------------- | ------------- |
  | alpha | Escritura | Opacidad del componente, un valor entre 0 (0%) y 1 (100%) |
  | code | Lectura | Contiene el último código detectado |
  | content | Lectura | Contiene el contenido completo que ofrece el último código detectado |
  | backgroundColor | Escritura | Color de fondo del componente. Acepta un color de la tabla de colores (@color.primary) o un valor hexadecimal en formato #AARRGGBB o #RRGGBB |
  | format | Lectura | Indica el formato del último código detectado |
  | type | Lectura | Indica el tipo de contenido al que se refiere el último código detectado, pudiendo ser: `UNKNOWN`, `CONTACT_INFO`, `EMAIL`, `ISBN`, `PHONE`, `PRODUCT`, `SMS`, `TEXT`, `URL`, `WIFI`, `GEO`, `CALENDAR_EVENT` o `DRIVER_LICENSE`. |
  | visible | Escritura/lectura | Indica si el componente es visible (`true`) o no (`false`) |
