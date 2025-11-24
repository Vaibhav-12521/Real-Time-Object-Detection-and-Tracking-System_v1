# Real-Time Object Detection and Tracking System

A Python-based real-time object detection and tracking system using YOLOv8 and OpenCV. This project enables live webcam object detection with persistent tracking IDs.

## Features

- ✅ Real-time object detection from webcam feed
- ✅ Object tracking with persistent IDs across frames
- ✅ Support for multiple YOLO model variants (nano, small, medium, large, extra-large)
- ✅ FPS counter for performance monitoring
- ✅ Easy-to-use class-based architecture

## Requirements

- Python 3.8+
- OpenCV (cv2)
- NumPy
- Ultralytics YOLO

## Installation

1. Clone or download this repository

2. Install required dependencies:
```bash
pip install opencv-python numpy ultralytics
```

3. Download YOLO model weights (automatically downloaded on first run):
   - `yolov8n.pt` (Nano - fastest)
   - `yolov8s.pt` (Small)
   - `yolov8m.pt` (Medium)
   - `yolov8l.pt` (Large)
   - `yolov8x.pt` (Extra Large - most accurate)

## Usage

### Basic Usage

Run the detection system with default settings (YOLOv8 nano model):

```bash
python main.py
```

### Custom Model

To use a different YOLO model, modify the [`main()`](testing/main.py) function:

```python
detect = tracker(model_path='yolov8m.pt')  # Use medium model
```

### Custom Camera

To use a different camera device:

```python
detect.detect_live(camera_id=1)  # Use secondary camera
```

## Code Structure

### Classes

#### `tracker`

Main class for object detection and tracking.

**Constructor:**
```python
tracker(model_path='yolov8m.pt')
```
- `model_path`: Path to YOLO model file

**Methods:**

- `detect_live(camera_id=0)`: Start live detection from webcam
  - `camera_id`: Camera device ID (default: 0 for primary webcam)
  
- `names()`: Get dictionary of detectable object classes

## Controls

- **Press 'q'**: Quit the application

## Model Comparison

| Model | Size | Speed | Accuracy |
|-------|------|-------|----------|
| yolov8n.pt | Smallest | Fastest | Good |
| yolov8s.pt | Small | Fast | Better |
| yolov8m.pt | Medium | Moderate | Great |
| yolov8l.pt | Large | Slow | Excellent |
| yolov8x.pt | Largest | Slowest | Best |

## Example Output

The system displays:
- Bounding boxes around detected objects
- Object class labels
- Tracking IDs for each object
- Real-time FPS counter

## Troubleshooting

**Camera not opening:**
- Check if camera is connected and not in use by another application
- Try different `camera_id` values (0, 1, 2, etc.)

**Low FPS:**
- Use a smaller model (e.g., `yolov8n.pt`)
- Reduce input resolution
- Ensure proper GPU drivers are installed

**Module not found errors:**
- Install all required packages: `pip install opencv-python numpy ultralytics`

## License

This project uses the Ultralytics YOLOv8 model. Please refer to [Ultralytics License](https://github.com/ultralytics/ultralytics/blob/main/LICENSE) for details.

## Acknowledgments

- [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics)
- OpenCV community

## Future Enhancements

- [ ] Add video file input support
- [ ] Implement object counting
- [ ] Add recording functionality
- [ ] Support for custom-trained models
- [ ] Multi-camera support
- [ ] Object detection logging
