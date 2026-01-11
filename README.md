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
