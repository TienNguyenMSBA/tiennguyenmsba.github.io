# Hotel Demand Forecasting: Traditional vs. Deep Learning Models

## 🏨 Project Overview
In the hotel industry, accurate demand forecasting is the backbone of effective Revenue Management. This project evaluates four different forecasting methodologies to determine which best predicts booking trends and optimizes pricing strategies:
- Pick-up Models (Additive and Multiplicative)
- Feedforward Neural Networks (FFNN)
- Long Short-Term Memory (LSTM)

The study utilizes historical booking data from three distinct hotels (G, M, and W) between 2008 and 2010 to analyze performance across various forecasting horizons.

## 🔬 Methodology & Models
The project compares the "Industry Standard" against "Modern AI" across different lead times (Days Before Arrival).
- Advance Booking (Pick-up) Model: A traditional heuristic used in hospitality that assumes future bookings follow historical "pick-up" patterns.
- FFNN (Feedforward Neural Network): Used to capture non-linear relationships between historical demand, temporal factors, and booking velocity.
- LSTM (Long Short-Term Memory): A Recurrent Neural Network (RNN) architecture designed to learn long-term dependencies in sequential time-series data.

## 📈 Key Findings
The models were evaluated using Mean Absolute Scaled Error (MASE) across different time horizons:

|Model| Best Performance Window |Key Strength|
|Pick-up Model| Short-term (< 30 days) | Highly accurate for immediate operational pricing. |
|FFNN| Overall Winner | Most robust; maintains accuracy where others fail (22-30 day range). |
|LSTM| Long-term (> 30 days) | Superior at capturing seasonal trends and cumulative patterns. |

- The FFNN Advantage: FFNN emerged as the most reliable model, consistently achieving the lowest error metrics. Unlike other models, it remained stable across all months and lead-time ranges, specifically outperforming others in the critical 22–30 day forecast window.

- Model Decay: The Pick-up model’s performance deteriorated over longer horizons as it struggled with seasonality and non-linear shifts.

## 💡 Business Recommendations: The Hybrid Strategy
Based on the results, I recommend a Hybrid Forecasting Framework for hotel managers to maximize profitability:
- Short-Term (0–14 Days): Utilize the Pick-up Model for rapid, operational pricing adjustments based on recent reservation activity.
- Medium-Term (15–30 Days): Transition to FFNN for high reliability and robustness during the "tipping point" of the booking curve.
- Long-Term (30+ Days): Deploy LSTM for strategic planning, leveraging its ability to understand long-term historical context and dependencies.

## 🛠️ Tech Stack
- Language: Python
- Libraries: PyTorch(Deep Learning), Pandas/NumPy (Data Processing), Matplotlib/Seaborn (Visualization)
- Metrics: MASE (Mean Absolute Scaled Error), RMSE