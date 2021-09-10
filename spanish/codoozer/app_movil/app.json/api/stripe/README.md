# API - Stripe

Stripe es una de las principales y más fiables plataformas de pagos online. Esta API te permite integrar Stripe muy fácilmente en Codoozer para poder montar tu tienda online, gestionando los productos desde la propia web de Stripe.

Para utilizar esta API, es necesario que conectes tu cuenta de Stripe con la de Codoozer. El uso de este API no te consumirá DoyoCoin. En su lugar, se te cobrará una pequeña comisión del 1% de las ventas que generes a través de la app.

Una vez integrada, podrás acceder a la información de Stripe de forma muy similar a las bases de datos.

## Conectar tu cuenta de Stripe
Si no dispones de una cuenta de Stripe, puedes crear una de forma gratuita en [https://stripe.com](https://stripe.com). Stripe no te cobrará una mensualidad por el uso de la plataforma. A cambio, solo te cobrará una pequeña comisión de aproximadamente el 3% de tus ventas.

Para conectar tu cuenta, obtén el `account_id` de tu cuenta de Stripe, que encontrarás en los ajustes de tu cuenta, e introdúcelo en el archivo `app.json`, en el parámetro `stripe` que encontrarás dentro del parámetro `api`.

Una vez introducido, accede a cualquier `view` de tu proyecto en Codoozer, y en el visor verás las instrucciones para conectar tu cuenta. Pincha en el enlace correspondiente y sigue las instrucciones posteriores.

## Uso del API Stripe
Para acceder a la información de Stripe, se usa la referencia `@api.stripe`, de forma muy similar a como se usan las referencias `@database` y `@firebase`.

Dentro de la referencia `@api.stripe` se pueden encontrar algunas colecciones que solo te permitirán leer datos y otras que te permiten también escribir, como se refleja en esta tabla:


  | Key | Tipo | Descripción | Modo |
  | ------------- | ------------- | ------------- |
  | [cart](#cart) | colección | Contiene información del carrito actual | escritura / lectura |
  | checkout | Documento | Contiene la información de la sesión de checkout | lectura |
  | products | Contiene todos los productos activos dados de alta en Stripe | lectura |

## cart
Esta colección permite obtener todos los productos que han sido añadidos por el usuario al carrito, así como añadir productos o variar sus cantidades.

Cada documento del carrito, contiene los siguientes parámetros:

  | Key | Descripción |
  | ------------- | ------------- |
  | currency | La divisa del producto |
  | description | La descripción del producto |
  | image | La primera de las imágenes del producto si la hubiere|
  | name | El nombre del producto |
  | price_id | El ID del precio asociado al producto |
  | product_id | ID del producto |
  | quantity | El número de unidades de este producto en el carrito|
  | unit_amount | El precio unitario en formato stripe (sin decimales, y multiplicado por 100)|
  | unit_price | El precio unitario del producto|
  | unit_price_currency | El precio unitario del producto incluyendo la divisa|

Se trata de una colección un tanto especial, pues no se accede a sus documentos mediante un `key` único. Se pueden mostrar los documentos mediante un componente `list`, y podremos editar el carrito mediante las funciones `add` y `delete`, donde, dependiendo del `key`utilizado, se conseguirán resultados distintos.

Para añadir un producto al carrito, se usa la función `add`, con los siguientes valores en el parámetro `what`:

  | Key | Descripción | Carácter |
  | ------------- | ------------- | ------------- |
  | price_id | El ID del precio, que se puede obtener del documento del producto `@api.stripe.products.prod_K6FkJyCDXDpw55.price.id` | obligatorio |
  | quantity | La cantidad de unidades a añadir. Si no se especifica, se sumará una unidad al carrito a la cantidad que ya existiese. Si se especifica una cantidad, se sobreescribirá la cantidad existente si dicho producto ya estaba en el carrito. | opcional |

Para eliminar un producto, se usa la función `delete`, pero con la particularidad siguiente:

Si usamos un ID de producto como `key` del documento, se eliminará por completo dicho producto del carrito. Por ejemplo:
<pre>
    {
    	"function": "delete",
        "what": "@api.stripe.cart.prod_K6FkJyCDXDpw55"
    }
</pre>

Si usamos un ID del precio de un producto como `key` del documento, se eliminará una unidad del producto correspondiente. En caso de que solo hubiese una unidad de dicho producto, se borraría por completo. Por ejemplo:
<pre>
    {
    	"function": "delete",
        "what": "@api.stripe.cart.price_1JFi57Hj4Gl3FOgkPxfP5fLu"
    }
</pre>

Otra particularidad de la colección `cart` es que cuando el usuario complete el pago del carrito, se vaciará por completo la colección.


## checkout
Al intentar acceder a él, se genera una sesión de checkout en el backend que devuelve un documento, con los siguientes parámetros:

| Key | Descripción |
| ------------- | ------------- |
| url | URL de la sesión, que se puede mostrar dentro de un componente `web` o abrir en un navegador externo.|


## products
Esta colección contiene documentos que son los productos disponibles en la cuenta de stripe.
Cada documento contiene la información del objeto producto proporcionada por [Stripe](https://stripe.com/docs/api/products/object). Además, al documento se añaden estos parámetros:

| Key | Descripción |
| ------------- | ------------- |
| image | En caso de que el producto tenga fotos, se incluye la URL de la primera de ellas|
| price | Es el objeto `price` asociado a dicho producto en [Stripe](https://stripe.com/docs/api/prices/object)|
| price_amount | El precio del producto, con decimales|
| price_amount_currency | El precio del producto como cadena de texto, incluyendo la divisa|

Por ejemplo, si se quiere obtener el nombre de un producto, se usaría `@api.stripe.prod_K6FkJyCDXDpw55.name` (o `@api.stripe.(@property.selectedProduct).name)`.

En stripe, a cada producto se le puede añadir cualquier información adicional a través del parámetro `metadata`. Por ejemplo, si se dispone de una página web con información detallada de un producto, se podría almacenar dicha URL como el metadata `url`(o el nombre que sea), y desde la app obtener dicha URL a través de la referencia correspondiente. Por ejemplo `@api.stripe.prod_K6FkJyCDXDpw55.metadata.url`.