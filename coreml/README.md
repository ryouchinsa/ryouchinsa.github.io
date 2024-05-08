# [RectLabel](https://rectlabel.com)
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

Thank you.

# Core ML menus
- [Load Core ML model](https://rectlabel.com/export#load-core-ml-model)
- [Clear Core ML model](https://rectlabel.com/export#clear-core-ml-model)
- [Auto labeling](https://rectlabel.com/export#auto-labeling)
- [Auto text recognition for lines and words](https://rectlabel.com/export#auto-text-recognition-for-lines-and-words)

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

![a](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/96c172b5-0e51-47a6-a467-f02611498445)

![a](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/3b826f68-f7bf-4267-a4ba-a5a468244a79)

![a](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/bc591ded-180c-4eee-b4c8-82a12ff4651a)

# Auto text recognition for lines and words
Using [Vision Framework](https://developer.apple.com/documentation/vision), automatic text recognition is performed.
- You can change the language.
- You can change the type to lines or words.

![ocr](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/3cbf40cd-ece4-451b-b2e8-12ea6e4724c7)








