# Foyer models

The model files Foyer's faces worker runs (decision 0065 in the Foyer repository), converted to ONNX. They're published here as release assets so the worker's image can download them; the worker checks each file's SHA-256 before loading it.

## Files (release `faces-1`)

| File | Size | SHA-256 | Made from | Licence |
|---|---|---|---|---|
| `yolov5m-face.onnx` | 88,302,370 bytes | `cdb57a6f9c8f61a59e169c30883e66d87d7d9afaeb8508200cb2cbc523a08ebb` | [deepcam-cn/yolov5-face](https://github.com/deepcam-cn/yolov5-face) at `152c688`, its `yolov5m-face.pt` weights | GPL-3.0, as the original |
| `adaface-ir101-webface12m.onnx` | 260,696,317 bytes | `cf09d54e6efcb97c464bd2227dbe178a98c793c2a9bd8ea749821c1d40917553` | [mk-minchul/AdaFace](https://github.com/mk-minchul/AdaFace) at `c60eaa7`, its IR-101 checkpoint trained on WebFace12M (backbone only) | MIT, as the original |

- **YOLOv5-face** finds faces and their five landmarks. Its source, including the code to train and export it, is the original repository above, under GPL-3.0; these weights are the original authors', unchanged apart from the conversion to ONNX.
- **AdaFace** turns a lined-up face into 512 values for recognition.

## How they're made

With the Foyer repository's `models/convert.sh`, which pins both repositories by commit and the original weights by SHA-256, reads the checkpoints with PyTorch's safe loader, and checks AdaFace's ONNX output against PyTorch's.

Both models were trained by their authors on public research datasets. See each original repository for details.
