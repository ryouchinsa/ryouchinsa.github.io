# RectLabel
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

Thank you.

# Create box

Create a box.
- Click 2 points.
- The label dialog opens, select an object name and attribute names.
- Press OK button, and the selected label is added to the label table.

Move the box.
- Drag the center of the box to move the box.
- Drag one of the four corner points to transform the box.
- Drag on the box pressing the option key, the box size is scaled up/down from the center.

Select multiple boxes.
- Drag a box pressing the command key, you can select multiple boxes.

Change color.
- To change the box color, use the color picker at the top-right corner.
- To change the cross hairs color, deselect all boxes and change the default color.

View menus and Settings.
- View menu -> "Focus box" to quick zoom to the selected box.
- View menu -> "Hide cross hairs" to hide cross hairs.
- View menu -> "Hide other boxes" to hide other boxes.
- View menu -> "Show labels on boxes" to show labels on boxes.
- View menu -> "Show coordinates on boxes" to show (x, y) coordinates on boxes.
- View menu -> "Show indexes on labels table" to show each row number on the labels table.
- View menu -> "Show checkboxes on labels table" to show a checkbox to show/hide for each row on the labels table.
- View menu -> "Show depth image" to show the depth image.
- Settings -> "Use 1-click buttons" is to show 1-click buttons of object names on the label dialog.
- Settings -> "Show edit points between box corners" is to show edit points between box corners.
- Settings -> "Click 4 points when draw boxes" is to draw a box clicking xmin, xmax, ymin, and ymax of the object.

![box](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/cce579b7-5ebc-4e20-9e8a-b92587d57848)

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

Right click on the label.
- "Copy as erase mask" to copy the polygon as an erase mask.
- "Cut using erase mask" to cut the polygon using the erase mask.
- "Convert to polygon" to change to polygon.
- "Convert to cubic bezier" to change to cubic bezier.
- "Convert to rotated box" to change to rotated box.

Merge polygons and separate the polygon.
- Select multiple polygons and right click on them, you can merge polygons.
- Right click on the merged polygon, you can separate the merged polygon.

# Create polygon using SAM
Change the mode to "Create polygon using SAM".
Select a model.
- [MobileSAM](https://github.com/ChaoningZhang/MobileSAM)
- [EfficientSAM](https://github.com/yformer/EfficientSAM)
- [Segment Anything models](https://github.com/facebookresearch/segment-anything).
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

![donut](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/da3a1f7a-2af4-4d34-8a6e-2864a0edf26d)

# Create keypoints
Create keypoints.
- Click to add points.
- Press an enter key to finish drawing.
- Press an escape key to cancel drawing.

Each keypoint has a visibility flag v defined as v=0: not labeled, v=1: labeled but not visible, and v=2: labeled and visible. [Read more](http://cocodataset.org/#format-data)
- Click holding option + command button, the point is added as not labeled.
- Click holding option button, the point is added as labeled but not visible.

To add an edge, drag from one to another point holding option button.
Drag an point pressing the shift key, the line angle between the point and the neighbor point is locked during the transformation.

When you right click on the point, edit menu opens.
- "Change keypoint name" to change the keypoint name.
To hide keypoints names, use View menu -> "Hide keypoints names".
If you put empty string to the keypoint name, the keypoint name is hidden.
- "Change keypoint color" to change the keypoint color and the edge color is defined by the source point color.
- "Make not labeled" to make the point not labeled.
- "Make labeled but not visible" to make the point as labeled but not visible.
- "Delete edge" to delete the edge with the point.

![keypoints](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/96d99cfd-51d4-4ad9-9a6d-616df41e96d8)

When you right click on the label, edit menu opens.
- "Clear bounding box" to clear the current bounding box.
To show and edit the bounding box, use View menu -> "Show boxes on keypoints".
- "Flip horizontally" to flip the "left" included keypoint position and the "right" included keypoint position.
- "Make visible" to make the point visible.

Keypoints names and edges are saved in the settings file.
For the first keypoints object, you have to press an enter key to finish drawing, change keypoints names, and add edges.
From the second keypoints object, if currently selected object or lastly selected object has keypoints names and edges, the label dialog appears without pressing an enter key and keypoints names and edges are automatically shown.

![keypoints](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/1655cc03-5ed0-4fb0-b16b-c0fd8b3744e8)

# Create pixels
You can label pixels using brushes and superpixels.

You can change the brush size using command + option + mouse wheel up/down.

Brush size 1 means 1px in the image.

Erase is used to erase pixels.

When [sidecar](https://support.apple.com/en-us/HT210380), double tap on Apple Pencil toggles the pixels erase checkbox.

Polygon is used to label pixels using the polygon tool.

Right clicking on the pixels, "Convert to polygon", "Flood Fill", "Clear pixels", and "Import pixels" menus appear.

You can drag & drop grayscale mask images to the labels table.

You can drag & drop the COCO RLE JSON file of the [SA-1B dataset](https://github.com/facebookresearch/segment-anything) to the labels table to import mask annotations.

Changing to the Move mode, you can click to select each pixels object on the image.

Changing to the Create box mode, dragging a box, you can select multiple pixels objects.

You can hide pixels.

You can show other pixels.

The pixels file is saved as {image_file_name}_pixels{pixels_idx}.png in the annotations folder.

![brush](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/d0ed1017-4057-4e51-89af-92b045ba104c)

![pixels_to_polygons](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/fc6a66b2-a03a-4083-afaf-627da74671e5)

Click or drag on the superpixels.

Superpixel size is used to adjust the segmentation size.

Superpixel smoothness is used to adjust the segmentation smoothness.

On the pixels panel, right or left arrow key changes the superpixel size by 1px.

You can hide superpixels.

If the superpixels are not shown, reselect the label on the label table.

![superpixel](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/b253bc32-86bc-4bc9-ae7e-8f49394898bb)

# Create image label
You can label the whole image without drawing boxes.

To train an image classifier model, export images for classification.

# Move
Change the mode to "Move".

To switch between Create and Move mode, hold space key when Create mode.

Drag the box or the image to move the position.

You can use mouse wheel to move the image position.

You can select multiple boxes and move them.

When you click on the box or the label, four corner points would appear.

Drag one of the four corner points to transform the box.

When you right click on the box or the label, edit menu would open.

"Focus" to quick zoom to the selected box, "Edit" to open the label dialog, "Duplicate" to duplicate the box, and "Delete" to delete the box.

When you double click on the box or the label, the label dialog would open.

To change the layer order, drag the label up/down on the label table.

# Rotate
Change the mode to "Rotate".

Drag up/down on the box to rotate the box.

You can select multiple boxes and rotate them.

![draw_obb](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/8fa54081-a002-4879-bdd2-19fe3025a005)

# Rotate the image right/left
You can rotate the image and annotation to the right/left by 90 degrees.

# Delete
You can select multiple boxes and delete them.

# Layer up/down
Change the layer order of the box.

![layer_order](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/d454efc7-0c00-4d60-932e-22827eec7cfb)

# Toggle erase
For creating polygon mode, toggling the erase mode, the "Erase polygon" panel is shown, and you can use the polygon tool for erasing multiple points of the selected polygon.

"Erase points" erases polygon points inside the drawn dashed area.

"Erase mask" erases polygon points in the same way as pixels mask.

![erase_points](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/2e1affe2-139c-47b1-93c6-f87258274d55)

![erase_mask](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/86a0e55c-2b7f-4c44-a24b-ad34c44b8ae1)

![erase_pixels](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/c0d998d5-d058-4c2d-acff-7e0807285367)

# Change brightness and contrast
Change the image brightness and contrast for dark images.

![contrast](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/9808a0a2-fd39-455b-b028-d1d3c33f264d)

# Change object color
Change the object color using the color picker.

# Clear object color
Clear the object color to the default color.

# Search images
You can search object, attribute, and image names in a gallery view.
- To search labeled images, use "notempty" search text.
- To search unlabeled images, use "" search text.

![search](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/18eaeed8-07c0-4688-85f8-f78a6eb4b4ea)

# Clear search images
Clear searching and show all images.

# Replace labels
Replace labels using regular expressions.

# Undo/Redo
You can undo/redo actions.

# Cut/Copy/Paste
You can select multiple boxes and cut/copy/paste them on another image.



