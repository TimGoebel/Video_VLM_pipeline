# Vision-Language Model for Video Action Analysis 

This project is a **Streamlit-based AI Assistant** that allows users to **analyze video frames, detect actions, and extract meaningful insights** using OpenAI's GPT-4 Turbo.

---

## 📌 Features
- **Parallel Processing**: Uses `ThreadPoolExecutor` to analyze multiple frames concurrently.
- **GPU Acceleration**: Leverages OpenCV’s `cuda` backend for faster frame decoding (if supported).
- **Frame Extraction**: Extracts frames from a video at a user-defined interval.
- **AI-Powered Action Detection**: Uses GPT-4 Turbo to analyze and describe actions in frames.
- **Keyword-Based Filtering**: Filters frames based on user-defined keywords.
- **Timestamped Results**: Each frame includes a **timestamp** (HH:MM:SS format) for accuracy.
- **Downloadable Reports**: Save results as **CSV** and **PDF** for later use.
- **Secure API Access**: Requires an **OpenAI API Key** to ensure authorized usage.

---

## 🏗️ Project Structure
```
📁 video-action-analysis
│── 📄 main.py                # Streamlit app entry point
│── 📁 vlm_video
│   │── 📄 vlm_video.py       # Video processing & analysis module
│── 📁 utils
│   │── 📄 utils.py           # Utility functions
│── 📄 requirements.txt       # Dependencies
│── 📄 README.md              # Project documentation
```

---

## Installation
### **1️⃣ Clone the Repository**
```sh
git clone https://github.com/TimGoebel/Video_VLM_pipeline.git
cd video-action-analysis
```

### **2️⃣ Install Dependencies**
```sh
pip install -r requirements.txt
```

---

## Running the App
Run the Streamlit app with:
```sh
streamlit run main.py
```

or use **run.bat** (for Windows users):
```
@echo off
python -m streamlit run main.py
pause  # Remove this if you don't want the CMD screen to stay open for troubleshooting
```

---

## How to Use

1️⃣ **Run the app** using Streamlit.  
2️⃣ **Enter your OpenAI API key** in the sidebar.  
3️⃣ **Select GPT-4 Turbo** as the model.  
4️⃣ **Upload a video** file.  
5️⃣ **Set frame extraction interval.**  
6️⃣ **Enable GPU acceleration (if supported).**  
7️⃣ **Enter a keyword** to filter relevant actions.  
8️⃣ **Analyze video** and view detected actions.  
9️⃣ **Download results** in CSV, PDF, or annotated video format.  
🔟 **Clear all stored session data only when explicitly requested.**  

---

## How They Work Together

✅ **Example 1: Fast Analysis, Sparse Frames**
- `frame_interval = 60` (1 frame every 2 seconds)
- `sequence_length = 5` (5-frame sequences analyzed together)
- **Effect:** The model will analyze sequences of frames spanning **10 seconds** of video at a time.

✅ **Example 2: Dense Analysis, Short Sequences**
- `frame_interval = 10` (1 frame every 0.3 seconds)
- `sequence_length = 3` (3-frame sequences analyzed together)
- **Effect:** The model gets finer details but still uses short-term context.

✅ **Example 3: Comprehensive Motion Analysis**
- `frame_interval = 30` (1 frame per second)
- `sequence_length = 7` (7-frame sequences analyzed together)
- **Effect:** The AI observes motion over **7 seconds**, improving its ability to detect continuous actions (e.g., someone getting up from a chair or throwing an object).

✅ **Keyword-Based Filtering**
- **Purpose:** Allows users to specify a keyword for filtering detected actions.
- **Effect:** The model will only retain and display results containing the specified keyword.
- **Example:** If the keyword is `"running"`, only frames where `"running"` is detected will be displayed in the results.
- **Use Case:** Helps in refining search results when looking for specific actions in large video datasets.

---

## Performance Optimization
### **Parallel Frame Processing**
- Extracts frames concurrently using `ThreadPoolExecutor`.
- Reduces analysis time by parallelizing GPT-4 Turbo calls.

### **GPU Acceleration with OpenCV CUDA**
- Uses CUDA (`cv2.cuda_GpuMat`) for **faster frame decoding**.
- Falls back to CPU if CUDA is unavailable.

---

## Future Enhancements
🚀 **YOLO Object Detection** - Adding YOLO-based bounding box detection.  
📊 **Visualization Dashboards** - Graph-based analytics of detected actions.  
🎭 **Pose Estimation** - Tracking human movement using **MediaPipe/OpenPose**.  

---

## 📜 License
This project is licensed under the **MIT License**.

---
