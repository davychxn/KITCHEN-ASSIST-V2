# KITCHEN-ASSIST-V2

[English](./README.md) | [中文](./README_CN.md)

## Project Overview

Kitchen Assistant V2 is a computer vision project for kitchen cookware detection and classification, featuring YOLO-based object detection and temporal classification models.

## Project Structure

### Documentation
- **`README.md`** - Project documentation (English)
- **`README_CN.md`** - Project documentation (Chinese)
- **`FINE_TUNING_JOURNEY.md`** - Model fine-tuning process documentation (English)
- **`FINE_TUNING_JOURNEY_CN.md`** - Model fine-tuning process documentation (Chinese)

### Models
- **`pan_pot_classifier_temporal.pth`** - Trained PyTorch temporal classification model for pan/pot detection

### Scripts
- **`verify_yolo.py`** - YOLO model verification script
- **`verify_temporal_on_originals.py`** - Temporal model verification on original images

### Directories

#### `yolo_training/`
YOLO model training results and artifacts.
- **`kitchenware_detector/`** - First training run results
  - Training metrics and curves (F1, PR, P, R)
  - Confusion matrices
  - Training batch visualizations
  - Model weights (best.pt, last.pt, epoch checkpoints)
  - Configuration (args.yaml)
- **`kitchenware_detector2/`** - Second training run results
  - Same structure as kitchenware_detector
  - Improved model with more training data

#### `verification_results_on_originals/`
Model verification outputs on original images.
- Marked/annotated images showing detection results
- `verification_results_on_originals.json` - Verification metrics and results
- Categories tested: boiling, on_fire, smoking

## Key Features

- **YOLO Object Detection** - Real-time kitchenware detection using YOLOv8/v11
- **Temporal Classification** - Enhanced classification using temporal information
- **Multi-class Detection** - Detects and classifies various kitchen cookware and states
- **Comprehensive Training Metrics** - Detailed evaluation with F1, Precision, Recall curves
- **Verification Pipeline** - Automated testing on diverse image sets

## Model Performance

### YOLO Detector
See training results in `yolo_training/kitchenware_detector/` and `yolo_training/kitchenware_detector2/`:
- Training curves and metrics
- Confusion matrices
- Validation batch predictions
- Model checkpoints at various epochs

### Temporal Classifier
- Model: `pan_pot_classifier_temporal.pth`
- Verification results: `verification_results_on_originals/`
- Performance metrics in JSON format

## Usage

### Verify YOLO Model
```bash
python verify_yolo.py
```

### Verify Temporal Model
```bash
python verify_temporal_on_originals.py
```

## Documentation

For detailed information about the fine-tuning process:
- English: [FINE_TUNING_JOURNEY.md](FINE_TUNING_JOURNEY.md)
- Chinese: [FINE_TUNING_JOURNEY_CN.md](FINE_TUNING_JOURNEY_CN.md)

## Repository Contents

This repository contains:
- ✅ Trained models (PyTorch weights)
- ✅ Training results and metrics
- ✅ Verification scripts and results
- ✅ Documentation (English & Chinese)

**Note**: Training data, annotation tools (X-AnyLabeling, ChatRex), and utility scripts are not included in version control.

## Requirements

```bash
# Core dependencies
pip install torch torchvision
pip install ultralytics  # For YOLO
pip install opencv-python
pip install numpy pandas matplotlib
```

## License

See individual component licenses for details.