# [RectLabel](https://rectlabel.com)
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

# File menus
- [Open images folder and annotations folder](https://rectlabel.com/file#open-images-folder-and-annotations-folder)
- [Open a folder which includes a yaml file](https://rectlabel.com/file#open-a-folder-which-includes-a-yaml-file)
- [Convert video to image frames](https://rectlabel.com/file#convert-video-to-image-frames)
- [Remove EXIF orientation flags](https://rectlabel.com/file#remove-exif-orientation-flags)
- [Rename image](https://rectlabel.com/file#rename-image)
- [Resize images](https://rectlabel.com/file#resize-images)
- [Next image and Prev image](https://rectlabel.com/file#next-image-and-prev-image)
- [Jump to image number](https://rectlabel.com/file#jump-to-image-number)
- [Copy/Move/Delete images](https://rectlabel.com/file#copymovedelete-images)
- [Save](https://rectlabel.com/file#save)
- [Close folder](https://rectlabel.com/file#close-folder)

# Open images folder and annotations folder
- You can drag & drop each images folder and annotations folder to the open table.
- "Label format" is to change the label format to read/write in the PASCAL VOC xml format or YOLO text format.
- "Sort images" is to sort images by Alphabetic, Numeric, and Last modified.
- "Read images folder recursively" is to open an images folder which includes sub-folders.
- After opening images, we recommend to use File menu -> Remove EXIF orientation flags.
- Image file names which include "_pixels", "_depth", and "_masks" are skipped.
- To copy the current image file name, click on the image file name shown at the top-left corner.

```
├── images
│   ├── 0.jpg
│   └── 1.jpg
└── annotations
    ├── 0.xml or 0.txt
    └── 1.xml or 1.txt
```

Drag & drop the root folder to the open table, child images and annotations/labels folders are automatically set.

```
└── root_folder
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

<video src="https://github.com/user-attachments/assets/96b128b1-2605-4cd3-b0d4-3ed06030649a" controls="controls" muted="muted" class="width-fit" style="max-height:640px; min-height: 200px"></video>

Once opened images and annotations folders, from the second launch, you can use command line arguments to RectLabel which image files should be opened.

```
open -a RectLabel --args -images 000000000872.jpg,000000010363.jpg
open -a RectLabel\ Pro --args -images 000000000872.jpg,000000010363.jpg
```

# Open images folder
The annotations folder should be images/annotations.

# Open a folder which includes a yaml file
You can open the exported YOLOv5/YOLOv8/YOLO11 folder.

```
└── exported_folder
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

![video](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/a7bc4ecd-8bb3-4b0d-85a0-347c0b32d6ae)

# Remove EXIF orientation flags
- On RectLabel, according to the [Exif orientation flags](https://github.com/recurser/exif-orientation-examples), each image is rotated and shown in the front orientation.
- You can remove the EXIF orientation flags from images and convert images to the front orientation.

# Rename image
- You can rename the image name.

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

# Copy/Move/Delete images
- You can move/copy all images or random fraction of total to another folder.
- Using Edit menu -> Search images, you can move/copy searched images to another folder.
- Deleted images and annotations are moved to the app folder.

# Save
The annotation file is saved as {image_file_name}.xml in the PASCAL VOC xml format or {image_file_name}.txt in the YOLO text format.

# Close folder
You can close current images and annotations folders.

