# RF Modulation Classification using Deep Learning

## 📌 Project Overview
This project implements a **Deep Learning based receiver** capable of classifying digital modulation types (QPSK, 16QAM, 8PSK) under varying noise conditions.

Unlike traditional RF engineering approaches that use mathematical definitions for demodulation, this project treats the problem as a **Computer Vision task**. It generates synthetic I/Q signals, converts them into Constellation Diagrams (images), and uses a Convolutional Neural Network (CNN) to classify the modulation scheme.

## 🚀 Key Features
* **Synthetic Data Generation:** A custom Python simulator acts as the Transmitter and Channel, generating complex I/Q data.
* **Channel Modeling:** Simulates **AWGN** (Additive White Gaussian Noise) with variable **SNR** (Signal-to-Noise Ratio) to train the model for robust performance in noisy environments.
* **Visual Representation:** Converts raw RF signals into **Constellation Diagrams**.
* **AI Model:** A PyTorch-based CNN that classifies modulation types with high accuracy (>95%).
* **Hardware-Agnostic:** Runs entirely on a standard PC without requiring SDR hardware (Software Defined Radio).

## 🛠️ Tech Stack
* **Language:** Python 3.x
* **Deep Learning:** PyTorch
* **Data Processing:** NumPy (for Complex Number manipulation)
* **Visualization:** Matplotlib, Seaborn

## 🧠 Theory & Logic

### 1. Signal Generation (The Transmitter)
The system generates digital symbols mapped to the complex plane (I/Q Data):
* **QPSK:** 4 points (2 bits/symbol).
* **8PSK:** 8 points arranged in a circle (3 bits/symbol).
* **16QAM:** 16 points arranged in a grid (4 bits/symbol).

### 2. Channel Simulation (The Physics)
To mimic real-world conditions, the system introduces randomness:
* **AWGN:** Random Gaussian noise is added to the ideal symbols.
* **Variable SNR:** The model is trained on a range of Signal-to-Noise Ratios (5dB - 25dB) to ensure it learns the *structure* of the data rather than memorizing clean samples.

### 3. The "Vision" Approach
Instead of analyzing the time-domain signal, we plot the **In-Phase (Real)** vs. **Quadrature (Imaginary)** components.
* The CNN analyzes the geometric distribution of the points (the "blobs").
* It learns to distinguish between a "Square grid" (16QAM) and a "4-corner layout" (QPSK), even when the points are scattered due to noise.

## 📊 Results
* **Accuracy:** The model achieves high accuracy on the test set.
* **Robustness:** Successfully classifies signals even in low SNR environments where the constellation diagram appears "cloudy".

## 📂 Project Structure
* `data_generator.py`: Generates the I/Q signals and saves them as images.
* `train_model.py`: Defines the CNN architecture and trains the model.
* `evaluate.py`: visualizes predictions and Confusion Matrix.

---
*Created as a preparation project for RF & AI integration roles.*
