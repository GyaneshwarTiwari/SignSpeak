# Real-Time Indian Sign Language (ISL) Recognition

This project implements a real-time sign language recognition system tailored for the Indian Sign Language (ISL) dataset. Its primary goal is to enhance communication accessibility for the deaf and hard‑of‑hearing community in India.

## Dataset
- **Classes**: 36 (digits 0–9 and letters A–Z)  
- **Samples**: 36,000 images (1,000 per class)  
- **Resolution**: 250×250  
- **Capture Device**: 720p laptop camera  
- **Conditions**: Varying lighting and backgrounds for robustness  

## Feature Extraction
- Utilizes **MediaPipe Hands** to extract 3D hand landmarks  
- Converts each image into a **126-dimensional** feature vector  
  - 63 features per hand, up to two hands  
- Captures spatial and depth information critical for gesture discrimination  

## Model Architecture
- **Framework**: TensorFlow/Keras  
- **Type**: Sequential neural network  
- **Layers**:  
  1. Dense (256 units, ReLU)  
  2. Dropout (30%)  
  3. Dense (128 units, ReLU)  
  4. Dropout (30%)  
  5. Dense (64 units, ReLU)  
  6. Dropout (30%)  
  7. Dense (36 units, Softmax)  
- **Training Setup**:  
  - **Split**: 60% train (21,600 samples), 40% test (14,400 samples)  
  - **Epochs**: 50  
  - **Optimizer**: Adam (lr=0.001)  
  - **Loss**: Categorical cross‑entropy  

## Evaluation
- **Metrics**: Accuracy, Precision, Recall, F1‑score  
- **Visualizations**: Confusion matrix & classification report  

## Real-Time GUI
- **Toolkit**: Tkinter  
- **Features**:  
  - Live video capture from a 720p webcam  
  - Prediction confidence threshold (0.7)  
  - Temporal consistency logic for reliable character appending  
  - Flat-palm gesture for error correction  

## API & Post‑Processing
- **Framework**: Flask API  
- **Integration**: Google Gemini (gemini-1.5-flash)  
- **Purpose**: Refine output text (e.g., correct “HELLOO WRLD” → “Hello World”)  

## Future Work
- Improve single‑hand detection consistency  
- Expand dataset diversity (more signers & environments)  
- Support dynamic gestures  
- Optimize for faster real‑time performance  
