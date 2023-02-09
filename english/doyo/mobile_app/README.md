# How to build a mobile native app with Doyo?

With just a single module in our project, we could create a universal native app, so defining it once, it will generate different versions for different platforms (Android Smartphone, Android Tablet, iPhone, iPad, etc.). It will only require some config variations inside the file app.json, in case some platform needs some specific configuration.

As an alternative, we could create different modules, one per platform, in case we need to create different interfaces for each platform.

### File structure for a mobile native app project

For building a mobile native app, our project must have the following structure

[app.json](app.json)  
├── [certificates (optional)](certificates)  
├── [dialogs (optional)](dialogs)  
├── [external (optional)](external)  
├── [menus (optional)](menus)  
├── [res](res)  
│&emsp;&emsp;├── [assets (optional)](res)  
│&emsp;&emsp;├── [fonts (optional)](res)  
│&emsp;&emsp;└── [icon](res)  
├── [view_types](view_types)  
└── [views](views)  



### Functions

Functions are the actions we want the app to do, as a response of some events (app started, user taps on something, a screen is about to be loaded, a screen has finished loading, etc.)

For more information, access the [functions](functions) page.


### References

References are used to access some object (cookie, variable, database, UI components, etc.) in order to get or set its value.

References are so important when building apps with Doyo. They can be used as parameters in functions, as data source on the UI components, and in some other parts of the project.

For more information, please access the [references](references) page.

Thanks to references, we will be able to have a lot of interaction between the user and the app.


