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
* Retaining high-missing columns with indicator flags did not materially improve model performance.
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

**Model Metrcis for Linear, Ridge and Lasso Regression model for full dataset**
(https://github.com/sushikshit79/MLAIPA2/blob/main/files/model_eval_metrcis_full_data.csv)

[**Model Metrcis for Linear, Ridge and Lasso Regression model for treated dataset**](https://github.com/sushikshit79/MLAIPA2/blob/main/files/model_eval_metrcis_nulls_removed.csv)


