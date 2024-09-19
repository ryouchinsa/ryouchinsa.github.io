# [RectLabel](https://rectlabel.com)
How to use? Read our [Help page](https://rectlabel.com/help/).

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

# Core ML menus
- [Load Core ML model](https://rectlabel.com/coreml#load-core-ml-model)
- [Auto labeling](https://rectlabel.com/coreml#auto-labeling)
- [Auto text recognition for lines and words](https://rectlabel.com/coreml#auto-text-recognition-for-lines-and-words)
- [Search incorrectly predicted images](https://rectlabel.com/coreml#search-incorrectly-predicted-images)

# Load Core ML model
- Apple provides [Core ML Models](https://developer.apple.com/machine-learning/models/).
- To convert your ML model to the Core ML format, use [coremltools](https://github.com/apple/coremltools).
- You can convert [YOLOv5](https://github.com/ultralytics/yolov5), [YOLOv8](https://github.com/ultralytics/ultralytics), and [MobileNetV2 + SSDLite](https://machinethink.net/blog/mobilenet-ssdlite-coreml/) models to Core ML models.

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

![coreml](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/9cd87cde-5488-4fe4-b360-30af2dac07ad)

![coreml_polygon](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/acf73fd2-4cdc-498c-ae41-9cf81cb28b9a)

![coreml_pixels](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/aef91eea-1d94-4785-8b2c-dafcd1eed39c)

# Auto text recognition for lines and words
Using [Vision Framework](https://developer.apple.com/documentation/vision), automatic text recognition is performed.
- You can change the language.
- You can change the type to lines or words.

![ocr](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/483bd361-ed04-4f21-bace-5601ad476c91)

# Search incorrectly predicted images
Show training images which predicted labels and boxes are incorrect compared with the current annotations. Such as "Not detected", "Not classified", and "Falsely detected".

![search_incorrectly](https://github.com/user-attachments/assets/7289e936-501a-4a90-a94c-586da4d9bb60)









