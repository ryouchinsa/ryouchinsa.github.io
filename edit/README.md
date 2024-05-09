# [RectLabel](https://rectlabel.com)
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

Thank you.

# Edit menus
- [Create box](https://rectlabel.com/edit#create-box)
- [Create polygon, cubic bezier, line, and point](https://rectlabel.com/edit#create-polygon-cubic-bezier-line-and-point)
- [Create polygon using SAM](https://rectlabel.com/edit#create-polygon-using-sam)
- [Create keypoints](https://rectlabel.com/edit#create-keypoints)
- [Create pixels](https://rectlabel.com/edit#create-pixels)
- [Create image label](https://rectlabel.com/edit#create-image-label)
- [Move](https://rectlabel.com/edit#move)
- [Rotate](https://rectlabel.com/edit#rotate)
- [Rotate the image right/left](https://rectlabel.com/edit#rotate-the-image-rightleft)
- [Delete](https://rectlabel.com/edit#delete)
- [Layer up/down](https://rectlabel.com/edit#layer-updown)
- [Toggle erase](https://rectlabel.com/edit#toggle-erase)
- [Change brightness and contrast](https://rectlabel.com/edit#change-brightness-and-contrast)
- [Change object color](https://rectlabel.com/edit#change-object-color)
- [Clear object color](https://rectlabel.com/edit#clear-object-color)
- [Search images](https://rectlabel.com/edit#search-images)
- [Clear search images](https://rectlabel.com/edit#clear-search-images)
- [Replace labels](https://rectlabel.com/edit#replace-labels)
- [Undo/Redo](https://rectlabel.com/edit#undoredo)
- [Cut/Copy/Paste](https://rectlabel.com/edit#cutcopypaste)

# Create box
Create a box.
- Click 2 points.
- The label dialog opens, select an object name and attribute names.
- Press OK button, and the selected label is added to the labels table.

Move the box.
- Drag the center of the box to move the box.
- Drag one of the four corner points to transform the box.
- Drag on the box pressing the option key, the box size is scaled up/down from the center.

Select multiple boxes.
- Drag a box pressing the command key, you can select multiple boxes.

Change color.
- To change the box color, use the color picker at the top-right corner.
- To change the cross hairs color, deselect all boxes and change the default color.

View menus.
- "Focus box" to quick zoom to the selected box.
- "Hide cross hairs" to hide cross hairs.
- "Hide other boxes" to hide other boxes.
- "Show labels on boxes" to show labels on boxes.
- "Show coordinates on boxes" to show (x, y) coordinates on boxes.
- "Show indexes on labels table" to show each row number on the labels table.
- "Show checkboxes on labels table" to show a checkbox to show/hide for each row on the labels table.
- "Show depth image" to show the depth image.

Settings menus.
- "Use 1-click buttons" is to show 1-click buttons of object names on the label dialog.
- "Show edit points between box corners" is to show edit points between box corners.
- "Click 4 points when draw boxes" is to draw a box clicking xmin, xmax, ymin, and ymax of the object.

![drag_to_select](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/bcc72148-d330-4d10-8190-89a571ffb134)

# Create polygon, cubic bezier, line, and point
Create a polygon.
- Click to add points.
- Press an enter key to finish drawing.
- Press an escape key to cancel drawing.

Right click on the point.
- "Add a point forward/backward" to add a point.
You can add a new point clicking a point along the shape.
- "Delete this point" to delete the point.
You can delete a point clicking a point pressing the option key.
- "Set to the first point" to set the point to the first point.
- "Point size up/down" to change the size of points.

Right click on the object.
- "Copy as erase mask" to copy the polygon as an erase mask.
- "Cut using erase mask" to cut the polygon using the erase mask.
- "Convert to polygon" to change to polygon.
- "Convert to cubic bezier" to change to cubic bezier.
- "Convert to rotated box" to change to rotated box.

Merge polygons and separate the polygon.
- Select multiple polygons and right click on them, you can merge polygons.
- Right click on the merged polygon, you can separate the merged polygon.

![edit_points](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/d0bfe027-a54b-4b4b-9d46-9ceda2e78b27)

# Create polygon using SAM
Select a model.
- [MobileSAM](https://github.com/ChaoningZhang/MobileSAM)
- [EfficientSAM](https://github.com/yformer/EfficientSAM)
- [Segment Anything models](https://github.com/facebookresearch/segment-anything)
- [HQ-SAM](https://github.com/SysCV/sam-hq)

Select a create type.
- box
- polygon
- pixels

Create using SAM.
- Press start button to start downloading the model and preprocessing the image.
- Click positive and negative points. Pressing the option key, you can switch the positive/negative mode.
- Press an enter key to finish drawing.
- Press an escape key to cancel drawing.

![sam_polygon](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/c12431bc-c06c-4a61-b9c5-97bd84a9cee8)

![sam_pixels](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/1af17234-5946-4acc-9cbe-7ee195bb5ad8)

# Create keypoints
Create keypoints.
- Click to add points.
- Press an enter key to finish drawing.
- Press an escape key to cancel drawing.

Each keypoint has a visibility flag v defined as below. [Read more](http://cocodataset.org/#format-data)
- v=0: not labeled
- v=1: labeled but not visible
- v=2: labeled and visible

Change visibility when click each keypoint.
- Click pressing the option + command keys, the point is added as not labeled.
- Click pressing the option key, the point is added as labeled but not visible.

Create the skeleton.
- To add an edge, drag from one to another point pressing the option key.
- Drag an point pressing the shift key, the line angle between the point and the neighbor point is locked.

Right click on the point.
- "Change keypoint name" to change the keypoint name. 
- "Change keypoint color" to change the keypoint color. The edge color is defined by the source point color.
- "Make not labeled" to make the point not labeled.
- "Make labeled but not visible" to make the point as labeled but not visible.
- "Delete edge" to delete the edge connected with the point.

Right click on the object.
- "Clear bounding box" to clear the current bounding box.
- "Flip horizontally" to flip the "left" included keypoint position and the "right" included keypoint position.
- "Make visible" to make the point visible.

Keypoints names and edges are saved in the settings file.
For the first keypoints object, you have to press an enter key to finish drawing, change keypoints names, and add edges.

View menus.
- "Hide keypoints names" to hide keypoints names.
- "Show boxes on keypoints" to show and edit the bounding box.



# Create pixels
Create pixels using brushes.
- Drag to draw pixels.
- Change the brush size, pressing the command + option keys, and mouse wheel up/down.
- Erase is used to erase pixels.
- Polygon is used to label pixels using the polygon tool.

Right click on the object.
- "Convert to polygon" to convert the pixels to polygon.
- "Flood Fill" to fill the closed pixels area.
- "Clear pixels" to clear the pixels.
- "Import pixels" to import a mask image as pixels.

Import pixels.
- You can drag & drop grayscale mask images to the labels table.
- You can drag & drop the COCO RLE JSON file of the [SA-1B dataset](https://github.com/facebookresearch/segment-anything) to the labels table.

Select pixels.
- Changing to the Move mode, you can click to select each pixels object on the image.
- Changing to the Create box mode, dragging a box, you can select multiple pixels objects.

The pixels file is saved as {image_file_name}_pixels{pixels_idx}.png in the annotations folder.

View menus.
- "Hide pixels" to toggle pixels alpha.
- "Hide superpixels" to toggle superpixels alpha.
- "Show small pixels" to show small pixels areas.
- "Show other pixels" to show other pixels objects.

![brush](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/f0cbbb48-bd6f-4323-8dfe-5ea6844477a1)

Create pixels using superpixels.
- Click each superpixel or drag multiple superpixels.
- Superpixel size is used to adjust the segmentation size.
- Superpixel smoothness is used to adjust the segmentation smoothness.
- On the pixels panel, right/left arrow keys change the superpixel size by 1px.
- If superpixels are not shown, reselect the label on the labels table.

![superpixel](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/e1cdce3d-3985-4ed3-8a5c-7657f29a929f)

# Create image label
Create an image label without drawing the box.

Settings menu.
- “Add an image label when press an object hotkey” is to add an image label using hotkeys.

# Move
Select an object.
- Click an object to select.
- Pressing the command key, click multiple objects to select.
- To switch between Create and Move mode, hold the space key when Create mode.

Move an object/image.
- Drag an object or the image to move the position.
- You can select multiple objects and move them.
- You can use mouse wheel to move the image position.

Right click on the object.
- "Focus" to quick zoom to the selected object.
- "Edit" to open the label dialog. Double click on the object, the label dialog opens.
- "Copy" to copy the object.
- "Delete" to delete the object.

# Rotate
Rotate an object.
- Drag up/down on the object to rotate the object.
- You can select multiple objects and rotate them.

Settings menu.
- “Show the first point of the box” is to show the first point of the box.

![draw_obb](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/2aa869e8-f3d9-45ed-90a1-4424dfc909b6)

# Rotate the image right/left
You can rotate the image and annotation to the right/left by 90 degrees.

# Delete
You can select multiple objects and delete them.

# Layer up/down
Change the layer order of the object.

![layer_order](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/6d24af7e-86f8-4b63-bc0b-19f33ad5e721)

# Toggle erase
Erase points/mask when Create polygon mode.
- "Erase points" erases polygon points inside the drawn dashed area.
- "Erase mask" erases the drawn dashed area from the polygon.

![erase_points](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/c55e04bb-fd7f-4e9b-9f84-7c98997dbb07)

Erase pixels when Create pixels mode.

![erase_pixels](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/320e5b31-63ed-4224-be08-4c6cb841d798)

# Change brightness and contrast
Change the image brightness and contrast for dark images.

![contrast](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/6d7b98a6-b22a-47bb-8315-f45a809d3910)

# Change object color
Change the object color using the color picker.

# Clear object color
Clear the object color to the default color.

# Search images
You can search object, attribute, and image names in a gallery view.
- To search labeled images, use "notempty" search text.
- To search unlabeled images, use "" search text.

![search](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/725d6a93-5f29-4b3d-9adf-b9f052954d46)

# Clear search images
Clear searching and show all images.

# Replace labels
Replace labels using regular expressions.

# Undo/Redo
You can undo/redo actions.

# Cut/Copy/Paste
You can select multiple boxes and cut/copy/paste them on another image.



