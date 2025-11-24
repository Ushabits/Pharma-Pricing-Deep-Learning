# Multimodal Two-Tower Network for Pharmaceutical Pricing 💊

**A Deep Learning System to Decouple Brand Equity from Production Costs**

## 📌 Project Overview
The Indian pharmaceutical market is characterized by a "Branded Generic" paradox, where identical chemical molecules vary in price by up to **26x** based on manufacturer reputation. Traditional regression models fail to capture this non-linear "Brand Premium."

This project implements a **Multimodal Two-Tower Neural Network** to simultaneously solve two conflicting tasks:
1.  **Price Regression:** Predicting the exact retail price (Hard Cost).
2.  **Tier Classification:** Categorizing drugs into Value, Mid-Range, or Premium tiers (Soft Cost).

---

## 🚀 The Architecture: Solving "Negative Transfer"
Early experiments with standard neural networks failed due to **Negative Transfer**—the features needed to *group* drugs (abstract brand perception) conflicted with the features needed to *count* costs (linear arithmetic).

To solve this, I architected a **Two-Tower Network**:



* **Tower A (The Classifier):** A Deep Network that learns abstract market positioning to predict **Pricing Tiers**.
* **Tower B (The Regressor):** A Shallow, Linear Network that learns ingredient arithmetic (`Pack Size` × `Strength`) to predict **Exact Price**.

This decoupled approach prevents gradient interference, allowing the model to master both "Math" and "Marketing" simultaneously.

---

## 📊 Results & Performance

| Metric | Result | Context |
| :--- | :--- | :--- |
| **Price Prediction (MAE)** | **₹178.44** | High precision given prices range up to ₹50,000. |
| **Tier Accuracy** | **77.4%** | Successfully distinguishes Premium vs. Value segments. |
| **Optimization** | **Weighted Loss** | Balanced gradients using $\lambda_{tier}=1.0, \lambda_{price}=0.05$. |
<img width="708" height="371" alt="Model Output Metrics" src="https://github.com/user-attachments/assets/d139a082-649f-4f23-8bcf-920710d595ea" />


### 🔍 Key Insight: Anomaly Detection
The model validates the **"Branded Generic"** phenomenon (identified by *Ghooi et al., 2025*). The gap between the *Predicted Price* (based on ingredients) and *Actual Price* serves as an automated signal for **Price Gouging**, flagging products with excessive marketing markups.

---

## 🛠️ Tech Stack
* **Deep Learning:** TensorFlow, Keras (Functional API)
* **Architecture:** Multi-Task Learning (MTL), Two-Tower Networks, Embeddings
* **Data Processing:** Pandas, Scikit-Learn (StandardScaler, LabelEncoder)

---

## 📂 Usage
1. Install dependencies:
   ```bash
   pip install -r requirements.txt
