# BCS407_Project

Using YOLOv8 and Roboflow to detect Campus Safety Monitoring equipment on premises

## Classes Detected
- Wet Floor Signs
- Fire Alarms
- Emergency Exits
- Industrial Safety Helmets

## Results
| Version | Author | Classes | mAP@0.50 | Precision | Recall |
|---|---|---|---|---|---|
| Original | Suhail Sameer | 7 | 81.0% | 78.8% | 84.5% |
| Consolidated | Mohammad Abdullah | 4 | 96.8% | 96.2% | 94.3% |

## Run on Google Colab (Recommended)
1. Open the notebook in Google Colab
2. Go to `Runtime > Change runtime type > GPU (T4)`
3. Replace `YOUR_API_KEY_HERE` with your Roboflow API key
4. Run all cells

## Run Locally (Windows)
1. Create and activate a virtual environment:
```bash
python -m venv .venv
& .venv\Scripts\Activate.ps1
```
2. Install dependencies:
```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

## Credits
- Original repository, dataset collection and training script: [Suhail Sameer](https://github.com/suhailsameer) — [Original Repo](https://github.com/suhailsameer/BCS407_Project)
- Dataset consolidation, class merging and model retraining: Mohammad Abdullah
- Course: BCS407 – Artificial Intelligence, Canadian University Dubai
