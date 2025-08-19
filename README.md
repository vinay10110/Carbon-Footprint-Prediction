# Carbon Footprint Prediction

Predict a household's carbon footprint from lifestyle and home attributes. This project builds a regression model using PyCaret and visualizes performance and insights.

## Project Overview
- __Goal__: Estimate `carbon_footprint` from features like electricity usage, gas usage, vehicle miles, house size, water usage, insulation quality, recycling habits, diet type, etc.
- __Data__: CSV files in `dataset/`
  - `train.csv` — training data with target `carbon_footprint`
  - `test.csv` — test data without target
  - `sample_submission.csv` — format for submission
- __Notebook__: Main workflow in `CF.ipynb`
- __Best Model (from compare_models)__: LightGBM (R² ≈ 0.877, MAE ≈ 32.77, RMSE ≈ 66.23)

## Repository Structure
- `dataset/` — input CSVs
- `results/model/CF.pkl` — trained model artifact (example)
- `results/plots/` — saved figures (see below)
- `results/submission.csv` — prediction file
- `CF.ipynb` — data prep, modeling, prediction
- `requirements.txt` — project dependencies

## Quickstart
1. __Install dependencies__ (recommend a fresh virtual environment):
   - Python 3.11+
   - `pip install -r requirements.txt`
2. __Open the notebook__: `CF.ipynb`
3. __Run all cells__ to:
   - Load and preprocess data (missing values, encoding, cleaning, scaling)
   - Train and compare models with PyCaret (`compare_models()`)
   - Finalize best model and predict on test set
   - Save submission to `results/submission.csv`

## Key Results & Visualizations
Below are core plots stored in `results/plots/`.

### Feature Importance
![Feature Importance](results/plots/Feature_imp.png)

### Residuals Analysis
![Residuals](results/plots/Residuals.png)

### Learning Curve
![Learning Curve](results/plots/learning_curve.png)

> Tip: You can generate additional evaluation plots (Predictions vs Actual, Residuals distribution, metric summaries) directly in the notebook using the provided evaluation cells.

## Reproducing the Pipeline
- Preprocessing:
  - Fill categorical/binary NA with mode (e.g., `recycles_regularly`, `composts_organic_waste`, `smart_thermostat_installed`, `energy_efficient_appliances`).
  - Encode `diet_type` and `heating_type` (map other/none to `unknown`).
  - Clean `house_area_sqft` to numeric; impute with train mean.
  - Validate numeric ranges; set negatives to NA and impute with train median.
  - Scale selected continuous variables with `StandardScaler`.
- Modeling:
  - PyCaret regression `setup(..., target='carbon_footprint', session_id=42, normalize=True)`
  - `best_model = compare_models()`
  - `final_model = finalize_model(best_model)` and `predict_model` for inference.

## Requirements
- pandas, numpy, scikit-learn, matplotlib, seaborn, pycaret

## Notes
- Metrics may vary slightly per run due to randomness (fixed `session_id=42` helps reproducibility).
- Ensure plots exist in `results/plots/`. If not, run the evaluation cells in the notebook to regenerate.

## License
This project is provided as-is for educational and benchmarking purposes.
