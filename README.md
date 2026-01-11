## Intelligent Plant Disease Detection for Sustainable Agriculture

### ✅ Week 1: Foundation & Data Pipeline
## 📅 Weekly Progress Log

**Status:** Completed
**Focus:** Data Ingestion, Preprocessing, and Research Setup

**Key Activities:**
- **Project Scope Definition:** Defined the problem statement targeting **Potato Leaf Diseases** (Early Blight, Late Blight, Healthy), aligning with **SDG 2: Zero Hunger**.
- **Data Acquisition:** - Sourced the **PlantVillage** dataset (Potato subset) from Kaggle.
  - Uploaded data to Google Drive for persistent access in Colab.
- **Pipeline Implementation:** - Wrote a custom data loader using `tf.keras.preprocessing.image_dataset_from_directory`.
  - Standardized all input images to **256x256 pixels** for consistency.
  - Implemented an **80/10/10 Split** (Train/Validation/Test) to ensure rigorous evaluation.
- **Optimization:** - Applied `cache()` and `prefetch(AUTOTUNE)` to optimize data loading speed during training.

**Challenges Faced & Solutions:**
- **Challenge:** Understanding GitHub version control workflow.
  - *Solution:* Established a structured commit history for code files.
- **Challenge:** Limited hardware resources.
  - *Solution:* Configured Google Colab Environment to utilize Cloud GPU.

**Outcome:** A robust, error-free data pipeline is now ready. The system successfully loads images, splits them into batches, and visualizes class labels.

### ✅ Week 2: Model Architecture & Training
**Status:** Completed
**Focus:** Custom CNN Development and Stability Testing

**Key Activities:**
- **Architecture Design:** Designed a deep **Custom CNN** (5 Convolutional Blocks) from scratch.
  - *Constraint Check:* Strictly avoided pre-trained models (ResNet/VGG) to adhere to research guidelines.
  - *Innovation:* Integrated `RandomFlip` and `RandomRotation` layers directly into the model to improve generalization.
- **Scientific Stability:** Implemented "Seed Locking" (Seed=42) for Python, NumPy, and TensorFlow to ensure the model training is reproducible and stable.
- **Training Strategy:**
  - **Optimizer:** Adam (Adaptive Learning Rate).
  - **Epochs:** 25 (Selected empirically to prevent overfitting).
  - **Loss Function:** Sparse Categorical Crossentropy.

**Challenges Faced & Solutions:**
- **Challenge:** Determining the optimal number of training epochs.
  - *Analysis:* Training beyond 30 epochs caused the validation loss to fluctuate ("jumpy"), indicating overfitting.
  - *Solution:* Capped training at **25 Epochs**, where the model achieved maximum stability.

**Outcome:**
- Final Model: `potato_disease_final_model.keras`
- **Test Accuracy Achieved:** 91.41% (Excellent baseline for a custom architecture)

### 📊 Week 2 Visuals: Research Evidence
**1. Training Stability (Accuracy vs Loss)**
> *This graph demonstrates that the model learned effectively without memorizing noise (overfitting).*
![Training Graph](accuracy_loss_graph.png)

**2. Confusion Matrix (Error Analysis)**
> *This matrix reveals exactly which disease classes the model predicts correctly vs. incorrectly.*
![Confusion Matrix](confusion_matrix.png)

### ✅ Week 3: Inference, Optimization & Advanced Evaluation
**Status:** Completed
**Focus:** Inference Deployment, Statistical Validation (ROC), and Explainable AI

**Key Activities:**
- **Inference Engine Simulation:**
  - Developed a production-ready `predict_disease()` function that accepts raw images and outputs disease probability.
  - Successfully loaded the saved `.keras` model to simulate a real-world deployment scenario.
- **Stress Testing ("Farmer Scenarios"):**
  - **Single Sample Test:** Verified the model correctly identifies individual leaves with high confidence (>90%).
  - **Batch Processing:** Tested high-volume throughput (32 images at once).
  - **Uncertainty Analysis:** Implemented a flag to alert the user if model confidence drops below 80%.
- **Statistical Validation:**
  - **ROC Curve:** Generated the Receiver Operating Characteristic curve to scientifically validate the model's sensitivity.
  - **Result:** High Area Under Curve (AUC) confirms the model is robust against False Positives.
- **Performance Optimization:**
  - Conducted a **Latency Test** on the GPU.
  - **Result:** Average inference speed is **< 50ms per image**, confirming suitability for real-time mobile apps.
- **Explainable AI (XAI):**
  - Visualized the **Internal Feature Maps** of the first Convolutional Layer.
  - Confirmed the model is learning actual leaf textures (edges/spots) and not memorizing background noise.

**Challenges Faced & Solutions:**
- **Challenge:** Visualizing internal model layers ("Explainability").
  - *Issue:* Attempting to plot feature maps caused an `IndexError` because the code initially selected the "Rescaling" layer instead of the "Convolutional" layer.
  - *Solution:* Wrote a dynamic script to specifically search for and extract the first `Conv2D` layer automatically.

**Outcome:**
- A fully tested, optimized, and statistically validated inference system.
- **Visual Proof:**
  - **ROC Curve:** `roc_curve.png` (Statistical Proof)
  - **Feature Maps:** `feature_maps.png` (Explainability Proof)

### 📊 Week 3 Visuals: Advanced Analysis
**1. ROC Curve (Statistical Validation)**
> *Demonstrates the trade-off between True Positive Rate and False Positive Rate. High AUC indicates excellent performance.*
![ROC Curve](roc_curve.png.png)

**2. Internal Feature Maps (Explainable AI)**
> *Visualizes the internal filters of the first Convolutional Layer, proving the AI focuses on leaf edges and disease spots.*
![Feature Maps](feature_maps.png)

### ✅ Week 4: Final Presentation & Documentation
**Status:** Completed
**Focus:** Project Polish, Demo Video, and Final Reporting

**Key Activities:**
- **Project Demo Video:** Recorded a comprehensive screen-capture demonstrating:
  - The "Inference Engine" predicting diseases on new images.
  - The "Feature Maps" visualization to explain the model's logic.
  - The speed and stability of the system.
- **Short Project Report:** Compiled a formal document detailing the methodology, optimization steps, and statistical validation (ROC/AUC).
- **Literature Review:** Conducted an extensive review of 10 recent research papers (2024-2025) to align the project with current academic standards.

**Outcome:**
- A complete, "Research-Grade" GitHub repository ready for submission.
- **Deliverables:** `Project_Short_Report1.doc`,

---

### 📚 Literature Review (2024-2025)
*State-of-the-art research papers referenced for this project (Direct Links Included):*

1.  **[Deep learning and explainable AI for classification of potato leaf diseases (2024)](https://www.frontiersin.org/journals/artificial-intelligence/articles/10.3389/frai.2024.1449329/full)**
    * *Journal:* Frontiers in Artificial Intelligence
    * *Relevance:* Validates the use of Explainable AI (XAI) to interpret model decisions, similar to our Feature Map visualization.

2.  **[Potato Leaf Disease Detection Based on a Lightweight Deep Learning Model (2024)](https://www.mdpi.com/2504-4990/6/4/114)**
    * *Journal:* MDPI AgriEngineering
    * *Relevance:* Supports our choice of a lightweight custom CNN for efficient mobile deployment (0.40 GFLOPs).

3.  **[Enhancing plant disease detection through deep learning: a Depthwise CNN (2025)](https://www.frontiersin.org/journals/plant-science/articles/10.3389/fpls.2024.1505857/full)**
    * *Journal:* Frontiers in Plant Science
    * *Relevance:* Confirms that depthwise separable convolutions improve efficiency without sacrificing accuracy.

4.  **[A review of plant leaf disease identification by deep learning algorithms (2025)](https://www.frontiersin.org/journals/plant-science/articles/10.3389/fpls.2025.1637241/full)**
    * *Journal:* Frontiers in Plant Science
    * *Relevance:* Provided the foundation for our Data Augmentation strategy to handle background noise.

5.  **[Unified Lightweight CNN-Based Model for Multi-Crop Disease Detection (2024)](https://ijsem.org/article/9%20April%202024%20IJSEM.pdf)**
    * *Journal:* IJSEM
    * *Relevance:* Demonstrates that custom architectures can effectively handle multiple crop types (Rice, Wheat, Corn).

6.  **[Plant disease detection using vision transformers (2025)](https://www.researchgate.net/publication/388397435_Plant_disease_detection_using_vision_transformers)**
    * *Journal:* International Journal of Electrical and Computer Engineering (IJECE)
    * *Relevance:* A benchmark study comparing CNNs (our approach) against newer Vision Transformers (ViTs).

7.  **[Research on a Potato Leaf Disease Diagnosis System Based on Deep Learning (2025)](https://www.mdpi.com/2077-0472/15/4/424)**
    * *Journal:* MDPI Agriculture
    * *Relevance:* Highlights the economic importance of early detection for potato yield optimization.

8.  **[Comparative Study of Lightweight CNN Architectures for Maize Leaf Disease Detection (2025)](https://www.researchgate.net/publication/389526803_Comparative_Study_of_Lightweight_CNN_Architectures_for_Maize_Leaf_Disease_Detection)**
    * *Journal:* European Journal of Applied Science
    * *Relevance:* Validates the trend of comparing custom models against MobileNetV3 for edge devices.

9.  **[Multi-Class Plant Leaf Disease Detection: A CNN-based Approach (2024)](https://www.researchgate.net/publication/383494704_Multi-Class_Plant_Leaf_Disease_Detection_A_CNN-based_Approach_with_Mobile_App_Integration)**
    * *Journal:* International Journal of Computer Applications
    * *Relevance:* Discusses the integration of CNN models into mobile apps, aligning with our Week 3 latency testing.

10. **[Deep Learning Based Multi Crop Disease Detection System (2024)](https://journal.50sea.com/index.php/IJIST/article/view/944)**
    * *Journal:* International Journal of Innovations in Science & Technology
    * *Relevance:* Emphasizes the role of edge computing in modern agriculture.

---

### 👨‍💻 Author Details
**Student Name:** Shah Zaib Khan
**Roll Number:** SU92-MSAIW-S25-019
**Program:** Master of Science in Artificial Intelligence (MSAI)

**Submitted To:** Sir Talha
**Institution:** Superior University
