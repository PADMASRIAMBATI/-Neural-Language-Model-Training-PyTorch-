## 📄 `README.md`: NLM Training and Generalization Study

# Neural Language Model Training

## 🎯 Objective
To implement and train a Causal Neural Language Model (NLM) from scratch using PyTorch and demonstrate fundamental concepts of deep learning generalization by running controlled experiments that showcase **Underfitting**, **Overfitting**, and **Optimal Fit**.

## ⚙️ Project Setup and Reproducibility

### 1. Code & Access
The entire project, including data loading, preprocessing, model definitions, and comparative training loops, is contained within the Colab notebook.

* **Code File:** `Assignment-2.ipynb` (Included in this repository)
* **Execution Environment:** Designed for Google Colab (CUDA enabled).

### 2. Reproducibility Guarantee
Per assignment rules, all random processes are fixed to ensure full reproducibility.

* **Fixed Seed:** **42**
* **Implementation:** All components (tokenization, batching, model, training loop, PPL metric) were implemented *from scratch* using only standard PyTorch (`torch.nn`, `torch.optim`) and Python libraries.

### 3. Dataset (Exclusive Use)
* **Source:** Jane Austen's *Pride and Prejudice* (Exclusively the file provided via Google Drive).
* **Preprocessing:** Custom Word-level tokenization.
* **Final Vocabulary Size:** **3,206**

## 🧠 Model Implementation & Experimental Results

### Architecture Summary
* **Model Core:** Gated Recurrent Unit (GRU)
* **Objective:** Causal Language Modeling
* **Evaluation Metric:** Perplexity ($PPL = e^{\text{Average Cross-Entropy Loss}}$)

### Comparative Analysis of Model Fitting

The three models were configured to explicitly map to the "Understanding Checkpoints" (See the **Report** for plot visualization and analysis).

| Scenario | Configuration (Layers/Hidden/Dropout) | Key Training Dynamics | Final Val PPL |
| :--- | :--- | :--- | :--- |
| **1. Underfitting** | 1 / 32 / 0.0 (Low Capacity/Effort) | Train Loss stabilized quickly but remained high (> 3.5). **High Bias.** | **626.20** |
| **2. Overfitting** | 3 / 512 / 0.0 (High Capacity/No Reg.) | Train Loss $\to 0.078$. Val Loss **exploded past 15.0** after Epoch 6. **High Variance.** | **5,610,373.00** |
| **3. Best Fit** | 2 / 256 / 0.3 (Tuned/Regularized) | Val Loss dropped rapidly and was stabilized by Dropout. | **275.39** |

---

## 🏆 Conclusion and Final Metrics

### Final Selected Model (Model 3, Optimal Point)
The configuration designed for **Best Fit** achieved the lowest generalization error, demonstrating the optimal trade-off between model learning and prevention of noise memorization.

* **Optimal Configuration:** 2-Layer GRU, Hidden Size 256, Dropout 0.3
* **Optimal Validation Perplexity (PPL):** **275.39** (Observed at Epoch 1)
* **Analytical Rationale:** The low initial PPL highlights that the optimized capacity (Layer=2, Hidden=256) was sufficient to learn the corpus structure almost immediately. The rapid drop in PPL confirms the efficacy of the tuning parameters.

***

### 📌 Deliverables Checklist

| Item | Status | Notes |
| :--- | :--- | :--- |
| **Code (Training Script/Model)** | ✅ **Complete** | All code pushed to this repository. |
| **Plots (Loss Curves)** | ✅ **Complete** | Included in the separate final report document. |
| **Report (Analysis)** | ✅ **Complete** | Concise analysis submitted via Google Form. |
| **Reproducibility** | ✅ **Complete** | Fixed seed (42) implemented. |
| **Dataset Rule** | ✅ **Complete** | Only the provided text was used. |

***
