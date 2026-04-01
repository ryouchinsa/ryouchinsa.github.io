# [RectLabel](https://rectlabel.com)
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

# How to Train a RF-DETR Object Detection Model with Custom Data

We will show you how to train a [RF-DETR](https://github.com/roboflow/rf-detr) object detection model with your images and annotations and export to a Core ML model which can be used for auto labeling on RectLabel.

We recommend working through this blog post side-by-side with the [RF-DETR Object Detection Colab notebook](https://github.com/ryouchinsa/Rectlabel-support/blob/master/notebooks/train_rf_detr_object_detection_on_custom_dataset.ipynb).

Install RF-DETR.
```
pip install -q rfdetr[train,loggers]==1.6.0
```

Download training images and annotations. You can use these or replace them with your own data.
```
mkdir datasets
cd datasets
wget -q https://huggingface.co/datasets/rectlabel/datasets/resolve/main/converse_vans_detection_coco.zip
unzip -q converse_vans_detection_coco.zip
cd ..
```

Fine-tune RF-DETR on custom dataset. 
```
from rfdetr import RFDETRNano

model = RFDETRNano(num_classes=2)
dataset_dir = "datasets/converse_vans_detection_coco"
model.train(dataset_dir=dataset_dir, epochs=10, batch_size=4, grad_accum_steps=4)
```

The trained model is checkpoint_best_total.pth.
```
ls -la /content/output

total 1956476
drwxr-xr-x 3 root root      4096 Mar 29 15:02 .
drwxr-xr-x 1 root root      4096 Mar 29 14:57 ..
-rw-r--r-- 1 root root 534398511 Mar 29 15:01 checkpoint0009.pth
-rw-r--r-- 1 root root 399873726 Mar 29 15:00 checkpoint_best_ema.pth
-rw-r--r-- 1 root root 401162890 Mar 29 14:59 checkpoint_best_regular.pth
-rw------- 1 root root 133248663 Mar 29 15:01 checkpoint_best_total.pth
-rw-r--r-- 1 root root 534387619 Mar 29 15:01 checkpoint.pth
drwxr-xr-x 2 root root      4096 Mar 29 14:57 eval
-rw-r--r-- 1 root root      4412 Mar 29 15:01 events.out.tfevents.1774796221.326de40b558e.1060.0
-rw-r--r-- 1 root root    111680 Mar 29 15:01 log.txt
-rw-r--r-- 1 root root    196723 Mar 29 15:02 metrics_plot.png
-rw-r--r-- 1 root root       755 Mar 29 15:02 results.json
```

Before exporting to a Core ML model, edit a line of transformer.py.
```
path = "/usr/local/lib/python3.12/dist-packages/rfdetr/models/transformer.py"
with open(path, "r") as f:
    content = f.read()
modified_content = content.replace("mask_flatten, spatial_shapes_hw", "mask_flatten, spatial_shapes")
with open(path, "w") as f:
    f.write(modified_content)
```

Install RF-DETR to CoreML.
```
git clone https://github.com/ryouchinsa/rf-detr-to-coreml.git
cd rf-detr-to-coreml
pip install -q -e .
```

Move the best model to the current folder and export to a Core ML model.
```
mv /content/output/checkpoint_best_total.pth .
python export_coreml.py --model nano --weights checkpoint_best_total.pth

ls -la output

total 12
drwxr-xr-x 3 root root 4096 Mar 29 15:03 .
drwxr-xr-x 7 root root 4096 Mar 29 15:03 ..
drwxr-xr-x 3 root root 4096 Mar 29 15:03 rf-detr-nano-checkpoint_best_total-fp32.mlpackage
```

Now you can auto label using the Core ML model on RectLabel.

