# [RectLabel](https://rectlabel.com)
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

# How to Train a YOLO26 Instance Segmentation Model with Custom Data

We will show you how to train a [YOLO26](https://github.com/ultralytics/ultralytics) instance segmentation model with your images and annotations and export to a Core ML model which can be used for auto labeling on RectLabel.

We recommend working through this blog post side-by-side with the [YOLO26 Instance Segmentation Colab notebook](https://colab.research.google.com/github/ryouchinsa/Rectlabel-support/blob/master/notebooks/train_yolo26_object_detection_on_custom_dataset.ipynb
).

Install YOLO26.
```
pip install -q ultralytics
```

Download training images and annotations. You can use these or replace them with your own data.
```
mkdir datasets
cd datasets
wget -q https://huggingface.co/datasets/rectlabel/datasets/resolve/main/segment.zip
unzip -q segment.zip
cd ..
```

Create a workspace folder and start training from the workspace folder. Make sure the datasets path in the yaml file.
```
mkdir workspace
cd workspace
mv ../datasets/segment/segment.yaml .
yolo segment train data=segment.yaml model=yolo26m-seg.pt epochs=100
```

Move the best model to the current folder and export to a Core ML model.
```
mv runs/segment/train/weights/best.pt .
yolo export model=best.pt format=coreml
```

Now you can auto label using the Core ML model on RectLabel.




