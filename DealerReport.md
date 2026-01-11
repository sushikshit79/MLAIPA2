# Used Car Pricing Analysis – Dealer Report

## Summary of Findings

This analysis was conducted to identify the key drivers of used car prices and to recommend a  pricing model that can help dealers fine tune inventory and regional pricing strategies. After evaluating multiple modeling approaches and feature representations, it was found that **geographic location is the strongest driver of price**, followed by vehicle configuration and condition. Among the models tested, **Ridge Regression using encoded categorical features** provides the best balance of accuracy, stability, and interpretability and is recommended for practical use.

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
   
