**English** | [简体中文](README.zh-CN.md)

# YOLOv8 X-ray Item Detection

A coursework demonstration with annotation conversion, YOLOv8 training/validation, a PyQt5 review interface, and spreadsheet export of detection results.

**Category:** Artificial Intelligence · Computer Vision  
**Stack:** Python · PyTorch · Ultralytics · OpenCV · PyQt5

## Components

| Path | Purpose |
| --- | --- |
| `data_processing.py` | Convert annotations and write dataset YAML |
| `train.py` | Train/validate a YOLO model and run experiment/export sections |
| `x_ray_windows.py` | Image selection, visualization, and Excel export |
| `download_models.py`, `pre_train_models/` | Pretrained-model preparation |
| `trained_models/xray_detection_v1/` | Historical configuration, plots, results, and weights |
| `requirements.txt` | Historical environment snapshot |

The eight conversion labels are `Mobile_Phone`, `Cosmetic`, `Portable_Charger_1`, `Portable_Charger_2`, `Nonmetallic_Lighter`, `Water`, `Tablet`, and `Laptop`. These are dataset categories, not a complete definition of dangerous goods.

## Setup

Create and activate an isolated environment, review package pins for your platform, and run:

```bash
python -m pip install -r requirements.txt
```

Choose a compatible PyTorch/CUDA build if using GPU acceleration.

## Prepare data and train

Set `data_path` and `yolo_dataset_path` in `data_processing.py`; they currently contain local Windows paths. Confirm source layout and the generated `yolo_dataset/xray_data.yaml`.

The converter assigns its test-image directory as the YAML `val` split. Prepare a separate untouched test set before reporting final generalization results.

```bash
python data_processing.py
python train.py
```

Training loads `pre_train_models/yolov8n.pt` and writes to `trained_models/xray_detection_v1/`. Inspect the remaining prediction/export sections before executing the full script.

## Launch the interface

Replace the absolute checkpoint path in `x_ray_windows.py` with your compatible trained model, normally `trained_models/xray_detection_v1/weights/best.pt`. Run from the repository root:

```bash
python x_ray_windows.py
```

Inspect image detections and save results as `detection_results.xlsx` in the interface's local history directory.

## Limitations

Data must be prepared separately. Stored plots/checkpoint names do not establish a new evaluation. This is an educational demo, not an independently validated screening system. Export options depend on the installed framework and target environment. Data, weights, and upstream code retain separate licensing terms.

## Author and license

Author / maintainer: [https://github.com/OOOHGOD](https://github.com/OOOHGOD).

Eligible original contributions are under the [MIT License](LICENSE), permitting commercial use and modification with preservation of copyright and license notices in copies or substantial portions. [License scope](LICENSE_SCOPE.md) explains third-party exclusions and upstream terms.
