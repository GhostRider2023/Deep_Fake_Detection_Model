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

- Achieved an accuracy of **80%** on the validation dataset.
- Balanced performance on real and fake videos

## 📂 Project Structure

<svg viewBox="0 0 900 700" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <marker id="arrowhead" markerWidth="10" markerHeight="7" refX="9" refY="3.5" orient="auto">
      <polygon points="0 0, 10 3.5, 0 7" fill="black" />
    </marker>
    <marker id="arrowhead-red" markerWidth="10" markerHeight="7" refX="9" refY="3.5" orient="auto">
      <polygon points="0 0, 10 3.5, 0 7" fill="red" />
    </marker>
    <pattern id="dashed" patternUnits="userSpaceOnUse" width="8" height="8">
      <rect width="8" height="8" fill="white"/>
      <rect width="4" height="1" fill="red"/>
      <rect x="0" y="4" width="4" height="1" fill="red"/>
    </pattern>
  </defs>
  
  <!-- Legend -->
  <text x="680" y="25" font-family="Arial, sans-serif" font-size="14" font-weight="bold">Training Flow</text>
  <line x1="680" y1="35" x2="730" y2="35" stroke="black" stroke-width="2" marker-end="url(#arrowhead)"/>
  
  <text x="680" y="55" font-family="Arial, sans-serif" font-size="14" font-weight="bold" fill="red">Prediction Flow</text>
  <line x1="680" y1="65" x2="730" y2="65" stroke="red" stroke-width="2" stroke-dasharray="5,5" marker-end="url(#arrowhead-red)"/>
  
  <!-- Upload Video -->
  <polygon points="350,20 450,20 470,50 350,50" fill="none" stroke="black" stroke-width="2"/>
  <text x="410" y="40" font-family="Arial, sans-serif" font-size="12" text-anchor="middle">Upload Video</text>
  
  <!-- Dataset -->
  <ellipse cx="80" cy="200" rx="60" ry="40" fill="none" stroke="black" stroke-width="2"/>
  <text x="80" y="195" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Dataset (Fake /</text>
  <text x="80" y="208" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Real) videos</text>
  
  <!-- Preprocessing Box -->
  <rect x="180" y="120" width="150" height="160" fill="none" stroke="black" stroke-width="2"/>
  <text x="255" y="140" font-family="Arial, sans-serif" font-size="12" font-weight="bold" text-anchor="middle">Preprocessing</text>
  
  <!-- Preprocessing steps -->
  <rect x="190" y="150" width="130" height="20" fill="white" stroke="black" stroke-width="1"/>
  <text x="255" y="163" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Splitting video into frames</text>
  
  <rect x="190" y="180" width="130" height="20" fill="white" stroke="black" stroke-width="1"/>
  <text x="255" y="193" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Face Detection</text>
  
  <rect x="190" y="210" width="130" height="20" fill="white" stroke="black" stroke-width="1"/>
  <text x="255" y="223" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Face Cropping</text>
  
  <rect x="190" y="240" width="130" height="20" fill="white" stroke="black" stroke-width="1"/>
  <text x="255" y="253" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Saving the face cropped video</text>
  
  <!-- Processed Dataset -->
  <ellipse cx="450" cy="200" rx="70" ry="50" fill="none" stroke="black" stroke-width="2"/>
  <text x="450" y="190" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Processed</text>
  <text x="450" y="203" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Dataset</text>
  <text x="450" y="216" font-family="Arial, sans-serif" font-size="9" text-anchor="middle">(Contains only face video)</text>
  
  <!-- Data Splitting -->
  <rect x="580" y="150" width="100" height="40" fill="white" stroke="black" stroke-width="2"/>
  <text x="630" y="165" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Data Splitting</text>
  <text x="630" y="178" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Train / Test data</text>
  <text x="630" y="188" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">split</text>
  
  <!-- Data Loader -->
  <rect x="580" y="220" width="100" height="40" fill="white" stroke="black" stroke-width="2"/>
  <text x="630" y="235" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Data Loader</text>
  <text x="630" y="248" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Loading the Train</text>
  <text x="630" y="258" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">videos and labels</text>
  
  <!-- Main Model Box -->
  <rect x="400" y="320" width="300" height="140" fill="none" stroke="black" stroke-width="2"/>
  <text x="550" y="340" font-family="Arial, sans-serif" font-size="12" font-weight="bold" text-anchor="middle">Deepfake Detection Model</text>
  
  <!-- LSTM -->
  <rect x="420" y="350" width="80" height="40" fill="white" stroke="black" stroke-width="2"/>
  <text x="460" y="365" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">LSTM</text>
  <text x="460" y="378" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Video classification</text>
  
  <!-- ResNext -->
  <rect x="520" y="350" width="80" height="40" fill="white" stroke="black" stroke-width="2"/>
  <text x="560" y="365" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">ResNext</text>
  <text x="560" y="378" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Feature extraction</text>
  
  <!-- Train/Test label -->
  <text x="530" y="310" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Train / Test the Model</text>
  
  <!-- Model Evaluation -->
  <text x="320" y="380" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Model</text>
  <text x="320" y="393" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Evaluation</text>
  
  <!-- Confusion Matrix -->
  <rect x="270" y="400" width="100" height="30" fill="white" stroke="black" stroke-width="2"/>
  <text x="320" y="418" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Confusion Matrix</text>
  
  <!-- Load Trained Model -->
  <rect x="180" y="400" width="80" height="30" fill="white" stroke="black" stroke-width="2"/>
  <text x="220" y="418" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Load Trained Model</text>
  
  <!-- Export Trained Model -->
  <rect x="270" y="450" width="100" height="30" fill="white" stroke="black" stroke-width="2"/>
  <text x="320" y="468" font-family="Arial, sans-serif" font-size="10" text-anchor="middle">Export Trained Model</text>
  
  <!-- Final Output -->
  <rect x="380" y="580" width="100" height="40" fill="white" stroke="black" stroke-width="2"/>
  <text x="430" y="603" font-family="Arial, sans-serif" font-size="12" font-weight="bold" text-anchor="middle">REAL / FAKE</text>
  
  <!-- Training Flow Arrows (Black) -->
  <line x1="140" y1="200" x2="175" y2="200" stroke="black" stroke-width="2" marker-end="url(#arrowhead)"/>
  <line x1="335" y1="200" x2="375" y2="200" stroke="black" stroke-width="2" marker-end="url(#arrowhead)"/>
  <line x1="525" y1="200" x2="575" y2="170" stroke="black" stroke-width="2" marker-end="url(#arrowhead)"/>
  <line x1="630" y1="195" x2="630" y2="215" stroke="black" stroke-width="2" marker-end="url(#arrowhead)"/>
  <line x1="630" y1="265" x2="550" y2="315" stroke="black" stroke-width="2" marker-end="url(#arrowhead)"/>
  <line x1="500" y1="370" x2="515" y2="370" stroke="black" stroke-width="2" marker-end="url(#arrowhead)"/>
  <line x1="420" y1="370" x2="370" y2="390" stroke="black" stroke-width="2" marker-end="url(#arrowhead)"/>
  <line x1="320" y1="400" x2="320" y2="395" stroke="black" stroke-width="2" marker-end="url(#arrowhead)"/>
  <line x1="320" y1="435" x2="320" y2="445" stroke="black" stroke-width="2" marker-end="url(#arrowhead)"/>
  <line x1="270" y1="415" x2="265" y2="415" stroke="black" stroke-width="2" marker-end="url(#arrowhead)"/>
  
  <!-- Prediction Flow Arrows (Red Dashed) -->
  <line x1="410" y1="55" x2="255" y2="115" stroke="red" stroke-width="2" stroke-dasharray="5,5" marker-end="url(#arrowhead-red)"/>
  <line x1="255" y1="285" x2="220" y2="395" stroke="red" stroke-width="2" stroke-dasharray="5,5" marker-end="url(#arrowhead-red)"/>
  <line x1="220" y1="435" x2="320" y2="575" stroke="red" stroke-width="2" stroke-dasharray="5,5"/>
  <line x1="320" y1="485" x2="380" y2="575" stroke="red" stroke-width="2" stroke-dasharray="5,5" marker-end="url(#arrowhead-red)"/>
</svg>
