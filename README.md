# 🧠 Anomaly Detection using Autoencoders on MNIST

## 📌 Project Overview
This project demonstrates **Anomaly Detection** using **Convolutional Autoencoders** on the **MNIST dataset**. Instead of classifying digits, the model learns to **reconstruct normal images** and flags **anomalies** when reconstruction quality is poor.

Autoencoders are widely used in:
- **Fraud detection** (e.g., detecting unusual transactions)
- **Industrial defect detection** (e.g., identifying faulty products)
- **Medical imaging** (e.g., finding anomalies in MRI scans)
- **Cybersecurity** (e.g., detecting network intrusions)

---

## 📂 Dataset Used
We use the built-in **MNIST dataset** from TensorFlow, which contains **handwritten digits (0-9)**. However, instead of classifying digits, the model is trained to **reconstruct normal images**, allowing it to detect anomalies based on **reconstruction errors**.

### 🔹 Dataset Details:
- **Training Set:** 60,000 images
- **Testing Set:** 10,000 images
- **Image Size:** `28x28 pixels` (Grayscale)
- **Labels:** Digits from `0-9`

---

## 🔍 How Autoencoders Work
An **Autoencoder** is a type of neural network that learns **compressed representations** of data (encoding) and then reconstructs the original data (decoding). If an image cannot be **accurately reconstructed**, it is likely an **anomaly**.

### ✨ **Model Architecture**
1️⃣ **Encoder**: Compresses the input image into a smaller feature representation.  
2️⃣ **Decoder**: Reconstructs the input image from the compressed representation.  

The **difference between input and output** is called the **Reconstruction Error**, which is used to detect **anomalies**.

---

## 🚀 Implementation Steps
### **1️⃣ Load the Dataset**
- Import the **MNIST dataset** from TensorFlow.
- Normalize the pixel values between `0` and `1`.
- Reshape images to `(28, 28, 1)` for CNN processing.

### **2️⃣ Build the Autoencoder Model**
- **Encoder:**
  - Convolutional layers (`Conv2D`) extract features.
  - **MaxPooling** reduces dimensionality.
- **Decoder:**
  - **UpSampling** reconstructs the original image.
  - A final `Conv2D` layer generates the reconstructed image.

### **3️⃣ Train the Model**
- Use `Adam` optimizer and `Binary Cross-Entropy` loss function.
- Train for `10 epochs` on the MNIST dataset.
- Monitor **training loss** to ensure good reconstruction.

### **4️⃣ Detect Anomalies**
- Pass test images through the Autoencoder.
- Compute the **Reconstruction Error**.
- If the error is **high**, the image is flagged as an **anomaly**.

---

## 📊 Results & Analysis
After training, the model successfully reconstructs most images.  
However, when anomalies are present, the **reconstruction error increases**, making anomaly detection possible.

### ✅ **Expected Results**
- **Normal images** are reconstructed **accurately**.
- **Anomalies** (e.g., distorted digits, unseen patterns) have **blurry or poor reconstructions**.
- **Reconstruction error thresholding** is used to classify anomalies.

---

## 📸 Sample Output
**Top Row:** Original MNIST images  
**Bottom Row:** Reconstructed images (Anomalies will have distortions)  

