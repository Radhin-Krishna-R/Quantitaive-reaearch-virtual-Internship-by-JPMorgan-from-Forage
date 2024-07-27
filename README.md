_**Introduction**_

This directory consists of 2 mini projects I did as a part of the Quantitative Research (QR) program at JPMorgan Chase from Forge, it is a virtual job simulation. I had 2 tasks which are

>  1. Prototype of a pricing model For a Natural gas company

>  2. strategically bucket customers with various FICO scores(estimate the probability of default for a borrower)

______________________________________________________________________________________________________
For detailed Report Vist my portfolio Website on this project which i uploaded as 2 parts

:  https://radhinkrishna88.wixsite.com/radhin-portfolio/post/prototype-of-pricing-model-quantitative-research

:  https://radhinkrishna88.wixsite.com/radhin-portfolio/post/credit-risk-analysis
______________________________________________________________________________________________________


>****Prototype of a pricing model For a Natural gas company****

_**1.Aim**_

This task in the project aims to develop a methodology for improved pricing of natural gas storage contracts within the commodity trading desk.  Current data from external feeds lacks sufficient granularity for accurate pricing.  This report outlines an approach to extrapolate existing data while considering seasonal trends, ultimately leading to more precise contract valuation.

_**2. Project Scope**_

The project focuses on:

1. Analyzing historical natural gas price data along with seasonal trends.
2. Developing a data extrapolation model to generate higher-resolution data points.
3. Utilizing the enhanced data to estimate future gas prices for accurate storage contract pricing.
Data Analysis

Seasonality Identification: We will employ statistical methods like time series analysis to identify seasonal patterns in historical gas prices. Techniques such as seasonal decomposition (e.g., STL decomposition) will help isolate seasonal components from the overall trend and cyclical fluctuations.
Data Cleaning and Preprocessing:  The data will be cleaned to address missing values and outliers. Techniques like imputation and winsorization might be used to address these issues.
The date format was in mm-dd-yy, which is not the standard format for input, so I converted it into the standard format by rearranging the positions and expanding the year into four digits using the datetime module. 
3.3 Data Extrapolation Model Development

Several data extrapolation models can be considered:

Data visualization: To identify Time series properties of the pricing it decomposed into individual components and created a line plot.
Statistical Methods:  Regression analysis with seasonal components can be used to model historical price trends and seasonality. This approach allows for the prediction of future prices based on historical data and identified seasonal patterns.

A primary inference indicates that seasonality, occurring consistently, contributes to the increase in natural gas prices during the winter season. Additionally, there is a trend of constant linear growth in prices over time.

_**3.Model selection**_

Thus the data shows a linear trend and a steady seasonality i suspect it will fit linear model-polynomial regression ( the internship's standard answer which uses the sine function with linear regression is also provided here but in terms of accuracy polynomial regression  is slightly better)

Model Evaluation and Selection:-
The performance of various models will be evaluated using metrics like Mean Squared Error (MSE) or Mean Absolute Error (MAE).  The model with the lowest error will be selected for further analysis.

Contract Pricing:-
The chosen data extrapolation model will estimate future gas prices at any given date.  This information and the terms of the storage contract (storage fees, injection/withdrawal dates) will be used to price the contract accurately.

_**Project Deliverables**_

A well-documented data extrapolation model for natural gas prices.
A prototype system or script that can be used to price storage contracts based on the model's output.
A comprehensive report outlining the methodology, model development, and results.
The retailer can input the date he wants to predict the price and get the result closer to it

_**Conclusion**_

By enhancing the available data through extrapolation and incorporating seasonality, we can achieve more accurate pricing of natural gas storage contracts.  This will provide the trading desk with a valuable tool for informed decision-making when entering into storage contracts.

_______________________________________________________________________________________________________________

>strategically bucket customers with various FICO scores(estimate the probability of default for a borrower)

_**Introduction**_

Retail banks face significant risk when issuing loans due to the possibility of borrowers defaulting on their payments.  This project aims to develop a model using a Random Forest algorithm to predict loan default probabilities (PD).  Predicting PD allows banks to estimate potential losses and set aside appropriate reserves, ensuring financial stability.

**Feature Engineering**

While the provided features offer valuable insights, we may consider creating additional features to enhance the model's predictive power:

Debt-to-Income Ratio: This ratio (total debt / income) can provide a clearer picture of the borrower's financial burden.
Credit Utilization Ratio: This ratio (loan amount / credit line) indicates how much of the available credit the borrower is using.

_**Random Forest Model**_

A Random Forest algorithm will be employed for its effectiveness in credit risk analysis. This ensemble method combines multiple decision trees, improving accuracy and reducing overfitting.

The model will be trained on the prepared data, including both original and potentially derived features.
Hyperparameter tuning will be performed to optimize the model's performance. This involves adjusting parameters like the number of trees in the forest and the maximum depth of each tree.


_**Model Evaluation**_
AUC-ROC (Area Under the Receiver Operating Characteristic Curve): This metric assesses the model's ability to differentiate between defaulters and non-defaulters. A higher AUC-ROC indicates better performance.
Confusion Matrix: A table that visually summarizes how many predictions were correct (TP, TN) and incorrect (FP, FN) for each class (defaulter, non-defaulter).
Classification Report: Provides detailed metrics (precision, recall, F1-score) to evaluate how well the model identifies defaulters and non-defaulters.

Expected Loss Calculation

An expected loss function will be created to estimate potential losses associated with each loan. This function will consider:

Predicted Probability of Default (PD): Obtained from the trained Random Forest model for a particular loan applicant.
Recovery Rate: This represents the percentage of the loan amount that can be recovered in case of default. A typical value might be 10%.
Loan Amount: The total amount of the loan being considered.
The expected loss is calculated by multiplying the predicted PD by the potential loss amount (loan amount multiplied by (1 - recovery rate)).

Quantization for FICO Scores(sub part 2)

Introduction:

aims to develop a Random Forest model for predicting loan default probabilities (PD) in the retail banking arm. However,  a member of the risk team wants to ensure the model's effectiveness for future data sets with potentially different FICO score distributions.

Objective:  Develop a general approach to categorize FICO scores into a predefined number of buckets (corresponding to input labels for the model) while preserving the most relevant credit risk information.

Challenges:

Mapping FICO Scores to Ratings: We need to create a "rating map" that translates FICO scores into a rating system, with lower ratings indicating higher credit risk (better scores).
Solution Approaches:

Mean Squared Error (MSE) Quantization:
View this as an approximation problem.
Aim to minimize the squared error between the actual FICO score and a single representative value assigned to each bucket.
Log-likelihood Quantization:
This is a more sophisticated approach that maximizes a log-likelihood function.
This function considers the impact of quantization on:
Discretization "roughness" (how well the buckets capture the data distribution)
Default density within each bucket (concentration of high-risk borrowers)
Implementation Strategies:

The log-likelihood approach can be tackled by dividing it into subproblems:
Example: Create five buckets for FICO scores (0-600) and five buckets (600-850).
This allows for an incremental (step-by-step) solution using dynamic programming techniques.

Research and implement specific algorithms for both MSE and log-likelihood quantization approaches.
Evaluate the impact of quantization on the model's performance using metrics like AUC-ROC.
Choose the quantization method that offers the best balance between accuracy and generalizability.

_**Conclusion:**_

By incorporating FICO score quantization, this project aims to enhance the Random Forest model's generalizability and effectiveness in predicting loan defaults for future loan applications
