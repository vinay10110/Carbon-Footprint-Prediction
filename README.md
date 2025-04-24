# Carbon Footprint Prediction Project

## Project Overview
This project implements a machine learning solution to predict carbon footprints based on various lifestyle and consumption factors. The model uses LightGBM, a gradient boosting framework, to create accurate predictions of individual carbon footprints.

## Dataset Description
The dataset includes various features that influence carbon footprint:
- Electricity consumption (kWh per month)
- Natural gas consumption (therms per month)
- Vehicle miles per month
- House area (square feet)
- Water usage (liters per day)
- Diet type
- Recycling habits
- Home insulation quality
- Smart thermostat installation
- Energy-efficient appliances usage
- Household size
- Meat consumption (kg per week)
- Laundry loads per week
- Public transport usage
- Composting habits

## Data Preprocessing Steps
1. **Missing Value Treatment**
   - Filled missing values in categorical variables with mode
   - Replaced missing values in numerical variables with median
   - Cleaned negative values in consumption metrics

2. **Feature Engineering**
   - Converted categorical variables to numerical using label encoding
   - Standardized numerical features using StandardScaler
   - Handled outliers and anomalies in consumption data

3. **Data Splitting**
   - Split data into 80% training and 20% testing sets
   - Maintained random state for reproducibility

## Model Implementation
The project uses two main approaches:

### 1. PyCaret Automated ML
- Utilized PyCaret's automated machine learning capabilities
- Compared various regression models
- Identified best performing algorithms

### 2. LightGBM Model
Implemented a LightGBM regressor with the following parameters:
- Objective: Regression
- Number of estimators: 100
- Learning rate: 0.1
- Number of leaves: 31
- Random state: 42

## Model Performance
The LightGBM model achieved impressive results:
- Mean Squared Error (MSE): 3615.27
- Root Mean Squared Error (RMSE): 60.13
- Mean Absolute Error (MAE): 30.84
- R² Score: 0.9016 (90.16% variance explained)

## Key Features Importance
The model identified several key factors that significantly influence carbon footprint:
1. Vehicle miles per month
2. Electricity consumption
3. Natural gas consumption
4. House area
5. Water usage

## Files in the Project
- `CF.ipynb`: Main Jupyter notebook containing all code and analysis
- `dataset/train.csv`: Training dataset
- `dataset/test.csv`: Test dataset
- `dataset/sample_submission.csv`: Sample submission format
- `submission.csv`: Final predictions file

## Requirements
- Python 3.x
- pandas
- numpy
- scikit-learn
- LightGBM
- PyCaret
- matplotlib
- seaborn

## Usage
1. Install required packages
2. Run the Jupyter notebook `CF.ipynb`
3. Follow the cell execution order for complete analysis and prediction

## Results and Conclusions
- The model shows strong predictive performance with 90.16% accuracy (R² score)
- Transportation and energy consumption are the most significant factors in carbon footprint
- The model can effectively predict carbon footprints based on lifestyle choices and consumption patterns

## Future Improvements
1. Feature engineering for seasonal variations
2. Hyperparameter optimization
3. Ensemble modeling with other algorithms
4. Collection of additional relevant features
5. Implementation of cross-validation