# [RectLabel](https://rectlabel.com)
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

# How to Train a YOLO26 Object Detection Model with Custom Data

We will show you how to train a [YOLO26](https://github.com/ultralytics/ultralytics) detection model with your images and annotations and export to a Core ML model which can be used for auto labeling on RectLabel.

We recommend working through this blog post side-by-side with the [YOLO26 Object Detection Colab notebook](https://colab.research.google.com/github/ryouchinsa/Rectlabel-support/blob/master/notebooks/train_yolo26_object_detection_on_custom_dataset.ipynb
).

Install YOLO26.
```
pip install -q ultralytics
```

Download training images and annotations. You can use these or replace them with your own data.
```
mkdir datasets
cd datasets
wget -q https://huggingface.co/datasets/rectlabel/datasets/resolve/main/converse_vans_detection.zip
unzip -q converse_vans_detection.zip
cd ..
```

Create a workspace folder and start training from the workspace folder. Make sure the datasets path in the yaml file.
```
mkdir workspace
cd workspace
mv ../datasets/converse_vans_detection/converse_vans_detection.yaml .
yolo task=detect mode=train model=yolo26n.pt data=converse_vans_detection.yaml epochs=100 imgsz=640 plots=True
```

Move the best model to the current folder and export to a Core ML model.
```
mv runs/detect/train/weights/best.pt .
yolo export model=best.pt format=coreml
```

Now you can auto label using the Core ML model on RectLabel.

![converse1](https://github.com/user-attachments/assets/36fc83c5-0d36-45b2-99a0-1ab39af20ab6)

![converse2](https://github.com/user-attachments/assets/850e081d-790c-4bfb-8aba-6d43310cf8c5)

![vans1](https://github.com/user-attachments/assets/2246a6bf-bba4-414f-b471-10b47fdbea98)

![vans2](https://github.com/user-attachments/assets/f2cb795a-f0d0-4604-9186-aad1cc0df095)









