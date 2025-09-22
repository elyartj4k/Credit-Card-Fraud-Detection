### 💳 Credit Card Fraud Detection API

This repository contains a Flask API for credit card fraud detection, powered by a machine learning model. It includes pre-trained models, data preprocessing tools, and a simple API for making predictions. This project is a proof of concept and is intended for educational and experimental purposes.

-----

### ⚠️ A Note on the Dataset

This project uses a dataset from the **MLG - ULB Credit Card Fraud Detection** Kaggle competition. For security and privacy, the original features have been replaced with derived features obtained through Principal Component Analysis (PCA).

The model's performance may vary in real-world scenarios, so feel free to use it as a starting point and adapt it to your specific data and requirements. Always handle sensitive data with caution\! 🛡️

-----

### 📂 Project Layout

Here's a quick look at the project's folder structure:

  * `testcode/`: A folder containing `sample.py` to test the API.
  * `model/source-model.ipynb`: A Jupyter Notebook detailing the model's development and training.
  * `app.py`: The core Flask application file.
  * `model.h5`: The pre-trained fraud detection model.
  * `requirements.txt`: Lists all the necessary Python packages.
  * `vectorizer.pkl`: A pre-trained data preprocessing tool.
  * `README.md`: You're reading it\!

-----

### 🚀 Get Started\!

Follow these steps to get the API running locally:

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/NotSooShariff/CC-Fraud-Detection.git
    ```

2.  **Navigate to the project:**

    ```bash
    cd credit-card-fraud-detection
    ```

3.  **Install dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

4.  **Run the Flask app:**

    ```bash
    python app.py
    ```

    Your API will be live at `http://127.0.0.1:5000`.

5.  **Expose your API to the web:**
    You can use [ngrok](https://ngrok.com/) to create a public URL for your local server.

      * Download and install ngrok.
      * Configure your auth token using `ngrok config add-authtoken YOUR_AUTH_TOKEN`.
      * Create a tunnel to your API:

    <!-- end list -->

    ```bash
    ngrok http 5000
    ```

    Use the provided "Forwarding" URL from ngrok to make calls from anywhere\! 🌐

-----

### 🧠 The Brain Behind the API: Model Explained

The fraud detection model was meticulously developed in the `source-model.ipynb` notebook. Here's a brief overview of the process:

  * **Data Prep:** Loaded and cleaned a dataset with anonymized features.
  * **EDA:** Explored data distributions, especially the balance of fraudulent vs. non-fraudulent transactions.
  * **Scaling:** Applied **RobustScaler** to handle outliers in the "Amount" feature.
  * **Training:** Trained several models, including **Logistic Regression, Random Forest, Gradient Boosting**, and **SVC**.
  * **Evaluation:** Assessed model performance using metrics like **accuracy, precision, recall**, and **F1-score**.
  * **Imbalance Handling:** Used oversampling and undersampling to ensure fair training on imbalanced data.
  * **Fine-tuning:** Optimized hyperparameters to enhance the model's performance.

-----

### 🌐 API Endpoint

The API has a single endpoint for making predictions:

#### `/predict` (POST)

  * **Request Header:** `ngrok-skip-browser-warning: true` (Required for ngrok)

  * **Request Body (JSON):**

    ```json
    {
        "data": {
            "V1": -1.359807,
            "V2": -0.072781,
            "V3": 2.536347,
            ...
            "V28": -0.021053,
            "Amount": 149.62,
            "Time": 1
        }
    }
    ```

  * **Response:**

      * `1`: Fraudulent transaction. 🚩
      * `0`: Not fraudulent. ✅

-----

### ✨ Example Usage

1.  Ensure the Flask API and ngrok are running.

2.  Navigate to the `testcode/` folder:

    ```bash
    cd testcode/
    ```

3.  Run the sample script with your transaction data:

    ```bash
    python sample.py
    ```

    This script sends a request and prints the prediction:

    ```
    Prediction: 0.0 --> Not Fraud
    ```

-----

### 🙏 A Big Thank You\!

This project would not have been possible without the excellent tutorials from **Gregg Hogg's YouTube channel**. His content on machine learning was a major inspiration\! 👏

-----

### 🤝 Contributions

Got an idea to improve this project? Found a bug? Feel free to **fork** this repository, make your changes, and submit a **pull request**\! Let's build something great together. 🚀