# app.json

It is the main JSON file, which contains the definition of the project's global setup, and also the instructions to generate the app's executable file.

App.json is the only file that must be place on the project's root folder.

This next table shows the parameters that can have:

  | Key  | Nature | Description |
  | ------------- | ------------- | ------------- |
  | id | Mandatory | Unique identifier assigned to the project by Codoozer |
  | project_name | Mandatory | Alias of the project, assined by the developer |
  | name | Mandatory | Name of the app, the one that will be displayed when installing the app in a device. Accetps [multilanguage](../../multilanguage) |
  | [android](#android-configuration) | Optional | Contains some settings that are needed to generate the version of the app compatible with Android devices. Therefore, this parameter is only needed in case we want to develop an Android app |
  | [api](#api) | Optional | Contains some settings for using Codoozer's API, which act as a bridge to other 3rd party APIs|
  | [ios](#ios-configuration) | Optional | Contains some settings that are needed to generate the version of the app compatible with iOS devices (Apple). Therefore, this parameter is only needed in case we want to develop an iOS app |
  | [events](#app-events) | Mandatory | Defines how the app should react to some events. It must at least define the event `onstart`, which defines what the app should do right after it is opened. For instance, the function `goto` loading a view |
  | [monetization](#monetization) | Optional | Contains the configuration needed for monetizing the app |
  | [purchases](#compras-inapp) | Optional | Contains the configuration needed to use in-app purchases |
  | [colors](#colores) | Optional | Contains a table of colors that can be referenced from some parts of the project |
  | [databases](#bases-de-datos) | Optional | Contains the list of databases that the app will use |
  | [fonts](#tipografías-fonts) | Optional | Contains a list of TrueType fonts (TTF) that will be used in the project |



If you want to see a sample of an app.json file, [click here](app.json)




## Android configuration
The `android` parameter contains some values needed to generate the Android version of the app.

  | Key  | Nature | Description |
  | ------------- | ------------- | ------------- |
  | package_name | Mandatory | Name of the android package name, which is a worldwide unique identifier of an android app. The app can't be published on the app stores if they already have another app with the same package name. It is a sequence of words, without spaces nor special characters, joined by dots. |
  | version | Mandatory | The version number that we want our app to have. It must be an integer value and we should increase it every time we want to submit an update of our app to GooglePlay.|
  | version_name | Optional | It is a text showing the version number as we want our users to see it. It normally contains thress numbers concatenated by dots, indicating the version and subversion number. It we don't define the `version_name`, Codoozer will take the value of `version` and will add two zeros (1.0.0) |
  | certificate | Optional | It is a JSON object that contains information about the certificate to use for signing the app. |
  | maps_api_key | Optional | If we want to use Google Maps in our app, we need to obtain an API key from Google. Use this [link](https://developers.google.com/maps/documentation/android-sdk/get-api-key) to get more information about how to obtain the GoogleMaps API key.|
  | firebase | Optional | It must be added in case we need to use any Firebase services in our project: authentication, databases, push notifications, storage, etc. This parameter contains a JSON object that will define the settings of those Firebase products we want to use.|
  

This table shows the parameters that accepts the parameter `certificate`. If we don't add a certificate, Codoozer will generate one for us.

  | Key  | Description |
  | ------------- | ------------- |
  | file | Name of the `keystore` file inside the `certificates` folder. |
  | store_password | Password of the key storage. |
  | key_alias | The alias of the key inside the key storage that you want to use to sign the app. |
  | key_password | The password of the key associated with the entered alias.|

The next table shows the parameters accepted by the parameter `firebase`.

  | Key  | Descripción |
  | ------------- | ------------- |
  | analytics | Must be added and have `true` as value for using Firebase Analytics. |
  | authentication | Must be added and have `true` as value for using Firebase Authentication. |
  | firestore | Must be added and have `true` as value for using Firebase Firestore databases. |
  | inapp-messaging | Must be added and configured for using Firebase Firestore In-app Messaging. |
  | messaging | Must be added and configured for using Firebase Cloud Messaging (Push). |
  | storage | Must be added and have `true` as value for using Firebase Storage. |
  



## iOS configuration

Information not yet available.

## API
Codoozer offers a set of APIs that will make things much easier for you to connect with some 3rd party products:

| Key  | Descripción |
| ------------- | ------------- |
| [stripe](api/stripe) | One of the most popular online payments processing platforms.|

## App events
The `events` parameter contains a JSON object that includes a list of events to which we want to define how the app should react.

Currently we can only define the `onstart` parameter, that will define the behavior of the app right after it is opened. It normally includes a `goto` function to let the app know what view should be loaded at first. It also can contain some other functions to initialize properties, cookies, etc.

Here you can see an example:

<pre>
    "events":{
        "onstart": {"function":"goto","view":"main"}
    },
</pre>

In the future, other events will be accepted (`onexit`, `onpush`, etc.)


## Monetization
The `monetization` parameter includes the setting for monetizing the app. It contains a JSON object, which is explained in the next table:


  | Key  ||||
  | ------------- | ------------- | ------------- | ------------- |
  | android | ads | networks | An array of JSON objects, each one defining the settings of some ad network. |
  | android | ads | placements | An array of JSON objects that contain configurations for the different ad placements |

### AD networks:

Each JSON object inside the array contained in the `networks` parameter follows this structure:

  | Key  | Nature | Value |
  | ------------- | ------------- | ------------- |
  | admob | Optional | Used to include Google Admob in our project | 

The value of the `admob` parameter is a JSON object with the following structure:

  | Key  | Value |
  | ------------- | ------------- |
  | android_app_id | ID assigned by Admob for our app | 
  | android_test_devices | It's a text containing the test token of the device we want to use for testing or an array of texts in case we want to add more than one test devices. |
  
  
### Placements:

Each `placement` object contains the config information of the different places where we want to use ads. It can have these values:

  | Key  | Value |
  | ------------- | ------------- |
  | id | Placement ID that will be used whenever we want to use this ad configuration. | 
  | network  | Ad network used in this placement. |
  | format  | Type of ad. It can be `banner`, `interstitial` o `rewarded`. |
  | android_unit_id  | The ID provided by Admob for this placement in the Android version. |
  | ios_unit_id  | The ID provided by Admob for this placement in the iOS version. |

Here's an example:
<pre>
    "monetization":{
        "ads":{
            "networks":{
                "admob":{
                    "android_app_id":"ca-app-pub-3940256099942544~3xxxxxxxx",
                    "android_test_devices": "26F2006560892_1D83871216xxxxxxxx"
                }
            },
            "placements":{
                "banner_menu":{
                    "network":"admob",
                    "format":"banner",
                    "android_unit_id":"ca-app-pub-4520545808487978/58xxxxxxxx"
                },
                "after_result":{
                    "network":"admob",
                    "format":"interstitial",
                    "android_unit_id":"ca-app-pub-4520545808487978/12xxxxxxxx"
                },
                "earn_questions":{
                    "network":"admob",
                    "format":"rewarded",
                    "android_unit_id":"ca-app-pub-4520545808487978/10xxxxxxxx"
                }
            }
        }
        
    }
</pre>


## In-app purchases
The `purchases` parameter defines the configuration for using in-app purchases. This table shows the structure of the JSON object:


  | Key  | Nature | Description |
  | ------------- | ------------- | ------------- |
  | googleplay | Opcional | JSON object that contains the setting for using in-app purchases through GooglePlay|


### Purchases via GooglePlay
The `googleplay` parameter inside `purchases` has this structure:

  | Key  | Description |
  | ------------- | ------------- |
  | products | A JSON array containing the list of virtual products that we want to sell inside the app |
  
  
Each product must have the next JSON structure:

  | Key  | Description |
  | ------------- | ------------- |
  | id | Product's identifier. Must be identical to the ID that we set up on the GooglePlay developer console |
  | type | Indicates the type of product. Currently Codoozer only support the type `eternal`, used for those products that can only be purchased once and last forever. |


  
## Colors
The `colors` parameter is a JSON object that contains a list of key-value pairs, each one defining a color. The key will be used as the color's identifier. We will use that key as a reference to use that color in other parts of the app. The value is the color code, represented with a # symbol followed by the hexadecimal value with either the RRGGBB or AARRGGBB format.

Here's an example:
<pre>
    "colors":{
        "colorPrimary":"#00c2a9",
        "colorPrimaryDark": "#00a58c",
        "colorPrimaryLight": "#b7f0e7",
        "colorAccent": "#f15a9e",
        "colorSecondary": "#ffde39",
        "colorSecondaryDark": "#fec632",
        "colorSecondaryLight": "#fbe98d",
        "blue": "#0cafe8",
        "headlines": "#d7d4e3",
        "grey":"#999999",
        "titles": "#01579b",
        "fbutton": "#01579b",
        "white": "#ffffff",
        "black": "#000000"
    }
</pre>


## Bases de datos
The `databases` parameter contains an array of JSON objects, each one representing a different database included in the project. Firebase databases shouldn't be included here.

  | Key  | Nature | Description |
  | ------------- | ------------- | ------------- |
  | id | Mandatory | Identifier of the database that will be used to reference it. |
  | source | Mandatory | Filename of the file that contains the database. It can be a file inside `res` (or a subfolder) or a URL (for online databases) |
  | type | Mandatory | Type of database. It can be `csv` or `json`|
  

## Fonts
The `fonts` parameter is a JSON object that contains a list of key-value parameters, each one representing a TrueType font that will be used in the app. The key will be used as the identifier to use this font on texts inside the app. The value is the name of the ttf file that contains the font, which must be located inside the `fonts` folder inside the `res` folder.

Here's an example:
<pre>
    "fonts":{
        "young":"fonts/Louis_George_Cafe.ttf",
        "renner":"fonts/Renner_ 400Book.ttf",
        "monospatial":"fonts/nk57-monospace-no-lt.ttf",
        "linux":"fonts/LinLibertine_R.ttf"
    }
</pre>
