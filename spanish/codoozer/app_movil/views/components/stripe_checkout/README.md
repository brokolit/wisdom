# Componente STRIPE_CHECKOUT

El componente `stripe_checkout` muestra una sesión de checkout de Stripe. Stripe es una de las principales plataformas de pagos a través de Internet. Puedes usarlo dentro de tus apps creadas con Codoozer para la venta de productos físicos y/o servicios. En caso de que tu app la publiques en las appstores de Google o Apple, no puedes usar Stripe para venta de contenido digital. En esos casos, debes hacer uso de las compras in-app, usando la pasarela de pago que dichas appstores ofrecen, también compatibles con Codoozer.

Este componente te facilita la integración de Stripe en Codoozer, pues utiliza el propio backend de Codoozer para realizar las comunicaciones con el API de Stripe, con lo que no te tienes que preocupar de desarrollar tu propio backend. Para ello, es necesario que tu cuenta de Stripe esté conectada a la de Doyo y hagas uso de las referencias [@api.stripe](../../../app.json/api/stripe).

Si no quieres utilizar nuestro backend de Stripe, puedes seguir integrando pagos con Stripe a través de tu propio backend, realizando conexiones desde la app mediante la acción `request` y mostrando el checkout con un componente `web`, con lo que no necesitarás usar el componente `stripe_checkout`.

El estilo de este componente no se puede personalizar, pues lo proporciona el propio Stripe.


La siguiente tabla muestra los parámetros que puede contener este componente, además de los parámetros comunes a todos los componentes:

  | Key  | Caracter | Descripción |
  | ------------- | ------------- | ------------- |
  | billing_address_collection | Opcional | Puedes especificar que se añada al formulario de checkout una sección con los datos de facturación.|
  | email | Opcional | En caso de que tu app use autenticación y sepas el email del usuario, puedes usarlo en este componente para que ya salga prerellenado en el formulario de checkout. Puedes usar una referencia para obtener el email de forma dinámica.|
  | promotion_codes | Opcional | Si quieres que el formulario de checkout permita intruducir códigos de descuento, debes especificarlo con este parámetro.|

  
 

## Eventos

El componente `stripe_checkout` admite los siguientes eventos:

 | Evento  | Descripción |
  | ------------- | ------------- |
  | onpurchased | Se produce cuando el usuario ha completado el proceso de pago con éxito. |
  | oncancelled | Se produce cuando el usuario pulsa el botón de volver incluido dentro del checkout. |