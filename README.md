# melanin-superstructures-ml
# Prediction of Melanin Superstructures using Machine Learning

This repository contains the code and implementation details for my Bachelor's Thesis (TFG) developed at the University of Girona (UdG). The project focuses on applying Machine Learning and Deep Learning techniques to predict and analyze the properties of melanin superstructures.

---

## 🧬 Biological Problem Solved
Melanin pigments present complex molecular architectures and superstructures that dictate their physicochemical behavior. The main objective of this project was to build a robust predictive model capable of mapping molecular and structural features (input descriptors) to target biological/chemical properties (`labels`), accelerating the analysis without relying exclusively on expensive computational chemistry simulations.

---

## 🛠️ Machine Learning Approach & Architecture
To tackle this regression problem, a custom Deep Neural Network (DNN) was implemented using **PyTorch**. 

* **Data Preprocessing:** 
  * Dataset loaded from chemical descriptor files (features $x_1$ to $x_24$).
  * Features cleaned and scaled using `StandardScaler`.
  * Dataset split into three distinct subsets to prevent data leakage: **Training (68%)**, **Validation (17%)**, and **Test (15%)**.
* **Model Architecture (`MolNetImproved`):**
  * Input Layer: 24 features.
  * Hidden Layers: Sequential linear layers with decreasing dimensions ($128 \to 64 \to 32$) interspersed with `ReLU` activations and `Dropout (0.1)` for regularization to prevent overfitting.
  * Output Layer: 1 continuous target variable.
* **Training Strategy:**
  * **Optimizer:** Adam (Initial Learning Rate: $0.005$).
  * **Scheduler:** `StepLR` (decaying learning rate by a factor of 0.5 every 100 epochs).
  * **Loss Function:** Mean Squared Error (MSE).
  * **Batch Size:** 128 (using PyTorch `DataLoader`).

---

## 📊 Evaluation Metrics & Results
The model was evaluated on an unseen Test set to measure true generalization performance:

* **Final Test MSE Loss:** `0.1397`[cite: 1]
* **Mean Absolute Error (MAE):** `0.0376 units`[cite: 1]

### Real vs. Predicted Comparison (Test Set Examples)
| Real Value | Predicted Value |
| :---: | :---: |
| 0.5653 | 0.5676[cite: 1] |
| 0.5229 | 0.5398[cite: 1] |
| 0.5205 | 0.5219[cite: 1] |
| 0.4632 | 0.4758[cite: 1] |
| 0.3007 | 0.3177[cite: 1] |

---

## 📈 Performance Visualization
*(Aquí puedes arrastrar y soltar la imagen de la gráfica de dispersión "Real vs Predicció" que generaste con matplotlib en tu notebook).*
