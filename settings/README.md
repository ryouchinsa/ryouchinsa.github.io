# [RectLabel](https://rectlabel.com)
How to use? Read our [Help page](https://rectlabel.com/help/).

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

# Settings menus
- [Projects](https://rectlabel.com/settings#projects)
- [Objects](https://rectlabel.com/settings#objects)
- [Attributes](https://rectlabel.com/settings#attributes)
- [Hotkeys](https://rectlabel.com/settings#hotkeys)
- [Label fast](https://rectlabel.com/settings#label-fast)
- [Export/Import settings file](https://rectlabel.com/settings#exportimport-settings-file)
- [Locate settings file](https://rectlabel.com/settings#locate-settings-file)
- [Open app folder](https://rectlabel.com/settings#open-app-folder)

# Projects
A project contains an objects table and an attributes table.
- To switch the project, check on the "Primary" check box.
- To import projects, use RectLabel menu -> Import settings file.

![projects](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/b0a14482-a947-4816-bb0a-e16f265efc42)

# Objects
The objects table describes each object name and the object index.
- You can assign 0-9 number keys and A-Z alphabet keys to object names.
- To import objects, use Export menu -> Import an object names from a file. You can drag & drop an object names file to the objects table.
- Right clicking on the objects table header, "Sort alphabetically" menu appears.

![objects](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/d21486a7-e9a4-477a-93c6-7d841ea9af96)

# Attributes
The label "sneakers-converse-yellow" is a combination of the object name and attribute names.
- '-' is used as a separator so that '-' in the object name and attribute name is replaced with '\_'.
- If any objects are not using attributes, '-' in the object name is not replaced with '\_'.
- The prefix is used such as '-' + prefix + attribute name.
- The attribute types are "Single select", "Multiple select", and "Text input".
- You can assign 0-9 number keys and A-Z alphabet keys to attribute names.
- Right clicking on the attributes table header, "Sort alphabetically" menu appears.

![attributes](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/a4fb8154-3391-49c2-94d0-20513395a085)

# Hotkeys
Customize hotkeys to make your labeling work faster.

![hotkeys](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/e4933560-769d-490a-addc-80e9b3643c68)

# Label fast
Customize settings to make your labeling work faster.

- "Auto save" is to skip the confirmation dialog when save.
- "Auto copy from previous image" is to copy annotations from the previous image.
- "Skip backup dialog when overwrite" is to skip the backup dialog when overwrite.
- "Clear existing labels when auto label all images" is to clear existing labels when auto label all images.
- "Skip label dialog when create" is to skip the label dialog when create.
- "Close label dialog when select" is to close the label dialog when select an object name.
- "Change label when press an object/attribute hotkey" is to change the label using hotkeys.
- "Add an image label when press an object hotkey" is to add an image label using hotkeys.
- "Use 1-click buttons" is to show 1-click buttons of object names on the label dialog.
- "Maintain zoom and position" is to maintain zoom and position when you change the image.
- "Do not move image position" is to fix the image position.
- "Show circle edit points" is to show circle edit points instead of rectangle edit points.
- "Show all edit points" is to show edit points of all objects.
- "Show edit points between box corners" is to show edit points between box corners.
- "Show the first point of the box" is to show the first point of the box.
- "Click 4 points when draw boxes" is to draw a box clicking xmin, xmax, ymin, and ymax of the object.
- "Use truncated, occluded, and difficult tags" is to show truncated, occluded, and difficult checkboxes on the label dialog.
- "Rotate boxes as rotated boxes when augment" is to rotate boxes as rotated boxes when augment.
- "Separate merged polygons when read YOLO format" is to separate merged polygons when read YOLO format.
- "Save confidence values when YOLO format" is to save confidence values when YOLO format.
- "Save as floating-point values" is to save coordinates as floating-point values.
- "Use English as an app language" is to change the app language to English.

![label_fast](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/d73f7c26-41f2-4b08-b389-5f58bc0ad487)

# Export/Import settings file
You can export the current settings file and import to another computer.

# Locate settings file
You can change the location of the settings file. If you change the location to iCloud drive, you can share the settings file among multiple devices.

# Open app folder
You can open an app folder and delete the cache files.

