# AI-Driven Website Fingerprinting Attacks in a Closed-World Environment

An artificial intelligence framework designed to evaluate website fingerprinting attacks against encrypted network traffic. By leveraging a 1D-Convolutional Neural Network (1D-CNN), this project demonstrates how metadata side-channels (packet direction sequences) compromise user privacy, even when using secure protocols.

Developed as a core research project for APS360.

---

## 📌 Project Overview
Even when web traffic is encrypted (via HTTPS, VPNs, or Tor), observers can track packet sizes, directions, and timings. Because every website loads unique assets, these metadata footprints create distinct behavioral patterns. 

This project implements a **1D-CNN** to automatically extract sequential, time-dependent features from raw packet sequences, benchmarking its performance against a manually feature-engineered **Support Vector Machine (SVM)** baseline.

---

## 📊 Dataset & Preprocessing
* **Source:** Open-source `WFlib Benchmark Dataset` (Closed-World archive `CW.npz` via Zenodo).
* **Scope:** 105,730 network traffic traces across 95 monitored websites.
* **Pipeline:**
  1. Strip absolute timestamps and byte volumes.
  2. Encode sequences strictly as packet directions: `+1` (outgoing/client) and `-1` (incoming/server).
  3. Standardize dimensions by **truncating** or **zero-padding** all sequences to a fixed threshold of 5,000 elements.

---

## 🏗️ Model Architecture

### 1. Primary Model: 1D-CNN
Treats the packet array similarly to sequential audio/text vectors.
* **Layers:** Multiple 1D-Convolutional Layers for feature extraction + ReLU activations.
* **Output:** Fully Connected Dense layers ending in a Softmax function to calculate classification probabilities across the 95 website classes.

### 2. Baseline Model: SVM
relies on human-engineered statistical features extracted from the traces:
* Total Packet Volume
* Directional Counts
* Traffic Ratio (Incoming vs. Outgoing bytes)

---

## 🚀 Getting Started

### Prerequisites
Ensure you have Python 3.10+ installed. Clone this repository and install dependencies:
```bash
git clone [https://github.com/Harshita-Srikanth/Website-Fingerprinting-Attack.git](https://github.com/Harshita-Srikanth/Website-Fingerprinting-Attack.git)
cd Website-Fingerprinting-Attack
pip install -r requirements.txt
