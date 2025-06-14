# **DREAM-FLUTE: Enhancing Commonsense Reasoning and Figurative Language Understanding in NLP**

This repository implements **DREAM-FLUTE**, a method designed to enrich commonsense reasoning in NLP by integrating the **DREAM elaboration model** with **T5-BASE** and **BERT**. It focuses on combining multiple systems to improve performance on the Commonsense QA task using elaborations and textual explanations.

---

## 🚀 Project Summary

**DREAM-FLUTE** addresses the challenge of limited context understanding in large language models by using elaborations generated by DREAM. These elaborations enhance the input data, improving model performance in commonsense reasoning and figurative language tasks.

* **Objective**: Improve model reasoning and explainability for multiple-choice QA tasks.
* **Methods**: Combine DREAM-generated elaborations with BERT and T5-BASE pipelines.
* **Dataset**: Uses a preformatted version of the CoS-E dataset.

---

## 🗂️ Directory Structure

```bash
dream-flute/
├── formatted_dataset/
│   ├── train/
│   │   ├── *.arrow
│   │   └── dataset_info.json, state.json
│   ├── validation/
│   │   ├── *.arrow
│   │   └── dataset_info.json, state.json
│   └── dataset_dict.json
│
├── bert.ipynb                        # BERT fine-tuning without elaboration
├── bert_with_eloboration.ipynb      # BERT fine-tuning with DREAM elaborations
├── cos-e_t5_fine-tuning_and_generate_elaboration.ipynb  # T5 fine-tuning + elaboration
├── using_dream_for_elaboaration.ipynb  # Generates elaborations using DREAM
├── README.md
```

---

## 🧠 System Components

### 🔹 **System 1: BERT Fine-Tuning (Classification)**

* **Notebook**: `bert.ipynb`
* **Dataset**: Preformatted CoS-E in `formatted_dataset/`
* **Goal**: Predict the correct choice among multiple answers.

### 🔹 **System 1 Extended: BERT + Elaboration**

* **Notebook**: `bert_with_eloboration.ipynb`
* **Function**: Incorporates DREAM elaborations into input for BERT classification.
* **Finding**: Minimal improvement observed compared to baseline.

### 🔹 **System 2: T5-BASE + Elaboration Generation**

* **Notebook**: `cos-e_t5_fine-tuning_and_generate_elaboration.ipynb`
* **Function**: Uses T5 to generate both answer and explanation from elaboration-augmented input.
* **Output**: Classification label and human-like textual explanation.

### 🔹 **DREAM Elaboration Generation**

* **Notebook**: `using_dream_for_elaboaration.ipynb`
* **Function**: Dynamically generates scene elaborations based on CoS-E questions.
* **Purpose**: Augment inputs with rich commonsense context.

---

## 📊 Results Snapshot

| Model                 | Accuracy\@0 |
| --------------------- | ----------- |
| BERT (Baseline)       | 0.2039      |
| BERT + Elaboration    | 0.2048      |
| T5-BASE               | 0.3604      |
| T5-BASE + Elaboration | 0.4046      |

🔎 **Insight**: T5-BASE shows significant gains with elaborations. BERT benefits less, suggesting generation-based models leverage context more effectively.

---

## 📦 Requirements

* Python ≥ 3.8
* `transformers`, `datasets`, `torch`, `tensorflow`, `tqdm`, `scikit-learn`

Install with:

```bash
pip install -r requirements.txt
```

---

## ▶️ Running the Project

1. **Download and prepare dataset** (already included as `formatted_dataset/`)
2. **Run DREAM elaboration generation**:

   ```bash
   # Or open: using_dream_for_elaboaration.ipynb
   ```
3. **Fine-tune models**:

   * BERT:

     ```bash
     # bert.ipynb or bert_with_eloboration.ipynb
     ```
   * T5 with elaboration:

     ```bash
     # cos-e_t5_fine-tuning_and_generate_elaboration.ipynb
     ```

---


## 🔗 Resources & References

* [DREAM (Gu et al., 2021)](https://arxiv.org/abs/2112.08656)
* [FLUTE (Chakrabarty et al., 2022)](https://arxiv.org/abs/2205.12404)
* [T5 (Raffel et al., 2020)](https://arxiv.org/abs/1910.10683)
* [CoS-E Dataset](https://github.com/salesforce/cos-e)
