# RectLabel
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

Thank you.

# Projects
A project contains an objects table and an attributes table.
To switch the project, check on the "Primary" check box.
To import projects from another settings file, use RectLabel menu -> Import settings file.

![projects](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/d89ed448-7d9d-4c92-8ff2-25e7f5936dc4)

# Objects
The objects table describes each object name and the object index.
You can assign 0-9 number keys and A-Z alphabet keys to objects.
To add objects from a text file, use Export menu -> Import an object names from a file.
You can drag & drop an object names file to the objects table.
You can copy object names from a text file to your pasteboard and paste to the objects table.
Right clicking on the objects table header, "Sort alphabetically" menu appears.

![objects](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/35ebf61e-f40b-4d56-a1d8-2a9ad5b2d6d4)

# Attributes
The label "sneakers-converse-yellow" is a combination of the object name and attribute names.
'-' is used as a separator so that '-' in the object name and attribute name is replaced with '\_'.
The prefix is used such as '-' + prefix + attribute name.
If any objects are not using attributes, '-' in the object name is not replaced with '\_'.
The attribute types are "Single select", "Multiple select", and "Text input".
To change the name on the items table, single click, double click, or press an enter key on the selected item.
For "Single select" type, you can use an empty string item so that the default label becomes the object name.
You can assign 0-9 number keys and A-Z alphabet keys to items.
Right clicking on the attributes table header, "Sort alphabetically" menu appears.

![attributes](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/97dd3b07-950f-42dd-afd2-c3026f2f9c23)

# Hotkeys
Customize hotkeys to make your labeling work faster.

![hotkeys](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/5636160e-ebe2-40b9-98f2-186aae86a236)

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

![label_fast](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/55ec35bf-aff8-4532-a6dd-3546d4c332cb)


