# AI Gesture Control - Virtual Mouse

This project allows you to control your computer's cursor, clicks, scrolling, and system commands using hand gestures captured through your webcam. It uses computer vision to create a virtual mouse, providing a touchless way to interact with your PC.

## Features

The application recognizes a variety of hand gestures to perform different actions:

| Gesture | Action |
| :--- | :--- |
| **One Finger Up** (Index) | **Cursor Control:** Move your index finger to move the mouse cursor across the screen. |
| **One Finger Up & Thumb Touch** | **Click & Drag:** <br> - **Single Click:** Briefly touch your thumb to the base of your middle finger. <br> - **Click & Hold:** Keep your thumb touched to drag and drop items. |
| **Two Fingers Up** (Index & Middle) | **Scroll Mode:** Move your hand up or down to scroll vertically. |
| **Three Fingers Up** (Index, Middle, Ring) | **Window Management:** <br> - **Swipe Up:** Open Task View (equivalent to `Win` + `Tab`). <br> - **Swipe Down:** Minimize the current window. |
| **Four Fingers Up** (All except thumb) | **Application Switching:** <br> - **Swipe Right:** Switch to the next application (`Alt` + `Tab`). <br> - **Swipe Left:** Switch to the previous application (`Alt` + `Shift` + `Tab`).|

## How It Works

The project is built on a few key libraries:

* **OpenCV:** Captures the video feed from the webcam.
* **MediaPipe:** Detects the hand and its 21 landmarks in real-time from the video feed.
* **NumPy:** Performs numerical operations to calculate distances and smoothen cursor movement.
* **PyAutoGUI:** Programmatically controls the mouse and keyboard to execute the corresponding actions on the operating system.

The main script reads the camera frame, passes it to the `handDetector` module (which uses MediaPipe), and gets the coordinates of the hand landmarks. It then checks how many fingers are up to determine the current gesture mode and performs the relevant action.

## Prerequisites

-   Python 3.7+
-   A webcam

## Setup and Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
    cd your-repo-name
    ```

2.  **Create a virtual environment (recommended):**
    ```bash
    # For Windows
    python -m venv venv
    .\venv\Scripts\activate

    # For macOS/Linux
    python3 -m venv venv
    source venv/bin/activate
    ```

3.  **Install the required packages:**
    Make sure you have a `requirements.txt` file with the required packages in your project directory.
    ```bash
    pip install -r requirements.txt
    ```

## How to Run

1.  Ensure your webcam is connected and not being used by another application.
2.  Run the main script from your terminal:
    ```bash
    python gesture_control.py
    ```
3.  A window showing your webcam feed will appear. You can now start using hand gestures to control your computer.
4.  To stop the program, press `q` on the OpenCV window or `Ctrl + C` in the terminal.

## Project Files

* `gesture_control.py`: The main script that runs the application loop, processes gestures, and controls the system.
* `HandTrakModule.py`: A reusable module that contains the `handDetector` class to find and process hand landmarks using MediaPipe.
* `requirements.txt`: A list of all the Python packages required for the project.

## Customization

You can fine-tune the application's behavior by modifying the variables at the top of the `gesture_control.py` script:

-   `smoothening`: A higher value makes the cursor movement smoother but slightly less responsive.
-   `frameR`: The "reduction" of the frame size for mapping hand movement to the screen. Adjust this to change cursor sensitivity.
-   `scroll_sensitivity`: Increases or decreases the speed of vertical scrolling.
-   `swipe_threshold` / `swipe_threshold_horizontal`: The distance your hand needs to travel to trigger a swipe action.

-   
https://github.com/user-attachments/assets/d4d1c763-fca4-451c-8e71-1521d8c345df

