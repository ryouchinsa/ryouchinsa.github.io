# [RectLabel](https://rectlabel.com)
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

# Core ML menus
- [Load Core ML model](https://rectlabel.com/coreml#load-core-ml-model)
- [Auto labeling](https://rectlabel.com/coreml#auto-labeling)
- [Auto text recognition for lines and words](https://rectlabel.com/coreml#auto-text-recognition-for-lines-and-words)
- [Toggle auto process](https://rectlabel.com/coreml#toggle-auto-process)
- [Search incorrectly predicted images](https://rectlabel.com/coreml#search-incorrectly-predicted-images)

# Load Core ML model
- Apple provides [Core ML Models](https://developer.apple.com/machine-learning/models/).
- To convert your ML model to the Core ML format, use [coremltools](https://github.com/apple/coremltools).
- You can convert [YOLOv5](https://github.com/ultralytics/yolov5), [YOLOv8/YOLO11/YOLO26](https://github.com/ultralytics/ultralytics), and [MobileNetV2 + SSDLite](https://machinethink.net/blog/mobilenet-ssdlite-coreml/) models to Core ML models.

# Auto labeling
Auto label images using the loaded Core ML model.
- You can change the confidence threshold.
- if the model does not include the non-maximum suppression, you can change the overlap threshold.
- If check on the "Auto" checkbox, when change the image, the image is automatically processed.
- For the "Filter by class", if you put "person", RectLabel finds only "person" class.

View menu.
- “Show labels on boxes” to show confidences on boxes.

Settings menus.
- “Skip backup dialog when overwrite” is to skip the backup dialog when overwrite.
- “Clear existing labels when auto label all images” is to clear existing labels when auto label all images.
- “Save confidence values when YOLO format” is to save confidence values when YOLO format.

![coreml](https://github.com/user-attachments/assets/e1276709-2a43-45cc-9cf6-95255b693df9)

![coreml_polygon](https://github.com/user-attachments/assets/e5cb7140-10da-4b8e-bad7-8f55091917a4)

![coreml_pixels](https://github.com/user-attachments/assets/55457942-a20c-4673-b36a-8c9d97cc35a4)

# Auto text recognition for lines and words
Using [Vision Framework](https://developer.apple.com/documentation/vision), automatic text recognition is performed.
- You can change the language.
- You can change the type to lines or words.

![ocr](https://github.com/user-attachments/assets/c60f4e34-c943-4d3d-9b39-a8efc4ada93d)

# Toggle auto process
You can auto label when change the image if you check on the "Auto process" checkbox on the Core ML dialog.

# Search incorrectly predicted images
Show training images which predicted labels and boxes are incorrect compared with the current annotations. Such as "Not detected", "Not classified", and "Falsely detected".

![search_incorrectly](https://github.com/user-attachments/assets/75567a43-bfec-4041-9bc3-25e8977c1ddc)










