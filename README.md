# Sports Video Cropping Script

## Overview
The script processes a sport match video with dimensions 2704x900, cropping it to YouTube-compatible 16:9 aspect ratio (1600x900) while dynamically tracking the action (players and ball) using the YOLOv8 object detection model. The script ensures smooth frame transitions for a natural viewing experience.

## Prerequisites
- Python 3.6 or higher
- A virtual environment (recommended)
- Input video file in 2704x900 resolution
- Installed dependencies: `opencv-python`, `numpy`, `ultralytics`

## Installation
1. Create and activate a virtual environment:
   ```bash
   python -m venv .venv
   ```
   - **Windows**:
     ```bash
     .venv\Scripts\activate
     ```
   - **Linux/macOS**:
     ```bash
     source .venv/bin/activate
     ```
2. Install required packages:
   ```bash
   pip install opencv-python numpy ultralytics
   ```

## Usage
1. Place your input video file (e.g., `input_video.mp4`) in the project directory.
2. Update the `input_path` and `output_path` variables in `crop_soccer_video.py` with the paths to your input and output video files:
   ```python
   input_path = 'path/to/your/input_video.mp4'
   output_path = 'path/to/your/output_video.mp4'
   ```
3. Run the script:
   ```bash
   python crop_soccer_video.py
   ```
4. The script will generate a cropped video in 16:9 aspect ratio, saved to the specified `output_path`.

## How It Works
- **Object Detection**: Uses YOLOv8 (`yolov8n.pt`) to detect players (class `person`) and the ball (class `sports ball`).
- **Action Tracking**: Centers the 1600x900 crop window on the ball (if detected) or the average position of players.
- **Smoothing**: Applies a moving average over 5 frames to ensure smooth transitions.
- **Output**: Saves the cropped video in MP4 format with the original frame rate.

## Notes
- For better detection accuracy, consider using a heavier YOLO model (e.g., `yolov8m.pt`) by replacing `yolov8n.pt` in the script.
- Processing high-resolution videos may be slow; consider downscaling frames temporarily for faster analysis (requires code modification).
- Ensure sufficient disk space for the output video.
- The generated `requirements.txt` (via `generate_requirements.py`) can be used to replicate the environment:
  ```bash
  pip install -r requirements.txt
  ```

## License
GNU

# Generate Requirements Script

## Overview
The `generate_requirements.py` script creates a `requirements.txt` file listing all Python packages installed in the active virtual environment. This allows other developers to easily replicate the environment for consistent project setup.

## Prerequisites
- Python 3.6 or higher
- An active Python virtual environment (e.g., `.venv`)
- Installed packages relevant to the project (e.g., `opencv-python`, `numpy`, `ultralytics`)

## Installation
1. Ensure you have a virtual environment set up in your project directory:
   ```bash
   python -m venv .venv
   ```
2. Activate the virtual environment:
   - **Windows**:
     ```bash
     .venv\Scripts\activate
     ```
   - **Linux/macOS**:
     ```bash
     source .venv/bin/activate
     ```
3. Install project dependencies (if not already installed):
   ```bash
   pip install opencv-python numpy ultralytics
   ```

## Usage
1. Ensure the virtual environment is activated (see above).
2. Run the script to generate the `requirements.txt` file:
   ```bash
   python generate_requirements.py
   ```
3. The script will create a `requirements.txt` file in the project directory, listing all installed packages and their versions.

## Reproducing the Environment
To replicate the environment on another machine:
1. Create and activate a new virtual environment (as shown in the Installation section).
2. Install the dependencies listed in `requirements.txt`:
   ```bash
   pip install -r requirements.txt
   ```

## Notes
- Ensure the virtual environment is active before running the script, as it only captures packages from the active environment.
- The generated `requirements.txt` file should be included in the project repository for version control.
- If specific Python versions are required, document them in your project setup instructions.
