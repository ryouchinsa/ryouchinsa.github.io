# RectLabel
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

Thank you.

# Load Core ML model
Apple provides [Core ML Models](https://developer.apple.com/machine-learning/models/).

To convert your ML model to the Core ML format, use [coremltools](https://github.com/apple/coremltools).

You can convert [YOLOv5](https://github.com/ultralytics/yolov5), [YOLOv8](https://github.com/ultralytics/ultralytics), [MobileNetV2 + SSDLite](https://machinethink.net/blog/mobilenet-ssdlite-coreml/), and [Turi Create](https://apple.github.io/turicreate/docs/userguide/object_detection/export-coreml.html) models to Core ML models.
RectLabel recognizes the model type through the file name and the short description. Such as YOLOv3, YOLOv5, YOLOv8, DeepLab, PoseNet, and FCRN-Depth.

If the output layers are interpreted as [VNRecognizedObjectObservation](https://developer.apple.com/documentation/vision/vnrecognizedobjectobservation), [VNClassificationObservation](https://developer.apple.com/documentation/vision/vnclassificationobservation), and [VNPixelBufferObservation](https://developer.apple.com/documentation/vision/vnpixelbufferobservation), RectLabel can decode the output layers without checking the file name and the short description.

If the Core ML model has 'classes' meta data, RectLabel uses these object names instead of the current objects table.

```
import coremltools
coreml_file = 'DeepLab.mlmodel'
coreml_model = coremltools.models.MLModel(coreml_file)
coreml_model.short_description = "DeepLab"
labels = [
    "background", "aeroplane", "bicycle", "bird", "board", "bottle", "bus", "car", "cat", "chair", "cow", "diningTable", "dog", "horse", "motorbike", "person", "pottedPlant", "sheep", "sofa", "train", "tvOrMonitor"
]
coreml_model.user_defined_metadata['classes'] = ",".join(labels)
coreml_model.save(coreml_file)
```

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

![coreml](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/c6ddc6d7-448e-450f-a4a8-985c301ce7c5)

![coreml_polygon](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/5cd883c8-9205-4121-805c-1b44b91841aa)

![coreml_seg](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/fa3a2092-745f-493d-9446-3f016227c1e0)

# Auto text recognition for lines and words
Using [Vision Framework](https://developer.apple.com/documentation/vision), automatic text recognition is performed.
- You can change the language.
- You can change the type to lines or words.

![ocr](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/3cbf40cd-ece4-451b-b2e8-12ea6e4724c7)








