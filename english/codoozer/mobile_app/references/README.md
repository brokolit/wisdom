References are like virtual boxes that can store data, so you can use it later. References can point to storage space inside the app itself (cookies, properties, local databases, UI components, etc.) or remote storage (firebase, etc.). The type of reference to use will depend on each single case.

References are very important when building apps with Codoozer. They can be used as parameters when calling functions, to indicate where some content is located, etc.

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
| app | App references give us access to some values of the app or the device, like the current location.|
| cookie | Cookies can store values permanently, so they will be available next time the user opens the app.|
| property | Properties store values only while the app is running. They are destroyed when the app finishes. |
| element | References to UI components let us get or set properties of those components. For example, if we want to change the color of a text in realtime. |
| database | Database references give us access to databases, so we can read or write data. |
| firebase | Firebase references let us use Firebase products. |
