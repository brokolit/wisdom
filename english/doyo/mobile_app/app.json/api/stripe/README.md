# API - Stripe

Stripe is one of the main and most trustable platforms for online payments processing. This API allows you to integrate Stripe with Doyo as easy as pie, so that you can build your own mobile shop and manage your products from the Stripe's dashboard.

In order to use this API, you'll need to connect your Stripe account to the one from Doyo. Using this API won't consume your DoyoCoin. Instead, you'll be charge a small transaction fee of 1% on every transaction made from the app.

Once integrated, you'll be able to access Stripe's information in a very similar way as you access database.

## Connecting your Stripe account
If you don't have a Stripe account, you can register for free at [https://stripe.com](https://stripe.com). Stripe won't charge you a monthly fee. Instead they will charge you a small transaction fee of 3% on every transaction.

For connecting your account to Doyo, you must get the `account_id` from your Stripe account. You'll find that ID in your account settings. Once you have that ID, you must store it in `app > api > stripe`.

After adding your account id, open any `view` of your project and you'll find the instructions in the preview area to connect your account. Click on the link and follow the instructions.S

## Using the Stripe API
For accessing the information on Stripe, use the reference  `@api.stripe`. It works very similarly to other references like `@database` and `@firebase`.

Inside the reference `@api.stripe` you'll find some collections that will let you read information and some others that will let you write too, as you can see in this table:


  | Key | Type | Description | Mode |
  | ------------- | ------------- | ------------- | ------------- |
  | [cart](#cart) | collection | Contains information about the current cart | write / read |
  | [checkout](#checkout) | document | Contains information about the checkout session | read |
  | [products](#products) | collection | Contains all the active products from Stripe | read |

## cart
This collection lets you access all the products that have been added by the user to the cart, as well as add new products or edit the existing ones.

Each document in the cart collection contains these parameters:

  | Key | Description |
  | ------------- | ------------- |
  | currency | The currency of the product|
  | description | The product's description |
  | image | The first image's URL in case there's any|
  | name | The product's name |
  | price_id | The ID of the price related to the product |
  | product_id | The ID of the product |
  | quantity | The number of units of this product that has been added to the cart|
  | unit_amount | The unit price in Stripe format (without decimal positions and multiplied by 100)|
  | unit_price | The unit price of the product|
  | unit_price_currency | The unit price of the product including the currency symbol|

The cart collection has some special features. You can access the documents using a unique `key`. You can list all the items in the cart with a `list` component though. You can also edit the items in the cart by using the functions `add` and `delete`, where, depending on the type of `key`used, they will perform differently.

To add a product into the cart, you must use the function `add`, with these values in the `what` parameter:

  | Key | Description | Nature |
  | ------------- | ------------- | ------------- |
  | price_id | The ID of the product's price, which can be found at @api.stripe.products.productID.price.id` | mandatory |
  | quantity | The number of units to add. If not defined, 1 unit will be added to the amount that already exists in the cart. If a quantity is defined, it will overwrite the existing amount of that product in the cart. | optional |

In order to delete an item from the cart, or reduce its quantity, you must use the function `delete`, with some special features:

If the ID of a product is used as the document's key, the whole product will be removed from the cart. For instance:

<pre>
    {
    	"function": "delete",
        "what": "@api.stripe.cart.prod_K6FkJyCDXDpw55"
    }
</pre>

If the ID of a product's price is used as the document's key, only 1 unit of the corresponding product will be removed from the cart. If there was only 1 unit added to the cart, the whole product will be removed. For instance:

<pre>
    {
    	"function": "delete",
        "what": "@api.stripe.cart.price_1JFi57Hj4Gl3FOgkPxfP5fLu"
    }
</pre>

Another special feature of the collection `cart` is that the whole collection will be cleared in case the user pays succesfully.


## checkout
When accessing the `chechout` document, a new checkout session will be created on the server side and a checkout document will be returned with these parameters:

| Key | Description |
| ------------- | ------------- |
| url | Session URL, that you can load into a `web` component or use the function `browser` to open the checkout page outside the app.|


## products
This collection has all the products that are active on the Stripe account.

Each document containns the product object provided by [Stripe](https://stripe.com/docs/api/products/object). Some extra parameters will be added by Doyo's API:

| Key | Description |
| ------------- | ------------- |
| image | In case the product has some images, the URL of the first image will be available in this parameter|
| price | It is the object `price` related to the product on [Stripe](https://stripe.com/docs/api/prices/object)|
| price_amount | The real price of the product, with decimal positions|
| price_amount_currency | The price of the product in text format, including the currency|

For instance, for getting the name of a product, you should use `@api.stripe.prod_K6FkJyCDXDpw55.name` (or `@api.stripe.(@property.selectedProduct).name)`.

You can add some extra information for each product on Stripe, using the `metadata` parameters. For instance, if you have a web page for each product with specs, you could store the URL of that web page as the parameter `url` inside the metadata. You'll be able to access that URL from the app using `@api.stripe.prod_K6FkJyCDXDpw55.metadata.url`.