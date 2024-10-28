readme file for piano - upload video and mention it in this.
# Gesture-Controlled Piano System using OpenCV and MediaPipe

## Overview

This project implements a gesture-controlled piano system that allows users to play piano sounds using hand gestures. By detecting hand landmarks using OpenCV and MediaPipe, the system triggers sound playback when fingertips are positioned over piano keys. The project also features dynamic volume control based on the distance between the thumb and index finger.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Setup](#setup)
- [Usage](#usage)
- [Code Structure](#code-structure)
- [Key Components](#key-components)
- [Conclusion](#conclusion)

## Features

- **Gesture Detection**: Utilizes hand landmarks for real-time gesture recognition.
- **Piano Simulation**: Visual representation of piano keys that responds to hand gestures.
- **Sound Playback**: Trigger sounds for each piano key using Pygame.
- **Dynamic Volume Control**: Adjust volume based on the distance between the thumb and index finger.

## Installation

To set up the project, ensure you have Python installed, and then follow these steps:

1. Clone the repository:
   ```bash
   git clone https://github.com/your_username/gesture-controlled-piano.git
   cd gesture-controlled-piano
   ```

2. Install the required packages:
   ```bash
   pip install -r requirements.txt
   ```

## Setup

1. **Sound Files**: 
   - Create a directory named `tunes` in the project root and place your sound files in it. Ensure the sound files are named as follows:
     - White keys: `a.wav`, `s.wav`, `d.wav`, `f.wav`, `g.wav`, `h.wav`, `j.wav`, `k.wav`, `l.wav`, `;.wav`
     - Black keys: `w.wav`, `e.wav`, `t.wav`, `y.wav`, `u.wav`, `o.wav`, `p.wav`

2. **Webcam Access**: 
   - Ensure your webcam is accessible, as the system requires it for detecting hand gestures.

## Usage

1. **Run the Main Script**: Execute the following command to start the gesture-controlled piano:
   ```bash
   python pianoandvolumecontrol.py
   ```

2. **Control the Piano**:
   - Place your hand in front of the webcam.
   - Position your fingertips above the piano keys on the display to trigger the corresponding sounds.
   - Use the distance between your thumb and index finger to adjust the volume dynamically.

3. **Exit the Application**: Press the 'q' key to quit the application.

## Code Structure

The project consists of the following main files:

- **handDetectorModule.py**: Contains the `handDetector` class for hand landmark detection.
- **pianoandvolumecontrol.py**: The main application script that integrates hand detection with sound playback and visual representation of piano keys.
- **requirements.txt**: Lists the required Python libraries for the project.

## Key Components

### 1. Hand Detection (handDetectorModule.py)

The `handDetector` class is responsible for detecting hands and extracting the position of key landmarks. It utilizes MediaPipe for real-time hand tracking.

- **findHands**: Detects hands in the video frame and draws landmarks.
- **findPosition**: Returns the coordinates of hand landmarks, particularly the tips of the fingers.

### 2. Piano and Volume Control (pianoandvolumecontrol.py)

This script manages the overall functionality of the piano system.

- **Sound Initialization**: 
   - Uses Pygame for sound playback and Pycaw for volume control.
   - Loads sound files for both white and black keys.

- **Drawing the Piano**: 
   - The `draw_piano` function visually renders the piano keys on the screen, highlighting the keys being played.

- **Gesture Recognition**:
   - Captures hand positions using the `handDetector` class.
   - Determines which piano key to highlight based on the little finger's position and plays the corresponding sound.

- **Volume Control**: 
   - Calculates the distance between the thumb and index finger to adjust the volume dynamically.

### 3. Volume Control with Pycaw

The project uses Pycaw to control system volume levels. The volume is set based on the distance between the thumb and index finger, providing an intuitive user experience.

```python
# Example snippet for volume control
vol = np.interp(length, (20, 250), [minVol, maxVol])
volume.SetMasterVolumeLevel(vol, None)
```

## Conclusion

This gesture-controlled piano system showcases the power of combining computer vision and audio processing to create an interactive musical experience. Users can intuitively play music using hand gestures while enjoying dynamic volume control.