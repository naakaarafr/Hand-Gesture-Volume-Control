# Hand Gesture Volume Control

A Python application that controls your computer's volume using hand gestures detected through your webcam. The system tracks the distance between your thumb and index finger to increase or decrease the system volume.

## Features

- **Real-time hand tracking** using MediaPipe
- **Gesture-based volume control** - pinch to decrease volume, spread fingers to increase volume
- **Visual feedback** with hand landmarks and distance indicators
- **Cross-platform compatibility** (Windows, macOS, Linux)

## How It Works

The application uses computer vision to:
1. Capture video from your webcam
2. Detect hand landmarks using MediaPipe
3. Track the positions of your thumb tip (landmark 4) and index finger tip (landmark 8)
4. Calculate the distance between these two points
5. Control system volume based on the distance:
   - **Distance > 25 pixels**: Increase volume
   - **Distance ≤ 25 pixels**: Decrease volume

## Prerequisites

- Python 3.7 or higher
- A working webcam
- The following Python packages (see Installation section)

## Installation

1. **Clone or download this repository**
   ```bash
   git clone https://github.com/naakaarafr/Hand-Gesture-Volume-Control.git
   cd Hand-Gesture-Volume-Control
   ```

2. **Install required packages**
   ```bash
   pip install opencv-python mediapipe pyautogui
   ```

   Or install from requirements.txt if available:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. **Run the application**
   ```bash
   python volume_control.py
   ```

2. **Position your hand in front of the camera**
   - Make sure your hand is well-lit and clearly visible
   - Keep your hand within the camera frame

3. **Control volume with gestures**
   - **Increase volume**: Spread your thumb and index finger apart (distance > 25 pixels)
   - **Decrease volume**: Bring your thumb and index finger closer together (pinch gesture)

4. **Visual indicators**
   - Green circle: Index finger tip position
   - Red circle: Thumb tip position
   - Green line: Distance between thumb and index finger
   - Hand landmarks: White dots and connections showing detected hand structure

5. **Exit the application**
   - Press the `ESC` key to close the application

## Controls

| Gesture | Action |
|---------|--------|
| Pinch (fingers close) | Volume Down |
| Spread (fingers apart) | Volume Up |
| ESC key | Exit application |

## Technical Details

### Dependencies
- **OpenCV (cv2)**: Video capture and image processing
- **MediaPipe**: Hand landmark detection and tracking
- **PyAutoGUI**: System volume control simulation

### Key Components
- Hand detection using MediaPipe's hand tracking solution
- Landmark extraction for thumb tip (ID: 4) and index finger tip (ID: 8)
- Distance calculation using Euclidean distance formula
- Volume control through simulated key presses (volumeup/volumedown)

### Performance Notes
- The distance calculation includes a division by 4 for sensitivity adjustment
- Frame rate depends on your camera and system performance
- The application processes video frames in real-time

## Troubleshooting

### Common Issues

1. **Camera not working**
   - Ensure your webcam is properly connected
   - Check if other applications are using the camera
   - Try changing the camera index in `cv2.VideoCapture(0)` to `cv2.VideoCapture(1)` or higher

2. **Hand not detected**
   - Ensure good lighting conditions
   - Keep your hand clearly visible in the frame
   - Try adjusting the distance from the camera

3. **Volume not changing**
   - Check if PyAutoGUI has permission to control your system
   - On macOS, you may need to grant accessibility permissions
   - On Linux, ensure your system responds to volumeup/volumedown key events

4. **Installation errors**
   - Make sure you have Python 3.7+ installed
   - Try installing packages individually
   - Consider using a virtual environment

### Platform-Specific Notes

**macOS:**
- May require accessibility permissions for PyAutoGUI
- Go to System Preferences > Security & Privacy > Accessibility

**Linux:**
- Ensure your desktop environment supports volume key simulation
- Some distributions may require additional audio system configuration

**Windows:**
- Should work out of the box with most systems
- Windows Defender might flag PyAutoGUI initially

## Customization

You can modify the following parameters in the code:

- **Distance threshold**: Change the value `25` in the condition `if dist>25:` to adjust sensitivity
- **Camera source**: Modify `cv2.VideoCapture(0)` to use a different camera
- **Circle sizes**: Adjust the `radius=15` parameter in `cv2.circle()` calls
- **Volume step**: Currently uses single key presses; can be modified for multiple presses

## Future Enhancements

Potential improvements for the project:
- Add volume level visualization
- Implement multiple gesture types
- Add configuration file for customizable settings
- Include audio feedback
- Support for multiple hands
- Add gesture for mute/unmute functionality

## Contributing

Feel free to fork this project and submit pull requests for improvements. Some areas for contribution:
- Better error handling
- Configuration management
- Additional gesture recognition
- Performance optimizations
- Cross-platform testing

## License

This project is open source and available under the [MIT License](LICENSE).

## Acknowledgments

- MediaPipe team for the excellent hand tracking solution
- OpenCV community for computer vision tools
- PyAutoGUI developers for system automation capabilities
