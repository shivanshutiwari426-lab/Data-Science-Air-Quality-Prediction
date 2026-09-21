# House Price Prediction

An end-to-end Machine Learning project that predicts residential house prices from structural and
locational features (area, bedrooms, bathrooms, location, age, amenities, etc.) using multiple
regression algorithms, with model comparison, hyperparameter tuning, and feature-importance analysis.

## Project Description

Real estate prices depend on many interacting factors — size, location, age, and amenities — making
manual price estimation unreliable. This project builds a data-driven regression pipeline that:

- Performs exploratory data analysis (EDA) to understand price drivers
- Cleans and preprocesses the data (missing values, encoding, outlier handling)
- Trains and compares six regression models: Linear Regression, Ridge, Lasso, Decision Tree,
  Random Forest, and Gradient Boosting
- Tunes the best-performing model with `GridSearchCV`
- Analyzes feature importance to explain what drives house prices
- Saves the final trained model for reuse

## Dataset

This project uses a **synthetically generated housing dataset** (`house_price_data.csv`), created
programmatically inside the notebook (Section 2) with a fixed random seed so results are fully
reproducible without any external download. It contains 2,000 records with 13 features (area,
bedrooms, bathrooms, stories, age, garage, distance to city, school rating, crime index, pool,
basement, furnishing status, location type) and the target column `Price`.

The dataset is built to statistically resemble real-world housing datasets. To run this project on
real data instead, you can substitute:

- [Kaggle House Prices – Advanced Regression Techniques (Ames Housing)](https://www.kaggle.com/c/house-prices-advanced-regression-techniques)
- [California Housing Prices dataset (Kaggle)](https://www.kaggle.com/datasets/camnugent/california-housing-prices)

To switch datasets, replace the data-generation cell in Section 2 of the notebook with
`df = pd.read_csv("your_dataset.csv")` and adjust column names referenced in later sections
accordingly.

## Technologies Used

- **Python 3.11**
- **pandas / numpy** — data manipulation
- **matplotlib / seaborn** — visualization
- **scikit-learn** — preprocessing, modeling, evaluation, hyperparameter tuning
- **joblib** — model persistence
- **Jupyter Notebook** — development environment

## Project Structure

```
├── YourName_HousePricePrediction.ipynb   # Main notebook (EDA, modeling, evaluation)
├── requirements.txt                       # Python dependencies
├── YourName_ProjectReport.docx            # Full project report
├── README.md                              # This file
├── house_price_data.csv                   # Generated dataset (created on first run)
├── house_price_model.pkl                  # Saved final model (created on run)
├── feature_scaler.pkl                     # Saved StandardScaler (created on run)
└── model_features.pkl                     # Saved list of model input columns (created on run)
```

## Setup & Run Instructions

1. **Clone / download** this project folder.

2. **Create a virtual environment** (recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate        # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Launch Jupyter Notebook:**
   ```bash
   jupyter notebook
   ```

5. **Open** `YourName_HousePricePrediction.ipynb` and run all cells from top to bottom
   (`Kernel → Restart & Run All`). The notebook is self-contained — it generates its own dataset,
   so no manual data download is required.

6. The trained model will be saved as `house_price_model.pkl` in the project folder, ready to be
   reloaded with `joblib.load("house_price_model.pkl")` for future predictions.

## Key Results

- Ensemble tree-based models (Random Forest, Gradient Boosting) outperformed linear models,
  reflecting non-linear relationships in housing prices.
- The **tuned Random Forest Regressor** was selected as the final model after `GridSearchCV`
  hyperparameter tuning.
- The most influential features were **Area (sqft)**, **Distance to City Center**, **Location Type**,
  and **School Rating**.
- Full metrics (MAE, RMSE, R²) and comparison charts for every model are available in the notebook.

## Author

Your Name

## License

This project is provided for educational purposes.
