
# 🍌 Banana Ripeness Detection using YOLOv8 + Streamlit

This project detects the **ripeness stage of bananas** — *unripe*, *ripe*, and *overripe* — using a custom-trained YOLOv8 model and an interactive Streamlit web app.

---

## 🧠 Project Overview

- **Framework:** [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics)
- **Interface:** [Streamlit](https://streamlit.io/)
- **Dataset:** Collected and annotated via [Roboflow](https://roboflow.com)
- **Goal:** Detect ripeness stages of bananas for automation or quality control systems.

---

## 🧩 Folder Structure

```
BananaRipeness/
├── app.py                             # Streamlit app
├── runs/
│   └── detect/
│       └── banana_safe_run/
│           └── weights/
│               ├── best.pt            # Trained model weights
│               └── last.pt
├── data.yaml                          # YOLO dataset config
├── requirements.txt                   # Dependencies
└── README.md
```

---

## ⚙️ Installation

### 1. Clone this repository
```bash
git clone https://github.com/<your-username>/BananaRipeness.git
cd BananaRipeness
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

> If you don't have a `requirements.txt`, create one:
> ```
> ultralytics
> streamlit
> pillow
> pyngrok
> ```

---

## 🧠 Train Your Own Model (Optional)

If you want to retrain with your dataset:

```python
from ultralytics import YOLO

model = YOLO("yolov8n.pt")
model.train(
    data="path/to/data.yaml",
    epochs=50,
    imgsz=640,
    batch=4,
    name="banana_training",
)
```

Weights will be saved under:
```
runs/detect/banana_training/weights/best.pt
```

---

## 🔍 Run Inference

```python
from ultralytics import YOLO
model = YOLO("runs/detect/banana_safe_run/weights/best.pt")
results = model.predict(source="path/to/image.jpg", show=True)
```

---

## 🖥️ Run Streamlit App

### Local (recommended)
```bash
streamlit run app.py
```
Then open:  
👉 [http://localhost:8501](http://localhost:8501)

### Google Colab or Remote (using ngrok)
```python
from pyngrok import ngrok
import subprocess

port = 8501
ngrok.set_auth_token("YOUR_NGROK_AUTH_TOKEN")
public_url = ngrok.connect(port).public_url
print("App URL:", public_url)
subprocess.Popen(["streamlit", "run", "app.py", "--server.port", str(port)])
```

---

## 🧾 Example Output

| Input Image | Prediction |
|--------------|-------------|
| ![banana](https://i.imgur.com/Fvc2VOB.jpg) | ![result](https://i.imgur.com/mUJPmP2.jpg) |

---

## 🌟 Features
- Real-time banana ripeness detection
- Lightweight YOLOv8n model
- Web interface for easy testing
- Works in Colab via ngrok tunneling

---

## 📦 Deployment Options
- **Streamlit Cloud:** Free and fast way to host apps
- **Hugging Face Spaces:** Great for sharing public demos
- **Local server:** Use `streamlit run app.py`

---

## 🙌 Acknowledgements
- [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics)
- [Roboflow](https://roboflow.com)
- [Streamlit](https://streamlit.io/)

---

### 🧑‍💻 Author
**Priyadharshini M**  
💡 Passionate about Computer Vision, ML, and AI applications in food quality and automation.
