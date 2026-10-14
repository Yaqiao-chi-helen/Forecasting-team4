# Forecasting Model Development: AI-Powered Energy Prediction
 
A prototype platform that forecasts next-hour electricity demand using machine learning and deep learning, with explainability analysis (SHAP and LIME) to show what drives each forecast.
 
Developed by **Forecasting Team 4** for the unit ICT30016 ICT Innovation Project (Swinburne University of Technology, 2026), for the **ARC Research Hub for Integrated Energy Storage Solutions**.
 
> This is a research prototype built with free, open-source tools. It is not a production forecasting system.
 
## Project overview
 
Accurate load forecasting is essential for grid stability, cost control and the integration of renewable energy. Traditional approaches often rely on a single model and offer limited explainability. This project:
 
- builds a baseline model (XGBoost) and a sequence model (LSTM) for hourly load forecasting;
- combines them into a weighted hybrid model;
- compares models using MAE, RMSE and MAPE;
- applies SHAP and LIME to explain which inputs drive the forecasts.
## Results
 
Trained and tested on PJM East hourly demand (2002–2018). The test set covers April 2015 to August 2018 and was never seen during training.
 
| Model | MAE (MW) |
| --- | --- |
| XGBoost (baseline) | 335.78 |
| LSTM | 237.83 |
| **Hybrid (LSTM + XGBoost)** | **228.96** |
 
The hybrid model's MAPE is **0.728%**, reducing the baseline error by almost one third. Full metrics, plots and the explainability analysis are in the main notebook.
 
## Repository structure
 
```
notebooks/
  Model_XGBoost_LSTM_latest_one.ipynb   <- MAIN NOTEBOOK (final version)
  models/                               <- saved LSTM model and results table
PJM Hourly Energy Concumption/
  data/raw/                             <- original PJME data from Kaggle
  data/processed/                       <- cleaned dataset used by the notebook
  Notebooks/data_cleaning.ipynb         <- data cleaning steps
Datasets/                               <- dataset research notes
Worklogs/                               <- weekly team work logs
requirements.txt                        <- pinned library versions
LICENSE                                 <- MIT Licence
```
 
Other notebooks in `notebooks/` are earlier development versions kept for reference.
 
## How to run
 
1. Open `notebooks/Model_XGBoost_LSTM_latest_one.ipynb` in Google Colab.
2. Select **Runtime → Change runtime type → T4 GPU** (LSTM training takes about 6 minutes on a T4 GPU).
3. Select **Runtime → Run all**.
The notebook loads the cleaned dataset directly from this repository, so no file upload or Google Drive access is needed. Random seeds and deterministic operations are fixed, so repeated runs reproduce the same results.
 
To run locally instead, install the pinned versions with `pip install -r requirements.txt`.
 
## Dependencies and licences
 
The prototype uses the following open-source Python libraries (versions from `requirements.txt`):
 
| Library | Version | Licence | Used for |
| --- | --- | --- | --- |
| [pandas](https://github.com/pandas-dev/pandas/blob/main/LICENSE) | 2.2.3 | BSD 3-Clause | Loading, cleaning and organising time-series data |
| [NumPy](https://github.com/numpy/numpy/blob/main/LICENSE.txt) | 2.1.3 | BSD 3-Clause | Numerical calculations and array operations |
| [scikit-learn](https://github.com/scikit-learn/scikit-learn/blob/main/COPYING) | 1.6.1 | BSD 3-Clause | Preprocessing and evaluation metrics |
| [TensorFlow / Keras](https://github.com/tensorflow/tensorflow/blob/master/LICENSE) | 2.21.0 | Apache 2.0 | Building and training the LSTM model |
| [XGBoost](https://github.com/dmlc/xgboost/blob/master/LICENSE) | 3.4.1 | Apache 2.0 | Gradient-boosted tree baseline model |
| [SHAP](https://github.com/shap/shap/blob/main/LICENSE) | 0.52.0 | MIT | Explaining predictions through feature attribution |
| [LIME](https://github.com/marcotcr/lime/blob/master/LICENSE) | 0.2.0.1 | BSD 2-Clause | Local explanations of individual predictions |
| [Matplotlib](https://matplotlib.org/stable/project/license.html) | 3.10.0 | Matplotlib licence (PSF-based) | Plotting trends, forecasts and results |
 
All libraries are used without modifying their source code, and none of their code is redistributed in this repository. Anyone who redistributes these libraries must follow their copyright, licence and notice requirements.
 
### Dataset
 
[PJM Hourly Energy Consumption](https://www.kaggle.com/datasets/robikscube/hourly-energy-consumption) (Kaggle) is released under **CC0 1.0 Universal** (public-domain dedication). It may be reused without attribution requirements; we credit Kaggle and PJM Interconnection as the source for transparency.
 
## Licence
 
This project is released under the [MIT Licence](LICENSE). You may use, copy, modify and distribute the code, provided the copyright and licence notice are kept. We chose MIT because all dependencies use compatible permissive licences and the dataset is CC0, and because it lets researchers and industry partners reuse the work with minimal restrictions.
 
## Team
 
Yaqiao Chi · Bhumika Sharma · Vidhi Patel · Marwa Aldhafeeri  
