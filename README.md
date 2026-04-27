# German CEFR Level Prediction using Machine Learning

This project implements a machine learning model designed to predict the **Common European Framework of Reference for Languages (CEFR)** proficiency level of German sentences. The system classifies input text into categories from **A1 (Beginner)** through **C1 (Advanced)**.

## Project Overview
The core objective is to provide an automated way to assess the difficulty of German text. Due to data scarcity, C2 level data was merged into the C1 category for this implementation.

## Technical Strategy
* **Algorithm:** Linear Support Vector Classification (LinearSVC).
* **Vectorization:** TF-IDF (Term Frequency-Inverse Document Frequency).
* **Feature Engineering:** Utilizes character n-grams (3-5 characters) to effectively capture the complex morphological features common in the German language.
* **Performance:** Achieved an accuracy of **80.44%** using a stratified 80/20 train/test split.

## Dataset & Pipeline
The final dataset consists of **2,249 unique sentences**.

### Data Sources
* **Merlin Corpus:** Extracted from raw .txt files, providing foundational real-world learner data.
* **Hugging Face:** Publicly available datasets added to increase volume and variety, including `UniversalCEFR/elg_cefr_de` and `EliasAhl/german-cefr`.

### Preprocessing & Augmentation
* **Cleaning:** Standardized input by removing multiple newlines, PII like postal codes, boilerplate salutations, and extra whitespace.
* **Augmentation:** Addressed class imbalance for minority classes (A1, C1) using **Back-Translation** (DE to EN to DE) via Google Translator.

## Usage
The project includes an interactive script that loads the serialized model to predict levels for user input.

```python
# Example Usage
text = "Ich denke, dass wir mehr für den Umweltschutz tun sollten."
print(predict_cefr(text))
# Output: C1
