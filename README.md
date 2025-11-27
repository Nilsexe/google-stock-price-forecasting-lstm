# 📈 Google Stock Price Forecasting Using LSTM  
*A Deep Learning Approach to Time-Series Prediction*

<p align="center">
  <img src="https://img.shields.io/badge/Framework-TensorFlow-blue?logo=tensorflow" />
  <img src="https://img.shields.io/badge/Python-3.8+-yellow?logo=python" />
  <img src="https://img.shields.io/badge/Notebook-Jupyter-green?logo=jupyter" />
  <img src="https://img.shields.io/badge/Model-LSTM-orange?logo=keras" />
</p>

---

## 🧠 Overview

This project demonstrates how to build and evaluate a **Long Short-Term Memory (LSTM)** deep learning model to forecast the closing price of **Google (GOOGL)** stock.

The notebook walks through a full, production-style time-series pipeline — including data loading, preprocessing, model training, evaluation, and visualization.

The purpose of the project is to explore the effectiveness of recurrent neural networks in financial time-series analysis and trend forecasting.

---

## 🎯 Objectives

- Load and visualize historical Google stock market data  
- Prepare time-series sequences suitable for LSTM networks  
- Build and train an LSTM model using TensorFlow/Keras  
- Evaluate predictions using **RMSE**
- Plot actual vs. predicted values  
- Discuss limitations and future improvements  

---

## 📂 Project Structure



---

## 🛠️ Technologies Used

- **Python 3.8+**
- **TensorFlow / Keras**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Scikit-learn**

---

## 📊 Model Architecture

The LSTM forecasting model uses a stacked recurrent architecture:

- Input Layer
  - The model takes sequences of past 60 days of normalized closing price data (window length), forming the input shape (sequence_length, 1).
- LSTM Layers
  - First LSTM layer
    - Units: 60
    - return_sequences=True, so that it outputs a full sequence to the next LSTM.
    - Activation: typically tanh (default) for LSTM.
    - Dropout: e.g., Dropout(0.2) to regularize and reduce overfitting.
  - Second LSTM layer
    - Units: 60
    - return_sequences=True
    - Activation: tanh
    - Dropout: 0.2
  - Third LSTM layer
    - Units: 60
    - return_sequences=False
    - Activation: tanh
    - Dropout: 0.2
- Dense Output Layer
  - After the LSTM layers, there's a fully connected (Dense) layer with 1 neuron, producing the forecast for the next day's closing price.
  - Activation: linear, as this is a regression task.
- Compilation
  - Loss Function: Mean Squared Error (MSE) — well-suited for regression and time-series prediction.
  - Optimizer: Adam — commonly used for its good convergence behavior.


- **Optimizer:** Adam  
- **Loss Function:** Mean Squared Error (MSE)  
- **Output:** Next-day closing price prediction  

### Model Summary

| Layer (type) | Output Shape   | Param # |
| ------------ | -------------- | ------- |
| LSTM         | (None, 60, 60) | 14880   |
| Dropout      | (None, 60, 60) | 0       |
| LSTM         | (None, 60, 60) | 29040   |
| Dropout      | (None, 60, 60) | 0       |
| LSTM         | (None, 60)     | 29040   |
| Dropout      | (None, 60)     | 0       |
| Dense        | (None, 1)      | 61      |

- Total params: 72,021
- Trainable params: 72,021
- Non-trainable params: 0

---

## 📉 Model Performance

The notebook computes the following metrics using **inverse-transformed predictions** (in USD):

| Metric | Value |
|--------|-------|
|**RMSE**| 10.65 |

These metrics provide insight into how closely the model tracks real stock movements.

---

## 📈 Visualizations

The notebook includes several informative visualizations:

### ✔ Actual vs. Predicted Prices  
A direct comparison of model output vs. true values.
![Actual vs Predicted Prices](images/actual_vs_predicted_prices.png)

### ✔ Training Loss Curve  
Displays convergence behavior during model training.
![Loss Over Epochs](images/loss_over_epochs.png)

---

## 🔍 Key Insights

- LSTM networks can effectively learn temporal dependencies in stock price data.  
- Predictions track major trends but are limited by market volatility.  
- Scaling data and proper sequence windowing improve model performance.  
- A single-feature (closing price only) model provides reasonable baseline accuracy.

---

## ⚠️ Limitations

- Stock prices are influenced by many external factors not included in the dataset.  
- Deep learning cannot compensate for unpredictable market events.  
- Only closing prices were used — no volume, indicators, or sentiment inputs.  
- Long-term forecasting is significantly less accurate than short-term.

---

## 🚀 Future Improvements

Planned enhancements or ideas for extension:

- Add technical indicators (RSI, MACD, Bollinger Bands)  
- Include news sentiment or macroeconomic features  
- Use other architectures (GRU, Transformer, Temporal Convolutional Networks)  
- Apply hyperparameter tuning (Optuna, KerasTuner)  
- Perform multi-step forecasting (predict multiple days ahead)  
- Implement walk-forward/rolling-window cross-validation  

---

## ▶️ How to Run

### 1️⃣ Clone the repository
```bash
git clone https://github.com/yourusername/google-stock-lstm-forecast.git
cd google-stock-lstm-forecast
```

### 2️⃣ Install dependencies
```bash
pip install -r requirements.txt
```

### 3️⃣ Launch the notebook
```bash
jupyter notebook google_stock_lstm_forecast.ipynb
```

---

## 📜 License

This project is provided under the [MIT License](LICENSE).
Feel free to use, modify, and distribute for personal or educational purposes.

---

## 🤝 Contributions

Contributions, suggestions, and improvements are always welcome!
Feel free to open an issue or submit a pull request.

---

## 👤 Author

**Arian Jr**  
📧 [Contact Me](arianjafar59@gmail.com) • 🌐 [GitHub Profile](https://github.com/ArianJr)

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/ArianJr" target="_blank">ArianJr</a>
</p>

<p align="center">
  <sub>⭐ If you found this project useful, please consider giving it a star! It helps others discover it and supports my work.</sub>
</p>
