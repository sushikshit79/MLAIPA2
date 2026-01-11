# What drives the price of a car?

## OVERVIEW
As your consultant, I will initiate this project by adhering strictly to the CRoss-Industry Standard Process for Data Mining framework, beginning with a thorough understanding of your business.

My primary objective is to translate your business need, identifying the key factors influencing used car prices constructing a highly accurate Prediction model. This model will be developed using the provided 426K car dataset.

###  Business Understanding

The objective of this exercise is to provide an accurate and explanable car price prediction model by identifying key factors that influence vehicle pricing by leverage  provided vehicle dataset of 426,000 records. The project will follow the CRISP-DM framework to ensure alignment with business objectives and requirements. The solution will enusre there is right analytical rigor ensuring the model is well trained and quality tested for repeatable outcomes to support pricing decisions based oninsights and data-driven strategy.

### Data Understanding and Observations

* The used car dataset contains 426,880 records and 18 columns, representing a large and diverse vehicle inventory.
* The id column appears to be a database primary key and does not provide analytical value.
* The VIN column is unique to each vehicle and carries no semantic meaning for price prediction.
* Key attributes expected to strongly influence vehicle price include model, year, and odometer.
* Additional features such as vehicle size, condition, fuel type, cylinders, and transmission are also likely to impact pricing.
* Several columns contain substantial missing values, with drive, size, condition, and cylinders missing in over 30% of records, requiring careful handling.
* The dataset contains significant outliers in both price and odometer values that could skew model results if left untreated.
* Price distribution is heavily right-skewed, with most vehicles priced in the thousands or tens of thousands, while a small number of extreme values inflate the upper range.
* Odometer values show a long-tailed distribution, with a few unrealistically high readings stretching the scale beyond typical vehicle usage.
* A systematic approach to handling missing data, feature level and outlier treatment is essential for building a reliable pricing model.

#### Visualization for understanding data
![Cars Sold per Manufacturer](https://github.com/sushikshit79/MLAIPA2/blob/main/images/cars_sold_per_manufacturer.png)
![Odometer Distribution](https://github.com/sushikshit79/MLAIPA2/blob/main/images/odometer_distribution.png)
![Price Distribution](https://github.com/sushikshit79/MLAIPA2/blob/main/images/price_distribution.png)

### Data Preparation

#### Below are steps undertaken for prepartion of the data

* Initial modeling using the full dataset resulted in poor predictive performance across all models, indicating data quality issues.
* Filtering the dataset and removing records with excessive missing values significantly improved prediction accuracy.
* Retaining high-missing columns with indicator flags did not materially improve model performance.Below are model eval metrcics for full data and test data
   * ![**Model Metrcis for Linear, Ridge and Lasso Regression model for full dataset**](https://github.com/sushikshit79/MLAIPA2/blob/main/files/model_eval_metrcis_full_data.csv)
   * ![**Test dataset model metrcis for Linear, Ridge and Lasso Regression model for full dataset**](https://github.com/sushikshit79/MLAIPA2/blob/main/files/test_eval_metrics_full_data.csv)
* Records containing missing values in critical fields were removed, resulting in approximately 73% of the original data being excluded to ensure data integrity.
* Outlier treatment was applied to the price and odometer columns using lower and upper quartile thresholds to reduce noise and extreme value influence.
* Logarithmic transformations were applied to the price and odometer columns to address skewness and stabilize variance.
* Numerical features were scaled to ensure comparability across features and numerical stability during model training.
* Categorical features were encoded to preserve category-level information for modeling.
* As an alternative modeling approach, categorical features were also manually converted to numeric identifiers to evaluate performance differences.

### Modeling
The three regression techniques that are evaluated are
* Linear Regression
* Ridge Regression
* Lasso Regression

Two feature representation are tested
* Encoded categorical features
* Numeric identifiers with ploynomial expansion

#### Model metrics
Below are model metrcis with validation dataset for different approaches

![**Model Metrcis for Linear, Ridge and Lasso Regression model for treated dataset**](https://github.com/sushikshit79/MLAIPA2/blob/main/files/model_eval_metrcis_encoded.csv))

![**Model Metrcis for Linear, Ridge and Lasso Regression model for numeric identifiers with ploynomial expansion**](https://github.com/sushikshit79/MLAIPA2/blob/main/files/model_eval_metrcis_numeric_conv.csv)

### Model Evaluation

* Initial evaluation using the full dataset resulted in poor price prediction performance across all three models (Linear, Ridge, and Lasso), indicating data quality issues, particularly replacing missing values with unknown and adding columns gave higher prediction error
* Filtering the dataset and removing records with excessive missing values significantly improved model performance, highlighting the importance of data preprocessing over model complexity.
* When using the full dataset, alternative filtering strategies such as retaining high-missing columns with indicator flags did not materially improve performance, reinforcing the decision to remove incomplete records.
* Model evaluation was conducted using Linear, Ridge, and Lasso regression with encoded categorical features, as well as with numerical identifiers derived from categorical variables.
* In the numeric approach, polynomial feature expansion with degrees 2, 3, and 5 were tested. Increasing polynomial degree did not meaningfully affect MAE, RMSE, or R², indicating limited nonlinear signal in the numeric feature space. As a result, polynomial degree 2 was selected for consistency.
* Models were evaluated using:
    * Mean Absolute Error (MAE)
    * Root Mean Squared Error (RMSE)
    * R2 Score
* Feature Importance Analysis
    * Both encoded and numeric approaches identified **region** and **state** as the most influential features.
    * Secondary features included model, type, condition, and transmission.
    * Feature importance rankings were stable across modeling techniques.
* While MAE and RMSE were comparable between encoded and numeric approaches, encoded models achieved substantially higher R**2, indicating superior ability to explain variance in vehicle prices.
* Given the minimal difference in absolute error metrics and the meaningful difference in explanatory power, the encoded feature approach is selected, as it preserves categorical nuance and captures regional market variation that numeric conversion may suppress.
* Within the encoded models, Ridge regression was selected over Linear and Lasso. Though Linear and Ridge showed similar performance, Ridge offers greater robustness and improved stability under potential future data shifts. Lasso underperformed in terms of R**2, indicating excessive regularization and reduced ability to capture variance.
* Validation and test metrics were closely aligned, indicating good generalization and no evidence of overfitting.
* Finally, despite extensive feature engineering and polynomial expansion, overall R2 values remained modest, indicating that model performance is primarily constrained by the available data rather than model selection.
  
**Based on these observations, Ridge regression with encoded categorical features is selected as the final model.**

#### Below are model metrcis with validation dataset for different approaches

![**Test dataset model metrcis for Linear, Ridge and Lasso Regression model for treated dataset**](https://github.com/sushikshit79/MLAIPA2/blob/main/files/test_eval_metrics_encoded.csv)

![**MTest dataset model metrcis for Linear, Ridge and Lasso Regression model for numeric identifiers with ploynomial expansion**](https://github.com/sushikshit79/MLAIPA2/blob/main/files/test_eval_metrics_numeric_conv.csv)

#### Below are permutation importance for Linear, Ridge and Lasso Regression model

![**Permutation importance for Linear, Ridge and Lasso Regression model for treated dataset**](https://github.com/sushikshit79/MLAIPA2/blob/main/files/perm_importance_encoded.csv)

![**Permutation importance for Linear, Ridge and Lasso Regression model numeric identifiers with ploynomial expansion**](https://github.com/sushikshit79/MLAIPA2/blob/main/files/perm_importance_num_identifier.csv)

## Used Car Pricing Analysis – Dealer Report

## Summary of Findings

This analysis was conducted to identify the key drivers of used car prices and to recommend a  pricing model that can help dealers fine tune inventory and regional pricing strategies. After evaluating multiple modeling approaches and feature representations, it was found that **geographic location is the strongest driver of price**, followed by vehicle configuration and condition. Among the models tested, 

**Ridge Regression using encoded categorical features** provides the best balance of accuracy, stability, and interpretability and is recommended for practical use.

## Key Findings for Dealers

1. Location Drives Price More Than Any Other Factor
All models and evaluation methods consistently show cased that region and state are the top drivers of price. Vehicle with same specification can command significantly different prices depdending on where there are sold.
**Dealer Take Away: Pricing Startegy should region and state sepecific and not unfiorm.**

2. Vehicle Atrributes
After location, the next most importan attributes of a vehicle are
    * Model
    * Vehicle Type(SUV, Sedan, Truck etc)
    * Condition
    * Transmission
Mileage and paint_color have a smaller impact over pricing once above factors are accounted for.
**Dealer Take Away: Inventory decisions should priortise condition and configuration.**

3. Data Quality Significantly impacted Pricing Accuracy
Models trained on fill dataset performed poorly due to missing and incosistent data. Removing incomplete records helped in prediction accuracy.**Dealer Take Away: Maintaining clean and  structured data leads to better pricing recommendation decisions.**

4. Business Implication based on the given data
    * Regional inventory can be optimized based on location based sales
    * Over investment in cosmetics of a vehicles may not lead to additional sales with limited rate of return on investment.
    * Future improvements may come additional inputs like seasonality rather than employing complex models

## Recommendation 
To support accurate and consistent pricing decisions, adopt a Ridge regression model with encoded categorical features. This approach captures nuances/real-world behavior of vehicle pricing attributes while remaining interpretable and robust for dealer operations.





