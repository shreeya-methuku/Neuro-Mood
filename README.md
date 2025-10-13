# **Real-Time Emotion Detection using CNN and OpenCV**

This project implements a deep learning solution for real-time human emotion classification from a live webcam feed. It combines the power of **Convolutional Neural Networks (CNNs)** for image feature extraction and **OpenCV** for camera handling and face detection.

## **1\. Project Overview**

The system captures video frames, detects human faces, and then uses a pre-trained Keras model to classify the emotion displayed on the face.

**Key Features:**

* **Real-Time Processing:** Analyzes emotions in a continuous video stream.  
* **7 Emotion Classes:** Classifies faces into one of seven categories: Angry, Disgust, Fear, Happy, Neutral, Sad, and Surprise.  
* **Robust Face Detection:** Utilizes OpenCV's Haar Cascade classifier for reliable face localization.

## **2\. Technical Foundation: Convolutional Neural Networks (CNN)**

The core of this system is a **Convolutional Neural Network (CNN)**. CNNs are a class of deep neural networks specifically designed to process pixel data, making them the industry standard for image recognition tasks like emotion detection.

### **How it Works**

1. **Convolutional Layers:** These layers apply filters (kernels) to the input image to extract local features, such as edges, lines, and curves.  
2. **Pooling Layers:** These layers reduce the dimensionality (size) of the feature maps, which helps the model focus on the most important features and makes it more robust to small changes in facial position (translation invariance).  
3. **Fully Connected Layers:** The high-level features learned are flattened and passed to traditional neural network layers for the final classification, outputting a probability score for each of the seven emotions.

## **3\. Project Structure and Required Files**

For this project to run, both the execution script and the model/configuration files are essential.

| File/Asset | Type | Description |
| :---- | :---- | :---- |
| mainnn.py | Python Script | **Primary executable script.** Contains the main loop for video capture, face detection, model prediction, and display. *(Note: main.py and mainn.py are older iterations.)* |
| model.h5 | Keras Model | The **pre-trained CNN model** containing the weights and architecture necessary to classify the  grayscale face image into an emotion. |
| haarcascade\_frontalface\_default.xml | XML Config | The **OpenCV Haar Cascade file** used by the cv2.CascadeClassifier to detect the frontal human face region. **Crucial for the face detection step.** |

## **4\. Setup and Installation**

### **Prerequisites**

You need **Python 3** installed on your system.

### **Dependencies**

This project requires several key libraries, primarily **OpenCV** and **Keras/TensorFlow** for deep learning.

1. **Create a Virtual Environment (Recommended):**  
   python3 \-m venv venv  
   source venv/bin/activate  \# On Windows use \`venv\\Scripts\\activate\`

2. **Install Libraries:**  
   pip install opencv-python numpy keras tensorflow

### **Running the Application**

1. Ensure File Paths are Correct:  
   You must verify that the absolute paths to the .xml and .h5 files within your chosen execution script (e.g., mainnn.py) are correct for your system. The current paths look like this:  
   face\_classifier \= cv2.CascadeClassifier(r'/Users/ameca/Emotion\_Detection\_CNN/haarcascade\_frontalface\_default.xml')  
   classifier \= load\_model(r'/Users/ameca/Emotion\_Detection\_CNN/model.h5')

   **You must update these paths** if your files are located elsewhere, or place the files in the directory specified.  
2. Execute the Script:  
   Run the primary script from your terminal:  
   python mainnn.py

3. **Operation:**  
   * Your webcam will activate, and a new window titled **"Emotion Detector"** will appear.  
   * Faces detected in the frame will be outlined with a rectangle.  
   * The model's real-time emotion prediction will be displayed above the rectangle.  
   * Press the **'q' key** to exit the application.