# [RectLabel](https://rectlabel.com)
How to use? Read our [Help page](https://rectlabel.com/help/).

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

# Edit menus
- [Create box](https://rectlabel.com/edit#create-box)
- [Create polygon, cubic bezier, line, and point](https://rectlabel.com/edit#create-polygon-cubic-bezier-line-and-point)
- [Create polygon using SAM](https://rectlabel.com/edit#create-polygon-using-sam)
- [Create keypoints](https://rectlabel.com/edit#create-keypoints)
- [Create pixels](https://rectlabel.com/edit#create-pixels)
- [Create image label](https://rectlabel.com/edit#create-image-label)
- [Create memo](https://rectlabel.com/edit#create-memo)
- [Move](https://rectlabel.com/edit#move)
- [Rotate](https://rectlabel.com/edit#rotate)
- [Rotate the image right/left](https://rectlabel.com/edit#rotate-the-image-rightleft)
- [Delete](https://rectlabel.com/edit#delete)
- [Layer up/down](https://rectlabel.com/edit#layer-updown)
- [Toggle erase](https://rectlabel.com/edit#toggle-erase)
- [Copy as erase mask](https://rectlabel.com/edit#copy-as-erase-mask)
- [Cut using erase mask](https://rectlabel.com/edit#cut-using-erase-mask)
- [Start SAM preprocessing](https://rectlabel.com/edit#start-sam-preprocessing)
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

![box2](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/354ca023-22df-451d-ade9-00b69e01315b)

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

![edit_points](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/d718987d-a616-4430-ae57-52a9baaf7a25)

# Create polygon using SAM
Select a model.
- [Segment Anything Model 2](https://github.com/facebookresearch/sam2)
- [Segment Anything Model](https://github.com/facebookresearch/segment-anything)
- [MobileSAM](https://github.com/ChaoningZhang/MobileSAM)

Select a create type.
- box
- polygon
- pixels

Create using SAM.
- Press start button to start downloading the model and preprocessing the image.
- Click positive and negative points. Pressing the option key, you can switch the positive/negative mode.
- Press an enter key to finish drawing.
- Press an escape key to cancel drawing.

Right click on the object.
- "Convert to polygon/pixels using SAM" to convert selected boxes to polygons/pixels after preprocessing the image using SAM.

![sam2_polygon](https://github.com/user-attachments/assets/052f467f-b94d-4137-9c40-ca8cf80b3a51)
![sam2_pixels](https://github.com/user-attachments/assets/05c9ece6-1906-4196-9676-6b96053ee61f)

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
- "Set bounding box from the next polygon" to set the bounding box from the next polygon or pixels object.
- "Clear all keypoints" to set 0 visible value for all keypoints.
- "Flip horizontally" to flip the "left" included keypoint position and the "right" included keypoint position.
- "Make visible" to make the point visible.

Keypoints names and edges are saved in the settings file.
For the first keypoints object, you have to press an enter key to finish drawing, change keypoints names, and add edges.

View menus.
- "Hide keypoints names" to hide keypoints names.
- "Show boxes on keypoints" to show and edit the bounding box.

<video src="https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/ec057788-1cd5-43d9-b5c4-b16f348ea619" controls="controls" muted="muted" class="width-fit" style="max-height:640px; min-height: 200px"></video>

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

![brush](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/2195d55f-ded2-48fd-a953-4b7b21834fa4)

Create pixels using superpixels.
- Click each superpixel or drag multiple superpixels.
- Superpixel size is used to adjust the segmentation size.
- Superpixel smoothness is used to adjust the segmentation smoothness.
- On the pixels panel, right/left arrow keys change the superpixel size by 1px.
- If superpixels are not shown, reselect the label on the labels table.

![superpixel](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/1ab1aa17-dee1-4c7a-ad70-b1b137399415)

# Create image label
Create an image label without drawing the box.

Settings menu.
- “Add an image label when press an object hotkey” is to add an image label using hotkeys.

# Create memo
Create memo for the image and can be used for searching. This feature works for the PASCAL VOC xml format.

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

![draw_obb](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/73300c44-76e4-413e-9cff-66e7747c2700)

# Rotate the image right/left
You can rotate the image and annotation to the right/left by 90 degrees.

# Delete
You can select multiple objects and delete them.

# Layer up/down
Change the layer order of the object.

![layer_order](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/4909bd70-f806-419f-a53a-d31fba9549fe)

# Toggle erase
Erase points/mask when Create polygon mode.
- "Erase points" erases polygon points inside the drawn dashed area.
- "Erase mask" erases the drawn dashed area from the polygon.

![erase_points](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/2f39c8fe-305d-4c43-866c-7c15609f274a)

Erase pixels when Create pixels mode.

![erase_pixels](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/5ac2f132-af4f-47a7-b071-e565bbd8d167)

# Copy as erase mask
Copy the polygon as an erase mask.

# Cut using erase mask
Cut the polygon using the erase mask.

# Start SAM preprocessing
Start downloading the SAM model and preprocessing the image.

# Change brightness and contrast
Change the image brightness and contrast for dark images.

# Change object color
Change the object color using the color picker.

# Clear object color
Clear the object color to the default color.

# Search images
You can search object, attribute, image names, and memo in a gallery view.
- To search labeled images, use "notempty" search text.
- To search unlabeled images, use "" search text.

![search4](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/550ea105-c2cf-4085-9851-696a069192cb)

# Clear search images
Clear searching and show all images.

# Replace labels
Replace labels using regular expressions.

# Undo/Redo
You can undo/redo actions.

# Cut/Copy/Paste
You can select multiple boxes and cut/copy/paste them on another image.



