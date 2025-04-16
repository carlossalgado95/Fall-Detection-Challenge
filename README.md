# 🧍‍♂️ Fall Detection Challenge

## 📊 Dataset
The dataset contains inertial sensor data (accelerometer and gyroscope) labeled as:
- **ADL** (Activities of Daily Living)
- **Fall**
- **Near Fall**

## 🔄 Preprocessing
- Removal of missing values
- Feature creation: **acceleration magnitude**
- Sliding window segmentation: **window size = 128**, **stride = 64**
- Feature-wise normalization using `StandardScaler`
- Train-test split (80/20 with stratification)

## 🛠️ Feature Engineering
- `acc_magnitude = sqrt(x² + y² + z²)`
- (Optional) Window-level statistical features: mean, std, etc.

## 🧠 Model
A hybrid approach was adopted:
- A **1D Convolutional Neural Network (CNN)** was used to extract temporal features from the sensor data.
- A **Random Forest** classifier was trained on these deep features to classify fall events.

This approach combines temporal pattern learning with model interpretability and low computational cost.

## 🧪 Evaluation
Metrics computed on the test set:

| Class     | Precision | Recall | F1-score |
|------------|-----------|--------|----------|
| ADL        | 0.96      | 0.97   | 0.97     |
| Fall       | 0.90      | 0.84   | 0.87     |
| Near Fall  | 0.8      | 0.86   | 0.83     |
| **Accuracy** |           |        | **0.90**  |

> The model achieved **high accuracy and balanced performance across classes**, even in the presence of class imbalance.

## ⚠️ Challenges
- **Class imbalance** (more ADL samples than falls)
- **Sensor noise** and subject variability
- Inconsistent column names across `.xlsx` files

## 🧭 Future Improvements
- Experiment with sequential models: **LSTM**, **GRU**, or **Transformers**
- Apply **data augmentation** for fall and near-fall cases
- Use **subject-wise cross-validation** for better generalization
- Real-time deployment on **IoT or wearable devices**

## ▶️ How to Run

```bash
git clone https://github.com/your-username/your-repo.git
cd your-repo
pip install -r requirements.txt
python train.py

