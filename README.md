# 📈 Google Stock Price Trend Prediction using RNN (LSTM)

This project demonstrates how to use a Recurrent Neural Network (RNN), specifically Long Short-Term Memory (LSTM), to predict **trends** in Google’s stock price. Rather than forecasting the exact price (which is highly unpredictable due to market volatility), this model aims to learn from historical price data and predict **upward** or **downward** trends.

---

## 🧠 Problem Statement

Stock market prices are highly volatile and influenced by many unpredictable external factors, making exact prediction nearly impossible. However, using historical patterns, it's feasible to **predict the direction of movement**—whether the stock price will go up or down in the near future.

This project focuses on using LSTM to detect these **directional trends** in Google’s stock prices by analyzing the **"Open" price** over a sliding window of 60 days.

---

## 📁 Folder Structure

RNN/
│
├── Google_Stock_Price_Train.csv # Contains Google stock prices from 2012 to 2016
├── Google_Stock_Price_Test.csv # Contains Google stock prices from January 2017
└── rnn.ipynb # Jupyter Notebook containing complete model code


Each CSV file should include the following columns:
- `Date`
- `Open` (used as input feature)
- `High`
- `Low`
- `Close`
- `Volume`

The model uses only the **Open** price for learning and prediction.

---

## 📊 Dataset Description

- **Training Set:** `Google_Stock_Price_Train.csv`
  - Time period: **2012 to 2016**
  - Used to train the model using sequences of the past 60 days to predict the 61st day's "Open" price.
  
- **Test Set:** `Google_Stock_Price_Test.csv`
  - Time period: **January 2017**
  - Used to evaluate how well the model can generalize and predict future trends.

---

## 🛠️ Model Architecture & Workflow

1. **Data Preprocessing**
   - Extract "Open" prices.
   - Normalize values using `MinMaxScaler` to scale between 0 and 1.
   - Create sequences of 60-day windows to predict the next day’s open price.

2. **Model Architecture**
   - 4 stacked LSTM layers, each with 50 units.
   - `Dropout(0.2)` after each layer to prevent overfitting.
   - Final output layer: 1 neuron (predicts one float value — the scaled open price).

3. **Training**
   - Optimizer: `adam`
   - Loss function: `mean_squared_error`
   - Epochs: 100
   - Batch size: 32

4. **Prediction**
   - The last 60 days of training data + test data are used to predict each value in January 2017.
   - Predictions are inverse-transformed to original price scale.

5. **Visualization**
   - Plots actual vs predicted stock prices using `matplotlib`.

---

## 📈 Output

The notebook generates a graph comparing:
- 🔴 **Actual Google Stock Opening Prices (Jan 2017)**
- 🔵 **Predicted Google Stock Opening Prices**

This helps visualize how well the model was able to learn and generalize the trend patterns from past data.

---

## 💻 Requirements

Install all required packages using:

```bash
pip install numpy pandas matplotlib scikit-learn keras tensorflow

⚠️ Disclaimer
This model is created purely for educational purposes and should not be used for real-world financial trading or investments. The stock market is influenced by complex external events and this model does not factor in such variables.

📚 Credits
Stock data source: [Google Finance Dataset via CSV]
LSTM implementation using Keras & TensorFlow

🙋‍♂️ Contact For queries or feedback, feel free to reach out via email or GitHub issues.
