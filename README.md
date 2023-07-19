# Eye_Gaze_Tracking
The Gaze Checker hardware and software infrastructure can implement gaze monitoring.

## Gaze Checker Annotator Software:
Determine eye movement from the raw streamed image. ESP32-CAM acts as an Access Point and generates a WiFi hotspot network. 
When ESP is switched on, the network is created:
- SSID: EyeGazeTracking
- Password: 12345678

ESP32-CAM streams the image to a static local IP:
- Image resolution: VGA (640x480) 
- LocalIP: 192.168.4.1

To use the Annotator Software, the phone must be connected to the ESP network. Software currently compatible with Android systems:
- Android Studio - Kotlin is the development environment

The software displays the streamed image on the phone. Processes the image frame by frame and creates a Bitmap with the appropriate resolution for the detection to work. During detection, the software displays the data in real time.
Different timers can be set in the software:
- 1 minute
- 5 minutes
- 10 minutes
- 20 minutes
- 30 minutes
- 500 minutes

When the timers expire or the software is switched off, the processed images and the extracted data are saved by the software. Creates 2 subfolders in the "Documents" or "Download" folder on the phone to save CSV files and image files.
CSV files:
- Name: DateTime of creation
- Format: yyyy-MM-dd_HHH-mm-ss-SSS

Contents:
- date_time,pupil_side,top,left,right,bottom,centerX,centerY
- date_time: time of detection in milliseconds
- pupil_side: left or right pupil
- Generates a boundigBox around the pupil with the following coordinates
  - top
  - left
  - righ
  - bottom

![Picture2](https://github.com/BenceBiricz/Eye_Gaze_Tracking/assets/71565433/fd79f4cf-6992-497b-ba8b-9fb8bdba40d6)

- centerX,centerY = center of the boundingBox

The software is able to determine the range of pupil movement using a measurement:
- Determining the maximum and minimum values of the bounding boxes

## Software GUI:
| Main | Real time evaluation | Settings |
| ------------- |:-------------:| -----:|
| ![Picture3](https://github.com/BenceBiricz/Eye_Gaze_Tracking/assets/71565433/fcea072d-c248-46b1-a52c-b25b07d3fc8a) | ![Picture5](https://github.com/BenceBiricz/Eye_Gaze_Tracking/assets/71565433/f3b32e90-8acf-4819-ba1e-e634e0b47011) | ![Picture4](https://github.com/BenceBiricz/Eye_Gaze_Tracking/assets/71565433/e667824f-8d0c-4c30-9ced-f32d7fb6b31b) |
| ------------- |:-------------:| -----:|


