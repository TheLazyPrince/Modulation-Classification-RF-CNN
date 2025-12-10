# RF Modulation Classifier (Python & Deep Learning)

## About The Project
I built this project to explore how Computer Vision can be applied to Radio Frequency (RF) tasks.
Since I didn't have access to physical RF hardware (like an SDR or Spectrum Analyzer) at home, I decided to build a full simulation in Python.

The goal was to create a "Digital Twin" of a communication system: generating signals, simulating a noisy channel, and then using a Neural Network to figure out which modulation was used based on the signal's shape.

## How It Works
Instead of using traditional mathematical demodulation, I treated this as an image classification problem:

1.  **The Transmitter (Simulation):** I used `numpy` to generate complex I/Q signals for three common modulation types: **QPSK**, **16QAM**, and **8PSK**.
2.  **The Channel (Physics):** To make it realistic, I added **AWGN** (Additive White Gaussian Noise) to the signals. I varied the **SNR** (Signal-to-Noise Ratio) randomly, so the model learns to handle both clean and very noisy signals.
3.  **The "Eyes":** I plotted the I/Q data as **Constellation Diagrams** (scatter plots) and saved them as images.
4.  **The "Brain":** I trained a custom **CNN (Convolutional Neural Network)** in PyTorch to look at these diagrams and classify the modulation type.

## Project Structure
* `data_generator.py`: The simulator. It creates the signals, adds noise/interference, and generates the dataset images.
* `train_model.py`: The PyTorch model. It loads the images into RAM and trains the CNN.
* `evaluate.py`: Tests the model and visualizes the results (including a Confusion Matrix).

## Key Concepts Used
* **RF:** I/Q Data, Constellation Diagrams, AWGN, SNR, Modulation schemes (QPSK/8PSK/16QAM).
* **Deep Learning:** CNN Architecture, Custom Dataset Loading, Supervised Learning.
* **Python:** Numpy for vector math, Matplotlib for visualization.

## Results
The model achieves high accuracy (approx. 95%+) on the test set.
It was interesting to see that the model makes mistakes exactly where a human would—when the SNR is so low that the constellation "dots" turn into a shapeless cloud of noise.


1. Install requirements:
    ```bash
    pip install numpy matplotlib torch torchvision seaborn scikit-learn
    ```


---
*Built as a hands-on project to combine Signal Processing concepts with AI.*