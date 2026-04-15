# BCS407_Project
Using YOLOv8 and Roboflow to detect Campus Safety Monitoring equipment on premises
## Run Locally (Windows)

1. Create and activate a virtual environment:

```powershell
python -m venv .venv
& .venv\Scripts\Activate.ps1
```

2. Install dependencies:

```powershell
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

If you don't have `requirements.txt`, install these packages:

```powershell
python -m pip install ultralytics roboflow notebook jupyterlab opencv-python matplotlib pyyaml pillow
```

3. Start Jupyter Notebook and open the training notebook:

```powershell
& .venv\Scripts\Activate.ps1
jupyter notebook BCS407_YOLOv8_Training.ipynb
```

## Notes & Changes for Local Use
- The notebook has been updated to replace Google Colab-specific calls (Drive mount, `!` shell commands, `files.upload`) with local equivalents.
- Save directory: `BCS407_SafetyDetection` (created in the notebook working directory).
- Training outputs and runs are saved under `runs/detect/campus_safety_yolov8s` by default.
- Device detection: the notebook will use GPU (if available) or CPU automatically.

## Roboflow Dataset
The notebook still expects you to provide your Roboflow API key and project details in the dataset download cell. Replace the placeholders with your values to download the dataset.

## Helpful Commands
- Activate venv: `& .venv\Scripts\Activate.ps1`
- Install packages: `python -m pip install -r requirements.txt`
- Run notebook: `jupyter notebook BCS407_YOLOv8_Training.ipynb`

If you'd like, I can add a `requirements.txt` and a short LICENSE or more detailed README sections (usage examples, dataset notes).
