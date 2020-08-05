# Res folder

This folder should always exist, at least for adding an icon for our project.

Inside this folder we will place all the content files that we will use at some point of our app. The files stored inside the `res` folder will only be added to the final app in case they are used in some component of any other place.

The `res` folder can have subfolders to organize our files. The next 3 folders are used by Codoozer.

##### res / assets

The `assets` folder is a special (and optional) folder. All the files inside that folder will be ALWAYS be added to the final app, even if they are not used directly in our project. This is useful in case we have the intention to use those resources on databases, cookies, etc.

##### res / fonts

This folder is only needed if we want to use TTF fonts in our project. We must add the font files in this folder, but also add the fonts inside the app.json file.

##### res / icon

This folder must include at least a PNG file, that will be the default icon to be used in all those case when we don't set an specific icon.

If the name of an icon file starts with `icon_` followed by a number (icon_114.png), that icon will be used for those platforms (or versions) that need an icon of that size in pixels.

We can also use the prefix `android` or `ios` to set specific icons for those platforms. For instance, the default icon for android would be called `android.png`, while an icon for android platforms and 114 pixels would be called `android_114.png`.

