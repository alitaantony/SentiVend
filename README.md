# Vending Machine Emotion-based Snack Recommendation System

This project uses facial emotion recognition and audio tone analysis to suggest snacks and drinks from a vending machine based on the user's emotional and tonal response. The system leverages TinyML to deploy the models on an embedded device (SeeedStudio XIAO ESP32S3) with an onboard camera and microphone.

## Features

- **Facial Emotion Recognition**: Detects the user's emotional state through facial expressions.
- **Audio Tone Recognition**: Analyzes the user's voice tone to understand their mood.
- **Snack Suggestion**: Based on facial and tonal analysis, the system recommends a snack or drink from the vending machine.
- **TinyML Deployment**: The model is optimized and deployed on the SeeedStudio XIAO ESP32S3 microcontroller.

## Hardware Used

- **SeeedStudio XIAO-ESP32S3 Sense**
  - Onboard Camera
  - PDM Microphone
  - ESP32S3 Chipset
- **SeeedStudio XIAO nRF52840 Sense**
  - IMU Sensor
  - PDM Microphone
- **SeeedStudio Grove Vision 2**
  - Arm Cortex-M55
  - Ethos-U55
  - Supports TensorFlow and PyTorch

## Software Requirements

- **Python**: 3.8.0 or higher
- **Libraries**:
  - `tensorflow` (2.11.0 or latest)
  - `tensorflow-lite` (2.11.0 or latest)
  - `librosa` (0.9.2)
  - `numpy` (1.23.1)
  - `scipy` (1.9.1)
  - `soundfile` (0.10.3.post1)
  - `pyserial` (3.5)
  - `opencv-python` (4.7.0)
- **Arduino IDE** (for programming the ESP32)
- **ESP32 Board Support** in Arduino IDE

## Installation

### Python Dependencies

Install Python packages using `pip`:

### Arduino IDE Setup

1. Install **ESP32 Board Support** in Arduino IDE:
   - Go to **File > Preferences** in Arduino IDE.
   - In the **Additional Boards Manager URLs** field, add the ESP32 URL: `https://dl.espressif.com/dl/package_esp32_index.json`.
   - Go to **Tools > Board > Boards Manager**, search for "ESP32", and install it.

2. Install the **TensorFlow Lite for Microcontrollers** library:
   - In Arduino IDE, go to **Sketch > Include Library > Manage Libraries**.
   - Search for **"TensorFlow Lite for Microcontrollers"** and install it.

---

### Uploading Code to ESP32

1. Open the `emotion_model_inference.ino` file in Arduino IDE.
2. Select the correct **Board**:
   - Go to **Tools > Board** and select **SeeedStudio XIAO ESP32S3**.
3. Select the correct **Port**:
   - Go to **Tools > Port** and select the port associated with the XIAO ESP32S3.
4. Click **Upload** to upload the code to the device.

---

### Model Deployment

1. **Train the Models**:
   - Train the **Facial Emotion Recognition Model** and **Tone Recognition Model** using appropriate datasets.
   - For facial emotion recognition, use datasets like FER-2013. For tone recognition, datasets like EmoReact can be used.
   
2. **Convert Models to TensorFlow Lite**:
   - Once the models are trained, convert them into TensorFlow Lite format (`.tflite`).
   - Use TensorFlow's `TFLiteConverter` to convert the models.

3. **Include the Models in Arduino Project**:
   - Copy the `.tflite` model files into the **`data`** folder in your Arduino project.
   - Modify the code in the `emotion_model_inference.ino` file to load and use these models.

---

### Usage

1. The user clicks the **"Choose for me"** button on the interface to begin the process.
2. The **camera** on the XIAO ESP32S3 captures the user's facial expression to detect emotions such as happiness, sadness, anger, etc.
3. The **microphone** records the user's response to the prompt (e.g., "How are you today?") for tonal analysis.
4. The system combines the results of both **facial emotion recognition** and **audio tone analysis** to determine the user's emotional state.
5. Based on this analysis, the system suggests an appropriate snack or drink from the vending machine.

---

### Contributing

Contributions are welcome! Feel free to fork the repository, make improvements, and submit pull requests. Here’s how you can contribute:

1. **Fork the Repository**: Click the **Fork** button on the top right of this repository.
2. **Clone your fork**:
   ```bash
   git clone https://github.com/YOUR-USERNAME/Vending-Machine-Emotion-Based-Snack-Recommendation-System.git
