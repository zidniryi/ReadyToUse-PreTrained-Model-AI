# Curated List of Pre-Trained AI Models

This repository contains a collection of **pre-trained AI models** in TensorFlow Lite (`.tflite`) format, along with their corresponding label files (`labels.txt`). These models are designed for tasks such as image classification for cats, dogs, birds, and color recognition.

## Table of Contents

- [Introduction](#introduction)
- [Model Overview](#model-overview)
  - [Cat & Dog Classification](#cat--dog-classification)
  - [Bird Classification](#bird-classification)
  - [Color Classification](#color-classification)
- [How to Use](#how-to-use)
- [Contributing](#contributing)
- [License](#license)

## Introduction

This repository provides pre-trained AI models in `.tflite` format, optimized for mobile and edge devices. Each model is accompanied by a `labels.txt` file that maps the output to the corresponding categories. These models are ideal for quick integration into applications needing image classification functionality.

## Model Overview

### Cat & Dog Classification

- **Model:** `model_unquant.tflite`
- **Labels:** `labels.txt`
- **Task:** Classifies images into two categories: **Cat** and **Dog**.
- **Format:** TensorFlow Lite (`.tflite`)
- **Source:** Pre-trained model for mobile-based applications to detect whether an image contains a cat or a dog.

### Bird Classification

- **Model:** `model_unquant.tflite`
- **Labels:** `labels.txt`
- **Task:** Classifies images into bird categories.
- **Format:** TensorFlow Lite (`.tflite`)
- **Source:** Model designed to classify bird species from image input.

### Color Classification

- **Model:** `model_unquant.tflite`
- **Labels:** `labels.txt`
- **Task:** Classifies images based on dominant colors.
- **Format:** TensorFlow Lite (`.tflite`)
- **Source:** A simple color classification model to identify dominant colors in an image.

## How to Use

1. **Download the Models**:

   - Clone this repository or download the individual model files.

2. **Load the Model in Your Application**:

   - Using TensorFlow Lite in Python:

     ```python
     import tensorflow as tf

     # Load the TFLite model and allocate tensors
     interpreter = tf.lite.Interpreter(model_path="model_unquant.tflite")
     interpreter.allocate_tensors()

     # Get input and output details
     input_details = interpreter.get_input_details()
     output_details = interpreter.get_output_details()

     # Perform inference on an image (input should be preprocessed to match model requirements)
     interpreter.set_tensor(input_details[0]['index'], input_data)
     interpreter.invoke()

     # Get the output
     output_data = interpreter.get_tensor(output_details[0]['index'])
     print("Predicted label:", output_data)
     ```

3. **Use the `labels.txt` File**:

   - The `labels.txt` file contains a list of classes. You can map the model’s output to the human-readable label like so:
     ```python
     with open("labels.txt", "r") as f:
         labels = f.read().splitlines()
     predicted_label = labels[output_data.argmax()]
     print("Predicted label:", predicted_label)
     ```

4. **Optimizing for Mobile**:
   - These models are already optimized in `.tflite` format for mobile and edge devices.

## Contributing

Feel free to submit pull requests if you have additional models or improvements to suggest. Contributions to expand this list are welcome!

## License

This repository is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
