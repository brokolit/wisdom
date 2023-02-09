References are like virtual boxes that can store data, so you can use it later. References can point to storage space inside the app itself (cookies, properties, local databases, UI components, etc.) or remote storage (firebase, etc.). The type of reference to use will depend on each single case.

References are very important when building apps with Doyo. They can be used as parameters when calling functions, to indicate where some content is located, etc.

Thanks to references, we can add a lot of interaction between the app and the user.


## How to use references

References can be used to store some data or to get some data in order to use it.

For instance, if we want to remember that a user accessed the app before.

References can be used in different places, like:

- Parameters of functions.
- To indicate which content should a component show.
- Operators in conditions (if the user's age is less than 21 then go to a different screen).

For storing some value inside a reference, in most cases we use the function SET. That function is also used to edit the value of a reference. There are also other functions that will store/remove data in a references (add, delete, calendar, address, increase, reduce, multiply, etc.).

For using a reference, we must write the symbol **"@"** followed by the route and the name of the reference. The steps that define the route are separated by dots. The first step of the route indicates the [type of reference](reference-types)

References are represented by text strings. Here's an example of how to use a reference as the parameter of a SET function: 

<pre>
{
  "function":"set"
  "what":"@property.score",
  "value": 0
}
</pre>

We can also use the content inside a reference to construct the value of a parameter, even combining several references. In that case, we must include each reference inside parenthesis. Here we can see some examples:

<pre>
{
  "function":"set"
  "what":"@property.fullName",
  "value": "(@property.name) (@property.lastName)"
}
</pre>


<pre>
{
  "function":"set"
  "what":"@firebase.firestore.users.(@property.currentUserID).city",
  "value": "Valencia"
}
</pre>



## Reference types

There are several types of references:

| Tipo  | Descripción |
| ------------- | ------------- |
| [app](#reference-app) | App references give us access to some values of the app or the device, like the current location.|
| assets | It lets us access a resource stored in 'res/assets'.|
| [cookie](#cookies-and-properties) | Cookies can store values permanently, so they will be available next time the user opens the app.|
| database | Database references give us access to databases, so we can read or write data. |
| disk | Used to store a file in the external memory, making it accessible from outside the app. |
| element | References to UI components let us get or set properties of those components. For example, if we want to change the color of a text in realtime. |
| [property](#cookies-and-properties) | Properties store values only while the app is running. They are destroyed when the app finishes. |
| firebase | Firebase references let us use Firebase products. |
| wrapper | It allows us to set and get properties of the current wrapper. |



## Reference APP

References of type @app let us get information about the app or the device.

These are the @app references available:

| Name | Description |
| ------------- | ------------- |
| @app.admob_device_id | Returns the device ID used by Admob. This can be useful to configure our device as a test device, in order to always get fake ads. |
| @app.gaid | Returns the Google Advertising ID, which is a unique ID that has the device, although the user can reset it from the device's settings menu.|
| @app.lang | Gets the current language set in the device. |
| @app.lang.iso | Gets the current language set in the device in ISO format without the region. |
| @app.lang.iso3 | Gets the current language set in the device in ISO3 format. |
| @app.lang.region | Gets the current language set in the device in ISO format including the region. |
| @app.location | Gets the last known GPS location of the device, as "latitude,longitude". It must be used only if there's a view loaded, never in the onpreload event of the first view. |
| @app.location.latitude | Gets the latitude of the last known GP location. It must be used only if there's a view loaded. |
| @app.location.longitude | Gets the longitude of the last known GP location. It must be used only if there's a view loaded. |
| @app.time | Gets the current date and time set in the device. The format depends on the locale of the device. |
| @app.timestamp | Gets the current time as the number of miliseconds between that date and January 1st 1970. It is useful, for example, to meassure the time passed between two moments. |
| @app.version | Gets the current version of the app. |


## Cookies and properties

Both types of references let us write and read values. The difference between them is that values stored in references of type @cookie remain stored after the app closes, so they are available next time the user opens the app, while values store in references of type @property are deleted when the user closes the app.

The developer of the app decides the name of each reference, but that name can only contain letters, numbers or the underscore symbol. Avoid using spaces, or special characters.

<pre>
@property.username
</pre>

<pre>
@cookie.username
</pre>

When reading the value store in a @cookie or a @property, it is possible to add modifiers after the name, using dots to separate modifiers. Modifiers will alter the value returned by the reference, while the reference will keep the original value. It is possible to make a chain of modifiers, so each modifier will alter the value altered by the previous modifier. For instance: if we want to get the value stored in the cookie `price`, divide it by 2 and add 5, we would use:

<pre>
@cookie.price./2.+5
</pre>

The next table lists all the possible modifiers for text values:

| Modificador  | Descripción |
| ------------- | ------------- |
| number | Returns the character in the position N. |
| start-end | Returns the subtext between positions `start` and `end`. Both values must be positive integers. If the `end` value is higher than the text's length, the returned subtext will end in the last position of the text. |
| json | If the stored text is a JSON string, the next modifiers won't act as modifiers, but as the route to the value we want to obtain from the JSON string.|
| length | Returns the number of characters that the text has. |
| lower | Converts all characters into lower case. |
| md5 | Converts the text into a md5 hash. |
| trim | Get rid of all the spaces at the beginning or the end of the text, if there's any. |
| upper | Converts all characters into upper case. |
| urldecode | Decodes a text that was encoded using urlencoding. |
| urlencode | Encodes the text using urlencoding, so you can safely use it as a parameter of a URL. |


The next table lists all the possible modifiers for numeric values:

| Modificador  | Descripción |
| ------------- | ------------- |
| text | Converts a number into text format. It can be useful, for example, to store big numbers (like phone numbers) avoiding scientific format (1e12). |
| +N | Increases the previous value by N. |
| -N | Subtracts N from the previous number. |
| *N | Multiplies the previous value by N. |
| /N | Divides the previous value by N. |
| %N | Returns the reminder of dividing the previous value by N. |
| N% | Returns the percentaje N of the previous value. |
| ^N | Returns the previous value to the power of N.  |
| dN | Rounds the previous value using N decimal places. |
| abs | Returns the absolute value of the previous value. |
| acos | Returns the arccosine in degress of the previous value. |
| asin | Returns the arcsine in degress of the previous value. |
| atan | Returns the arctangent in degress of the previous value. |
| cos | Returns the cosine of the previous value (in degrees). |
| sin | Returns the sine of the previous value (in degrees). |
| tan | Returns the tangent of the previous value (in degrees). |
| sqrt | Returns the square root of the previous value. |

For those modifiers that specify an N value and incase the N value has decimal places, the N value must be wrapped using parenthesis, in order to avoid the dot to be considered as the end of the modifier. For example:

<pre>
@cookie.price.*(1.21)
</pre>

