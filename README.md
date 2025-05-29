# Deepfake Video Detection using ResNeXt and LSTM

This project aims to detect **video deepfakes** using advanced deep learning techniques, combining the power of **ResNeXt** and **LSTM** architectures.

## 🧠 Model Architecture

- **ResNeXt50** (pretrained on ImageNet) is used as the **CNN backbone** to extract rich feature vectors from individual video frames.
- These frame-wise features are passed to a **Long Short-Term Memory (LSTM)** network to capture temporal dependencies across frames.
- A final **classification layer** predicts whether the video is real or fake.

## 🔍 Preprocessing

- Faces were detected and aligned using **MTCNN (Multi-task Cascaded Convolutional Networks)**.
- The detected faces were resized and normalized before being passed to the model.

## 🚀 Highlights

- **Transfer Learning**: Utilized pretrained ResNeXt to improve performance and reduce training time.
- **Sequential Modeling**: Used LSTM to understand the sequence of frames, enabling robust detection.
- **Video-based pipeline**: The model processes sequences of frames to make predictions on full videos.

## 📈 Results

- Achieved an accuracy of **80%** on the validation dataset and 0.82 AUC.
- Balanced performance on real and fake videos
