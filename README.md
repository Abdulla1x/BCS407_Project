# AI-Based Smart Campus Safety Detection System

Using **YOLOv8** and **Roboflow** to detect safety-critical objects on campus in real time.
Trained on a custom dataset collected at Canadian University Dubai across 4 object classes.

**Course:** BCS407 – Artificial Intelligence | Canadian University Dubai
**Dataset:** [Roboflow v1](https://universe.roboflow.com/mohammads-workspace-ervg9/bcs_407-project-aui6o/1) (baseline) | [Roboflow v2](https://universe.roboflow.com/mohammads-workspace-ervg9/bcs_407-project-aui6o/2) (expanded Exit class)
**Model Weights:** [Google Drive](https://drive.google.com/drive/folders/1doXgtP_-K0IdJHfnvPcF5FNrX51GexfQ?usp=sharing) — see `exp2_hyperparam/weights/best.pt` for the best-performing model (Experiment 2)

---

## Classes Detected
- Fire Alarms
- Wet Floor Signs
- Emergency Exits
- Industrial Safety Helmets

---

## Results

### Part 1 — Baseline (Validation Set)

| Version | Classes | mAP@0.50 | Precision | Recall |
|---|---|---|---|---|
| Original (7 sub-classes) | 7 | 81.0% | 78.8% | 84.5% |
| Consolidated (Exit class merged) | 4 | **96.8%** | 96.2% | 94.3% |

### Part 2 — Improvement Experiments (Held-Out Test Set)

| Run | Change | Epochs | mAP@0.50 | mAP@0.50:0.95 | Precision | Recall |
|---|---|---|---|---|---|---|
| Baseline | YOLOv8s, original dataset | 50 | 92.96% | 66.91% | 96.17% | 94.25% |
| Exp 1 | YOLOv8m backbone | 50 | 92.45% | 66.47% | 89.83% | 92.50% |
| Exp 2 | YOLOv8s + tuned hyperparameters | 75 | **94.52%** | **69.82%** | 93.83% | 91.67% |
| Exp 3 | YOLOv8s + expanded Exit data | 50 | 92.36% | 67.28% | 91.26% | 92.23% |
| Final Combined | YOLOv8m + tuned HP + expanded data | 75 | 92.14% | 69.39% | 91.78% | 92.65% |

**Best single strategy:** Experiment 2 (hyperparameter tuning). Lower learning rate, higher weight decay, and extended warmup produced the best mAP and tightest bounding boxes — outperforming backbone scaling with no added inference cost.

---

## Dataset

| Split | Images |
|---|---|
| Train | 1,797 |
| Validation | 207 |
| Test | 207 |
| **Total** | **2,211** |

- v1 (2,069 images): original consolidated dataset used for Part 1 and baseline
- v2 (2,211 images): Exit class expanded from 494 to 637 annotations, used for Experiment 3
- Preprocessing: auto-orientation + resize to 640×640
- Augmentation: HSV jitter, horizontal/vertical flip, mosaic, mixup (applied during training)

---

## Notebooks

| File | Description |
|---|---|
| `BCS407_YOLOv8_Training.ipynb` | Part 1 — Suhail's original baseline, 7 sub-classes, no consolidation |
| `BCS407_YOLOv8_Training_Mohammad.ipynb` | Part 1 — class consolidation, merging, and model retraining (4 classes) |
| `BCS407_Part2_Experiments.ipynb` | Part 2 — all 3 experiments + final combined model |

---

## Run on Google Colab (Recommended)

1. Open the relevant notebook in Google Colab
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

---

## Credits
- Original repository, dataset collection and training script: [Suhail Sameer](https://github.com/suhailsameer) — [Original Repo](https://github.com/suhailsameer/BCS407_Project)
- Class consolidation, model retraining, dataset expansion, and all Part 2 experiments: Mohammad Abdullah
- Course: BCS407 – Artificial Intelligence, Canadian University Dubai
