# Freshness Detection for Fruits and Vegetables

A deep learning-based automated solution to detect and filter out rotten fruits and vegetables at the warehouse level. This project leverages **YOLOv8** object detection model to ensure that only fresh produce is delivered to customers, preventing spoiled or subpar items from reaching end consumers.

## 📋 Project Overview

This system provides **two modes of detection**:
- **Live Feed Detection**: Real-time detection via webcam stream
- **Image Detection**: Batch detection from uploaded images

The project uses publicly available data from Roboflow for model training and is designed to be scalable and customizable for various produce types.

### Key Objective
Automated quality assurance at warehouse level to reduce manual inspection time and improve delivery quality for QuickCommerce platforms.

## Features
- **Real-Time Detection**: Use live webcam feed to detect rotten products in real-time.
- **Image Detection**: Upload images to quickly detect rotten fruits or vegetables.
- **YOLO Model**: Leverages YOLOv8 model for object detection.
- **Scalable**: Can be expanded to include more types of produce and different detection models.
- **Customizable**: Allows for fine-tuning and deployment of different models for higher accuracy.

## 🔧 Installation & Setup

### Prerequisites
- Python 3.8 or higher
- pip (Python package manager)
- Webcam (for live feed detection)
- Internet connection (for Roboflow API)

### Step-by-Step Installation

#### 1. Clone the Repository
```bash
git clone https://github.com/Ganesh-10r/Freshness-Detection-of-Fruits-and-Vegetables-.git
cd Freshness-Detection-of-Fruits-and-Vegetables-
```

#### 2. Create Virtual Environment
**On Windows:**
```bash
python -m venv venv
.\venv\Scripts\activate
```

**On macOS/Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
```

#### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

#### 4. API Configuration
The project uses **Roboflow API** for model inference:
- API key is embedded in `app.py` (consider moving to environment variables for production)
- Ensure you have internet connectivity for API calls

#### 5. Run the Application
```bash
python app.py
```
The Flask server will start at **http://localhost:5000/**
Open this URL in your web browser to access the application.

## 📱 Usage

### Method 1: Web Interface (Recommended)
```bash
python app.py
```
Navigate to **http://localhost:5000** and use the GUI to:
- Upload single or multiple images
- Access live webcam feed
- View detection results with bounding boxes and confidence scores

### Method 2: Live Feed Detection
```bash
python FreshnessDetection_live.py
```
- Opens webcam stream for real-time detection
- Displays bounding boxes and labels on detected rotten produce
- Press **'q'** to exit

### Method 3: Image Detection
```bash
python FreshnessDetection_image.py
```📁 Project Structure

```
├── app.py                          # Main Flask application & web interface
├── FreshnessDetection_live.py     # Real-time webcam detection module
├── FreshnessDetection_image.py    # Image-based detection module
├── requirements.txt                # Python dependencies
├── static/
│   └── uploads/                    # Uploaded images & results storage
├── templates/
│   ├── index.html                 # Home/upload interface
│   ├── live_feed.html             # Live feed display
│   └── result.html                # Detection results page
├── test_image/                     # Sample test images
└── README.md                       # This file
```

## 🤖 Model & Data

### Detection Model
- **Architecture**: YOLOv8 (You Only Look Once v8)
- *⚙️ Configuration

### API Key Management
The Roboflow API key is currently embedded in the code. For production:
```python
# Create a .env file
ROBOFLOW_API_KEY=your_api_key_here
```

### Model Parameters (app.py)
```python
model.predict(
    image, 
    confidence=40,  # Confidence threshold (0-100)
    overlap=30      # NMS overlap threshold (0-100)
)
```

**Tuning Tips:**
- **Increase confidence** → Fewer false positives (stricter)
- **Decrease confidence** → Catch more objects (sensitive)
- **Decrease overlap** → Better distinction between nearby objects

## 📊 Performance Metrics

- **Inference Speed**: ~50-100ms per image (CPU)
- **Accuracy**: High on fresh/rotten classification
- **Input Formats**: JPG, PNG
- **Max Resolution**: Scales to input size (tested up to 1080p)

## 🐛 Troubleshooting

| Issue | Solution |
|-------|----------|
| Roboflow API error | Check API key and internet connectivity |
| Webcam not detected | Verify camera permissions, try alternate USB ports |
| Slow detection | Reduce image resolution or frame skip |
| Low accuracy | Augment dataset with more images |
| Port 5000 in use | `python app.py --port 8080` |

## 🚀 Future Enhancements

- [ ] Expand dataset to 50+ produce types
- [ ] Real-time training pipeline for model updates
- [ ] Dashboard with analytics & reporting
- [ ] Mobile app integration (Android/iOS)
- [ ] GPU optimization for faster inference
- [ ] Database integration for inventory tracking
- [ ] Multi-model ensemble for improved accuracy
- [ ] Docker containerization for easy deployment

## 📝 License

This project is open-source and available under the MIT License.

## 👤 Authors

- **Mallepogula Ganesh** - Initial development and model training

## 🤝 Contributing

Contributions are welcome! Please feel free to:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📞 Support

For issues, questions, or suggestions:
- Open an issue on GitHub
- Check existing documentation
- Review the troubleshooting section

---

**Note**: This is a demonstration project. For production deployment, consider security hardening, API key management, and comprehensive testing.
- Rotten Fruits/Vegetables
- *(Expandable with additional training data)*
## Functionality Overview

- **FreshnessDetection_live.py**: Handles real-time detection using webcam feed.
- **FreshnessDetection_image.py**: Processes uploaded images for freshness detection.

## Data and Model

- Uses YOLOv8, a state-of-the-art deep learning model for real-time object detection.
- Utilizes publicly available data from Roboflow for initial training.
- Can be expanded with more data to improve accuracy and coverage of different produce types.

## Future Enhancements

- Expand the dataset to include more fruits and vegetables.
- Implement real-time data capture for model refinement.
- Integrate a dashboard for visualizing detection results and generating reports.
- Experiment with different models or custom-trained models for improved accuracy.

## Conclusion

This application provides a quick and effective way to ensure the freshness of products delivered to customers. By using YOLO for real-time object detection, it helps reduce errors in delivering rotten produce and improves customer satisfaction for QuickCommerce platforms.


Feel free to contribute by expanding the dataset, refining the model, or adding new features to this application!
