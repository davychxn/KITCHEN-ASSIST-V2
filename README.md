# KITCHEN-ASSIST-V2

## Frame Extraction Tool

### Description
This tool iterates through all subfolders of a parent directory, finds MP4 files, and extracts 3 continuous frames from random positions in each video.

### Prerequisites
```bash
pip install opencv-python
```

### Usage

1. Configure the parent folder in `extract_frames.py` (line 7):
   ```python
   parent_folder = r"D:\delete2025\20251205_patent_abnormal\20260106_pics"
   ```

2. Run the script:
   ```bash
   python extract_frames.py
   ```

3. The script will:
   - Iterate through all subfolders in the parent directory
   - Find all MP4 files in each subfolder
   - Create a `pics` subfolder within each folder containing MP4 files
   - Extract frames and save them to the respective `pics` subfolder

### Output Format
- Files are named: `{subfolder_name}_{mp4_index}_{frame_number}.jpg`
- Example: `frying-pan_boiling_1_1.jpg`, `frying-pan_boiling_1_2.jpg`, `frying-pan_boiling_1_3.jpg`
- Existing pictures will be replaced if they already exist
- Each subfolder gets its own `pics` folder with extracted frames

### Features
- Automatically iterates through all subfolders
- Creates `pics` subfolder within each source folder (not in the script location)
- Randomly selects starting position in each video
- Extracts 3 consecutive frames from the selected position
- Processes all MP4 files in each subfolder
- Names output files based on subfolder name, video index, and frame sequence

---

## Environment Setup

### Python Environment
- **Environment Name**: `x-anylabeling-upn`
- **Python Version**: 3.9.25
- **CUDA Version**: 12.4
- **GPU**: NVIDIA GeForce RTX 4060 Ti (8GB)

### Activate Environment
```powershell
conda activate x-anylabeling-upn
```

## Installed Components

### 1. ChatRex
Universal Proposal Network for object detection and segmentation.

**Installation Location**: `ChatRex/`

**Installed Packages**:
- `chatrex` (v1.0) - Main package
- `MultiScaleDeformableAttention` (v1.0) - Deformable attention ops

**Note**: Currently installed without CUDA extensions (Python packages only).

### 2. X-AnyLabeling
Advanced annotation tool with AI-powered auto-labeling capabilities.

**Installation Location**: `X-AnyLabeling/`

**Version**: 3.3.4

## X-AnyLabeling Usage

### Launch GUI
```powershell
cd X-AnyLabeling
C:\Users\cndv3\miniconda3\envs\x-anylabeling-upn\python.exe -m anylabeling.app
```

### System Information
```powershell
C:\Users\cndv3\miniconda3\envs\x-anylabeling-upn\python.exe -m anylabeling.app checks
```

### Version Information
```powershell
C:\Users\cndv3\miniconda3\envs\x-anylabeling-upn\python.exe -m anylabeling.app version
```

### Show Config Path
```powershell
C:\Users\cndv3\miniconda3\envs\x-anylabeling-upn\python.exe -m anylabeling.app config
```

### Convert Annotations
```powershell
# See conversion options
C:\Users\cndv3\miniconda3\envs\x-anylabeling-upn\python.exe -m anylabeling.app convert --help

# Example: Convert to YOLO format
C:\Users\cndv3\miniconda3\envs\x-anylabeling-upn\python.exe -m anylabeling.app convert --input-format json --output-format yolo --input-dir ./images --output-dir ./labels
```

### Open Specific Image/Folder
```powershell
# Open a specific image
C:\Users\cndv3\miniconda3\envs\x-anylabeling-upn\python.exe -m anylabeling.app --filename "path/to/image.jpg"

# Open a folder
C:\Users\cndv3\miniconda3\envs\x-anylabeling-upn\python.exe -m anylabeling.app --filename "path/to/folder"
```

### Auto-save Mode
```powershell
C:\Users\cndv3\miniconda3\envs\x-anylabeling-upn\python.exe -m anylabeling.app --autosave
```

### Custom Config
```powershell
C:\Users\cndv3\miniconda3\envs\x-anylabeling-upn\python.exe -m anylabeling.app --config path/to/config.yaml
```

### Available Arguments
```
--reset-config              Reset Qt config
--logger-level              Set logger level (debug/info/warning/fatal/error)
--no-auto-update-check      Disable automatic update check
--filename [FILENAME]       Image or label filename (or directory path)
--output OUTPUT             Output file or directory
--config CONFIG             Config file or yaml-format string
--nodata                    Stop storing image data to JSON file
--autosave                  Auto save
--nosortlabels             Stop sorting labels
--labels LABELS             Comma separated list of labels or file containing labels
--keep-prev                Keep annotation of previous frame
--epsilon EPSILON          Epsilon to find nearest vertex on canvas
```

## Creating a Shortcut (Optional)

### PowerShell Alias
Add to your PowerShell profile (`$PROFILE`):

```powershell
function xanylabeling {
    C:\Users\cndv3\miniconda3\envs\x-anylabeling-upn\python.exe -m anylabeling.app $args
}
```

Reload profile:
```powershell
. $PROFILE
```

Usage:
```powershell
xanylabeling checks
xanylabeling version
xanylabeling --filename "image.jpg"
```

### Batch File
Create `xanylabeling.bat` in a folder that's in your PATH:

```batch
@echo off
C:\Users\cndv3\miniconda3\envs\x-anylabeling-upn\python.exe -m anylabeling.app %*
```

## Common Tasks

### Annotating Images
1. Launch X-AnyLabeling GUI
2. Load images: **File → Open Dir**
3. Select AI model: **Model → Load Model**
4. Use auto-labeling features
5. Save annotations: **File → Save**

### Supported AI Models
X-AnyLabeling supports:
- **Object Detection**: YOLOv5/8/11, RT-DETR, YOLO-World, etc.
- **Segmentation**: SAM, SAM2, SAM3, YOLOv8-Seg
- **Pose Estimation**: YOLOv8-Pose, DWPose, RTMO
- **OCR**: PP-OCRv4/v5
- **Grounding**: Grounding DINO, YOLO-World, YOLOE
- **Vision Language**: Florence2, Qwen3-VL, Gemini, ChatGPT
- **And many more** (see [model_zoo](X-AnyLabeling/docs/en/model_zoo.md))

### Supported Annotation Formats
- **Import/Export**: COCO, VOC, YOLO, DOTA, MOT, MASK, PPOCR, MMGD, VLM-R1
- **Annotation Types**: Polygons, rectangles, rotated boxes, circles, lines, points
- **Special**: Text detection, recognition, and KIE annotations

## System Status
✅ Windows 10/11  
✅ Python 3.9.25  
✅ CUDA 12.4  
✅ GPU Support (RTX 4060 Ti - 8GB)  
✅ 48GB RAM  
✅ All dependencies installed  

## Documentation
- **X-AnyLabeling Docs**: [X-AnyLabeling/docs/en/](X-AnyLabeling/docs/en/)
  - [Installation & Quickstart](X-AnyLabeling/docs/en/get_started.md)
  - [User Guide](X-AnyLabeling/docs/en/user_guide.md)
  - [CLI Guide](X-AnyLabeling/docs/en/cli.md)
  - [Custom Model](X-AnyLabeling/docs/en/custom_model.md)
  - [Model Zoo](X-AnyLabeling/docs/en/model_zoo.md)
- **ChatRex Docs**: [ChatRex/README.md](ChatRex/README.md)

## Troubleshooting

### GUI doesn't start
Check dependencies:
```powershell
C:\Users\cndv3\miniconda3\envs\x-anylabeling-upn\python.exe -m anylabeling.app checks
```

### Models don't load
Verify GPU is detected and ONNX Runtime GPU is installed:
```powershell
C:\Users\cndv3\miniconda3\envs\x-anylabeling-upn\python.exe -c "import onnxruntime as ort; print(ort.get_available_providers())"
```

Expected output: `['CUDAExecutionProvider', 'CPUExecutionProvider']`

### Check package conflicts
```powershell
C:\Users\cndv3\miniconda3\envs\x-anylabeling-upn\python.exe -m pip check
```