# API - Stripe

Stripe es una de las principales y más fiables plataformas de pagos online. Esta API te permite integrar Stripe muy fácilmente en Codoozer para poder montar tu tienda online, gestionando los productos desde la propia web de Stripe.

Para utilizar esta API, es necesario que conectes tu cuenta de Stripe con la de Codoozer. El uso de este API no te consumirá DoyoCoin. En su lugar, se te cobrará una pequeña comisión del 1% de las ventas que generes a través de la app.

Una vez integrada, podrás acceder a la información de Stripe de forma muy similar a las bases de datos.

## Conectar tu cuenta de Stripe
Si no dispones de una cuenta de Stripe, puedes crear una de forma gratuita en https://stripe.com(https://stripe.com). Stripe no te cobrará una mensualidad por el uso de la plataforma. A cambio, solo te cobrará una pequeña comisión de aproximadamente el 3% de tus ventas.

Para conectar tu cuenta, obtén el `account_id` de tu cuenta de Stripe, que encontrarás en los ajustes de tu cuenta, e introdúcelo en el archivo `app.json`, en el parámetro `stripe` que encontrarás dentro del parámetro `api`.

Una vez introducido, accede a cualquier `view` de tu proyecto en Codoozer, y en el visor verás las instrucciones para conectar tu cuenta. Pincha en el enlace correspondiente y sigue las instrucciones posteriores.

## Uso del API Stripe

