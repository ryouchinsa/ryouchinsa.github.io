# [RectLabel](https://rectlabel.com)
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

Thank you.

# Core ML menus
- [Load Core ML model](https://rectlabel.com/coreml#load-core-ml-model)
- [Clear Core ML model](https://rectlabel.com/coreml#clear-core-ml-model)
- [Auto labeling](https://rectlabel.com/coreml#auto-labeling)
- [Auto text recognition for lines and words](https://rectlabel.com/coreml#auto-text-recognition-for-lines-and-words)

# Load Core ML model
- Apple provides [Core ML Models](https://developer.apple.com/machine-learning/models/).
- To convert your ML model to the Core ML format, use [coremltools](https://github.com/apple/coremltools).
- You can convert [YOLOv5](https://github.com/ultralytics/yolov5), [YOLOv8](https://github.com/ultralytics/ultralytics), and [MobileNetV2 + SSDLite](https://machinethink.net/blog/mobilenet-ssdlite-coreml/) models to Core ML models.

# Clear Core ML model
Clear the loaded Core ML model to close the Confidence/Overlap threshold panel.

# Auto labeling
Auto label images using the loaded Core ML model.
- You can change the confidence threshold.
- if the model does not include the non-maximum suppression, you can change the overlap threshold.

View menu.
- “Show labels on boxes” to show confidences on boxes.

Settings menus.
- “Skip backup dialog when overwrite” is to skip the backup dialog when overwrite.
- “Clear existing labels when auto label all images” is to clear existing labels when auto label all images.
- “Save confidence values when YOLO format” is to save confidence values when YOLO format.

![coreml](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/b2301928-d331-4c69-97a8-5cfd4dd3a826)

![coreml_polygon](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/e1075ebc-ef42-4654-93aa-2b628b387461)

![coreml_seg](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/512b1743-a7cd-4f67-a93a-10234c34ce84)

# Auto text recognition for lines and words
Using [Vision Framework](https://developer.apple.com/documentation/vision), automatic text recognition is performed.
- You can change the language.
- You can change the type to lines or words.

![ocr](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/3cbf40cd-ece4-451b-b2e8-12ea6e4724c7)








