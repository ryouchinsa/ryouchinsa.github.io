# [RectLabel](https://rectlabel.com)
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

Thank you.

# Label polygons with holes using Segment Anything models
Open your images and annotations folders. If you do not have, [download donuts dataset](https://huggingface.co/datasets/rectlabel/datasets/resolve/main/donuts.zip).

- Edit menu -> Create polygon using SAM.
- Select a model, create polygon, and press the start button.
- After preprocessing the image, click positive points and negative points.
- Press enter key to finish drawing the polygon, and select the object name.

<video src="https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/506d5404-69c2-440d-9b3f-ddef52e8737e" controls="controls" muted="muted" class="width-fit" style="max-height:640px; min-height: 200px"></video>

After labeling all images, Export menu -> Export COCO JSON file.

![スクリーンショット 2024-05-05 0 28 45](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/2f4245ca-6110-4a5f-90eb-5823d09d4cf1)

Using [this script](https://github.com/ryouchinsa/Rectlabel-support/blob/master/pycocoDemo.py), you can visualize the exported COCO file.
- To train a Mask R-CNN model, read [Train Detectron2 models on Ubuntu 22.04](https://rectlabel.com/detectron2).

![スクリーンショット 2024-05-03 18 45 46](https://github.com/ryouchinsa/ryouchinsa.github.io/assets/1954306/94b22646-a816-4dcc-95a4-1f187b50e6f7)


