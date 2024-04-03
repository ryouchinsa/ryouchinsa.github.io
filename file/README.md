# RectLabel
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

Thank you.

# Open images folder and annotations folder
- You can drag & drop each images folder and annotations folder to the open table.
- "Label format" is to change the label format to read/write in the PASCAL VOC xml format or YOLO text format.
- "Sort images" is to sort images by Alphabetic, Numeric, and Last modified.
- After opening images, we recommend to use File menu -> Remove EXIF orientation flags.
- Image file names which include "_pixels" or "_depth" are skipped.
- To copy the current image file name, click on the image file name shown at the top-left corner.

```
├── images
│   ├── 0.jpg
│   └── 1.jpg
└── annotations
    ├── 0.xml or 0.txt
    └── 1.xml or 1.txt
```

Once opened images and annotations folders, from the second launch, you can use command line arguments to RectLabel which image files should be opened.

```
open -a RectLabel --args -images 000000000872.jpg,000000010363.jpg
open -a RectLabel\ Pro --args -images 000000000872.jpg,000000010363.jpg
```

![open_table](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/31463bca-5ad5-42bf-831c-d95228c432cd)

# Open images folder
For the annotations folder, RectLabel uses "images/annotations" folder.

```
└── images
    ├── annotations
    ├── 0.jpg
    └── 1.jpg
```

# Open a folder which includes a yaml file
You can open the YOLOv5/YOLOv8 folder exported from Roboflow.

```
└── exported_YOLOv5_YOLOv8_folder
    ├── data.yaml
    ├── train
    │   ├── images
    │   └── labels
    ├── valid
    │   ├── images
    │   └── labels
    └── test
        ├── images
        └── labels
```

# Convert video to image frames
- For "Video file", open a video file.
- For "Output folder", open a folder to save the image frames.
- For "Image size", both width and height would be less than or equal to the size.
- For "Frames per second", to reduce the number of frames to be exported.
- For "Frame suffix", you can select "frame1" or "frame001".

![video_to_frames](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/09f9c4a9-be00-4a41-9716-37809e459b63)

# Remove EXIF orientation flags
- On RectLabel, according to the [Exif orientation flags](https://github.com/recurser/exif-orientation-examples), each image is rotated and shown in the front orientation.
- You can remove the EXIF orientation flags from images and convert images to the front orientation.
- If necessary, you can rotate the image using Edit menu -> Rotate the image right/left.

# Resize images
- You can resize images and annotations.
- For "Image size", both width and height would be less than or equal to the size.
- If "Image size" is empty, images are not resized but annotations are resized to the same size as images.

# Next image and Prev image
- To show the next image, press the right arrow key.
- To show the previous image, press the left arrow key.
- Pressing the command key, the step size becomes 10.
- You can use Trackpad gestures and Magic Mouse gestures.

# Jump to image number
You can specify the image number to show.

# Move images
- You can move all images or random fraction of total to another folder.
- Searching images, you can move searched images to another folder.

# Copy images
- You can copy all images or random fraction of total to another folder.
- Searching images, you can copy searched images to another folder.

# Save
The annotation file is saved as {image_file_name}.xml in the PASCAL VOC xml format or {image_file_name}.txt in the YOLO text format.

# Close folder
You can close current images and annotations folders.

