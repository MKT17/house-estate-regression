# house-estate-regression

### Data Used
The dataset used for this analysis is the "Bengaluru_House_Data.csv," which contains the following columns:
- **area_type:** Type of area (e.g., Super built-up Area, Plot Area, Carpet Area, etc.)
- **availability:** When the property is available for sale (e.g., Ready To Move, etc.)
- **location:** Location of the property
- **size:** Number of bedrooms, halls, kitchens (e.g., 2 BHK, 4 Bedroom, etc.)
- **society:** Name of the society
- **total_sqft:** Total area in square feet
- **bath:** Number of bathrooms
- **balcony:** Number of balconies
- **price:** Price of the property in Lakhs

### Analysis Made

1. **Data Cleaning:**
   - Dropped irrelevant columns: `area_type`, `society`, `balcony`, and `availability`.
   - Removed rows with missing values.
   - Extracted the number of bedrooms from the `size` column and stored it in a new column `bhk`.

2. **Handling Outliers:**
   - Removed properties with an unusually high number of bedrooms (more than 20).
   - Converted `total_sqft` to a numeric value, handling ranges by taking their average.
   - Created a new column `price_per_sqft`.

3. **Location Normalization:**
   - Grouped locations with less than 10 properties under a single label "other."

4. **Outlier Removal in Square Feet per BHK:**
   - Removed properties where the total square feet per BHK was less than 300.

5. **Price per Square Feet Analysis:**
   - Removed outliers using the standard deviation method for each location.

6. **Bathroom Analysis:**
   - Removed properties where the number of bathrooms was greater than the number of bedrooms plus two.

7. **Feature Engineering:**
   - Created dummy variables for the location column.

8. **Model Building:**
   - Split the data into training and testing sets.
   - Built models using Linear Regression, Gradient Boosting Regressor, and Support Vector Regressor.
   - Evaluated model performance using cross-validation.

### Findings

- **Location Distribution:** Locations with less than 10 properties were grouped into the "other" category, reducing the number of unique locations from 1293 to 242.
- **Outlier Properties:** Identified and removed properties with an unusually high number of bedrooms and outlier prices per square foot.
- **Model Performance:** 
  - Linear Regression had a score of ~0.80 on the test set.
  - Gradient Boosting Regressor performed slightly better with a score of ~0.82.
  - Support Vector Regressor had a lower performance score of ~0.65.
  - Cross-validation scores for Linear Regression ranged from ~0.81 to ~0.87, indicating consistency.

### Summary

The analysis aimed to clean and preprocess the Bengaluru house data, remove outliers, and build predictive models to estimate house prices based on features such as location, square footage, number of bedrooms, and number of bathrooms. The best model, Gradient Boosting Regressor, achieved an R-squared score of ~0.82, indicating that the model explains 82% of the variance in the house prices.

### Limitations

1. **Dataset Limitations:** The dataset may not represent all the variances in the Bengaluru housing market, and important features like age of the property, proximity to amenities, etc., are missing.
2. **Model Limitations:** While Gradient Boosting Regressor performed the best, it still leaves 18% of the variance unexplained, indicating room for improvement.

