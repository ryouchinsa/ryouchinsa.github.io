# [RectLabel](https://rectlabel.com)
How to use? Read our [Help page](https://rectlabel.com/help/).

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

# ONNX menus
- [Load Cellpose ONNX Model](https://rectlabel.com/onnx#load-cellpose-onnx-model)

# Load Cellpose ONNX Model
Read [Cellpose CPP Wrapper for macOS and Ubuntu GPU](https://github.com/ryouchinsa/cellpose-cpp).

Select a model.
- [cyto3.onnx](https://huggingface.co/rectlabel/cellpose/resolve/main/cyto3.onnx.zip)
- [cpsam.onnx](https://huggingface.co/rectlabel/cellpose/resolve/main/cpsam.onnx.zip)

Select a create type.
- polygon
- pixels

Create using Cellpose.
- The first channel is for the cytoplasm and the second channel is for the nuclear.
- Increase the diameter to detect larger cells, decrease the diameter to detect smaller cells.
- Increase the flow threshold to increase the number of detections.
- Increase the min size not to detect cells which are less than the min size.
- Press start button to start downloading the model and processing the image.

View menu.
- "Show depth image" to show the Cellpose.

<video src="https://github.com/user-attachments/assets/22048c89-2412-43e3-9c0d-d0e12134ded5" controls="controls" muted="muted" class="width-fit" style="max-height:640px; min-height: 200px"></video>












