# 🤟 Sign Language MNIST — ASL Recognition

**Antonine University | Faculty of Engineering and Technology**  
**Authors:** Paul Riachy & Marita Tannoury  
**Supervisor:** Dr. Rina Bitar

---

## Overview

End-to-end machine-learning project that trains four models (SVM, Random Forest, CNN, LSTM)
on the [Sign Language MNIST](https://www.kaggle.com/datasets/datamunge/sign-language-mnist)
dataset to classify American Sign Language hand signs (letters A–Z, excluding J & Z which
require motion).

The project includes:
- **Automatic Kaggle dataset download** — no manual CSV uploads needed
- **Live webcam prediction** via OpenCV (local) or JavaScript (Google Colab)
- Full preprocessing pipeline with auto-inversion correction and morphological cleanup
- Model checkpointing and saved weights

---

## Results (expected)

| Model | Accuracy | Weighted F1 |
|---|---|---|
| SVM (RBF, PCA-100) | ~79% | ~79% |
| Random Forest (200 trees) | ~74% | ~74% |
| CNN (custom) | **~97%** | **~97%** |
| LSTM | ~87% | ~87% |

---

## Quick Start

### Option A — Google Colab (recommended)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_USERNAME/sign-language-asl/blob/main/notebooks/Sign_Language_MNIST_AI_Project.ipynb)

1. Click the badge above.
2. Go to `Runtime → Run all`.
3. When prompted, upload your `kaggle.json` (see below).

### Option B — Local Jupyter

```bash
# 1. Clone
git clone https://github.com/YOUR_USERNAME/sign-language-asl.git
cd sign-language-asl

# 2. Create environment
python -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Place Kaggle credentials
mkdir -p ~/.kaggle
cp /path/to/your/kaggle.json ~/.kaggle/
chmod 600 ~/.kaggle/kaggle.json    # Linux/macOS only

# 5. Launch notebook
jupyter notebook notebooks/Sign_Language_MNIST_AI_Project.ipynb
```

---

## Getting a Kaggle API Token

1. Log in to [kaggle.com](https://www.kaggle.com)
2. Go to **Account → Settings → API → Create New Token**
3. A `kaggle.json` file will download — keep it private!

```json
{"username":"your_username","key":"your_api_key"}
```

> ⚠️ Never commit `kaggle.json` to Git — it is already in `.gitignore`.

---

## Project Structure

```
sign-language-asl/
├── notebooks/
│   └── Sign_Language_MNIST_AI_Project.ipynb   ← main notebook
├── models/                                     ← saved models (git-ignored)
├── data/                                       ← downloaded CSVs (git-ignored)
├── images/                                     ← test hand-sign photos (local mode)
├── requirements.txt
├── .gitignore
└── README.md
```

---

## Live Camera Feature

| Environment | How it works |
|---|---|
| **Google Colab** | Section 7A opens your browser camera via JavaScript, captures a frame, runs inference |
| **Local Jupyter** | Section 7B opens an OpenCV window with **real-time** per-frame prediction overlay |
| **Anywhere** | Section 7C lets you upload any image file for inference |

### Tips for best results
- Use a **plain, light background** (white wall is ideal)
- Keep your hand **centered** in the green guide box
- Ensure **even lighting** — avoid harsh shadows
- J and Z are excluded from the dataset (they require motion)

---

## Dependencies

See `requirements.txt`. Core packages:

| Package | Purpose |
|---|---|
| `tensorflow` | CNN / LSTM training |
| `scikit-learn` | SVM, Random Forest, PCA, metrics |
| `kaggle` | Auto dataset download |
| `opencv-python` | Live camera & image preprocessing |
| `pandas` / `numpy` | Data handling |
| `matplotlib` / `seaborn` | Visualisations |

---

## License

MIT — see [LICENSE](LICENSE).
