# [RectLabel](https://rectlabel.com)
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

# How to Train a YOLO26 Classification Model with Custom Data

We will show you how to train a [YOLO26](https://github.com/ultralytics/ultralytics) classification model with your images and annotations and export to a Core ML model which can be used for auto labeling on RectLabel.

We recommend working through this blog post side-by-side with the [YOLO26 Object Classification Colab notebook](https://colab.research.google.com/github/ryouchinsa/Rectlabel-support/blob/master/notebooks/train_yolo26_classification_on_custom_dataset.ipynb).

Install YOLO26.
```
pip install -q ultralytics
```

Download training images and annotations. You can use these or replace them with your own data.
```
wget -q https://huggingface.co/datasets/rectlabel/datasets/resolve/main/converse_vans_classification.zip
unzip -q converse_vans_classification.zip
```

Fine-tune YOLO26 on custom dataset.
```
yolo classify train data=converse_vans_classification model=yolo26n-cls.pt epochs=100
```

Move the best model to the current folder and export to a Core ML model.
```
mv runs/classify/train/weights/best.pt .
yolo export model=best.pt format=coreml
```

Now you can auto label using the Core ML model on RectLabel.

![converse1](https://github.com/user-attachments/assets/657d6d1d-c090-454c-bba6-b364f465cd7c)

![converse2](https://github.com/user-attachments/assets/4b03edf4-9488-4284-9441-b15e9c847399)

![vans1](https://github.com/user-attachments/assets/e4b06774-024f-4518-a26e-ca50409c0346)

![vans2](https://github.com/user-attachments/assets/7ed1ff7a-af05-4655-8e8f-3dadf88d8863)









