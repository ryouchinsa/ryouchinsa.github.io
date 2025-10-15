# [RectLabel](https://rectlabel.com)
An offline image annotation tool for object detection and segmentation.

To download RectLabel apps.
- [RectLabel](https://apps.apple.com/app/id1210181730)
- [RectLabel Pro](https://apps.apple.com/app/id1490990105)

Post the problem to our [Github issues](https://github.com/ryouchinsa/Rectlabel-support/issues).

Have questions? Send an email to support@rectlabel.com.

# ONNX menus
- [Create polygon using Cellpose](https://rectlabel.com/onnx#create-polygon-using-cellpose)

# Create polygon using Cellpose
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
- "Focus box" to quick zoom to the selected polygon/pixels.
- "Hide other boxes" to hide other polygons.
- "Hide pixels" to toggle pixels alpha.
- "Show small pixels" to show small pixels areas.
- "Show other pixels" to show other pixels objects.
- "Show indexes on labels table" to show each row number on the labels table.
- "Show checkboxes on labels table" to show a checkbox to show/hide for each row on the labels table.
- "Show depth image" to show the predicted Cellpose.

<video src="https://github.com/user-attachments/assets/22048c89-2412-43e3-9c0d-d0e12134ded5" controls="controls" muted="muted" class="width-fit" style="max-height:640px; min-height: 200px"></video>












