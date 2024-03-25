# RectLabel
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

Thank you.

# Create box
Change the mode to "Create box".

To draw a box, click 2 points.

If necessary, click 4 points for xmin, xmax, ymin, and ymax of the object.

Press enter key to finish drawing when the number of points is less than 4.

When you finished drawing, the label dialog would open, and the label would be added to the label table.

Drag the center of the box to move the box.

Drag one of the four corner points to transform the box.

If necessary, show edit points between box corners.

Drag on the box pressing the option key, the box size is scaled up/down from the center.

Drag a box pressing the command key, you can select multiple boxes.

When you select multiple boxes and right click on them, you can merge boxes.

To change the box color, use the color picker at the top-right corner.

To change the cross hairs color, deselect all boxes and change the default color.

You can hide the cross hairs.

You can show labels on boxes.

![drag_to_select](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/25fe9bc3-259c-4dfa-8c36-ef9b64f33b08)

# Create polygon, cubic bezier, line, and point
Change the mode to "Create polygon", "Create cubic bezier", "Create line", or "Create point".

Click to add points.

Press enter key to finish drawing.

Press escape key to cancel drawing.

When you right click on the point, edit menu would open.

"Add a point forward/backward" to add a point.

You can add a new point to the polygon/cubic bezier/line, clicking a point along the shape.

"Delete this point" to delete the point.

You can delete a point on the polygon/cubic bezier/line/point, clicking a point pressing the option key.

"Set to the first point" to set the point to the first point for DOTA text format.

"Point size up/down" to change the size of points.

When you right click on the label, edit menu would open.

"Copy as erase mask" to copy the polygon as an erase mask.

"Paste as erase mask" to paste the copied erase mask to the polygon.

"Convert to polygon" to change to polygon.

"Convert to cubic bezier" to change to cubic bezier.

"Convert to rotated box" to change to rotated box.

When you select multiple polygons and right click on them, you can merge polygons.

To separate the merged polygon to multiple polygons, right click on the merged polygon.

![edit_points](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/83d29639-cef4-49f0-860e-011ace0ddf6b)

# Create polygon using SAM
Change the mode to "Create polygon using SAM".

Select a model among [MobileSAM](https://github.com/ChaoningZhang/MobileSAM), [EfficientSAM](https://github.com/yformer/EfficientSAM), [HQ-SAM](https://github.com/SysCV/sam-hq), and [Segment Anything models](https://github.com/facebookresearch/segment-anything).

Press start button to start downloading the model and preprocessing the image. After preprocessing, you can click positive and negative points.

Pressing the option key, you can switch the positive mode and negative mode.

Press enter key to finish labeling.

Press escape key to cancel labeling.

![sam_polygon](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/09f08a66-cafa-4145-862e-409abadb3800)

![sam_pixels](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/a6d7a1b4-b611-461a-91e2-1a707a602b3e)

# Create keypoints
Change the mode to "Create keypoints".

Click to add points.

Click holding option + command button, the point is added as not labeled.

Click holding option button, the point is added as labeled but not visible.

Press enter key to finish drawing.

Press escape key to cancel drawing.

To add an edge, drag from one to another point holding option button.

Drag an point pressing the shift key, the line angle between the point and the neighbor point is locked during the transformation.

[Each keypoint has a visibility flag v defined as v=0: not labeled, v=1: labeled but not visible, and v=2: labeled and visible](http://cocodataset.org/#format-data).

When you right click on the point, edit menu would open.

"Change keypoint name" to change the keypoint name.

You can hide keypoints names.

"Change keypoint color" to change the keypoint color and the edge color is defined by the source point color.

"Make not labeled" to make the point not labeled.

"Make labeled but not visible" to make the point as labeled but not visible.

"Delete edge" to delete the edge with the point.

If you put empty string to the keypoint name, the keypoint name is hidden.

When you right click on the label, edit menu would open.

"Clear bounding box" to clear the current bounding box.

To show and edit the bounding box, show boxes on keypoints.

"Flip horizontally" to flip the "left" included keypoint position and the "right" included keypoint position.

"Make visible" to make the point visible.

Keypoints names and edges are saved in the settings file.

For the first keypoints object, you have to press enter key to finish drawing, change keypoints names, and add edges.

From the second keypoints object, if currently selected object or lastly selected object has keypoints names and edges, the label dialog would appear without pressing the enter key and keypoints names and edges are automatically shown.

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

To show all images again, clear search images.

You can use [Wildcard(*), AND(&), OR(|), NOT(!), and more](https://developer.apple.com/library/content/documentation/UserExperience/Conceptual/SearchKitConcepts/searchKit_concepts/searchKit_concepts.html#//apple_ref/doc/uid/TP40002844-BAJFJGFF) in the search text.

To search labeled images, use "notempty" search text. To search unlabeled images, use "" search text.

![search](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/18eaeed8-07c0-4688-85f8-f78a6eb4b4ea)

# Clear search images
Clear searching and show all images.

# Replace labels
Replace labels using regular expressions.

# Undo/Redo
You can undo/redo actions.

# Cut/Copy/Paste
You can select multiple boxes and cut/copy/paste them on another image.


