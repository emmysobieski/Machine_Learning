# Machine_Learning

I ran the following models to see which one is best at predicting credit risk.

First, I looked at the objective and dataset. In the dataset, there are 347 total high risk credits and 68,470 low risk credits, so the percentage of high risk credits is very low at 5/1,000th or half of one percent.

Numerical Comparison of select values

Naive Oversampling: 63.8% BAS

Bad Credit:  Precision 0.01  Recall 0.68  F1 0.02 
Good Credit: Precision 1.00  Recall 0.64  F1 0.78 

SMOTE Oversampling: 69.5% BAS

Bad Credit:  Precision 0.01  Recall 0.61  F1 0.02 
Good Credit: Precision 1.00  Recall 0.70  F1 0.82 

Cluster Undersampling: 41.3% BAS

Bad Credit:  Precision 0.01  Recall 0.68  F1 0.01 
Good Credit: Precision 1.00  Recall 0.41  F1 0.58 

SMOTEENN Combination: 59.8% BAS

Bad Credit:  Precision 0.01  Recall 0.65  F1 0.02 
Good Credit: Precision 1.00  Recall 0.60  F1 0.75 

Goal 1: Write loans by finding low credit risk clients

If the goal in predicting credit risk is to accept as may loans as possible, without taking on undue risk, then you can look to focus on how the model performs in predicting good credits. Given that using NO prediction model at all, will statistically lead to only half a percent of bad loans, this means the RISK of experiencing a bad loan is low, so you can optimize the model choice for selecting the model that chooses good loans the best. In this case, the SMOTE model has the best F1 score of 82, showing a nice balance between recall scores of good and bad credits. This model also has the highest Balanced Accuracy Score of 69.5%.

For all models the precision score is meaningless, showing that due to the low number of bad credits, the model will look incredibly precise for predicting good credits just because the natural likelihood of good credits in the data is 99.5% of the data. That leads me to Goal 2, using sensitivity to predict and avoid bad credits, if that is the client focus more than accepting good credits.

Goal 2: Avoid Risk of writing bad loans by finding and avoiding high credit risk clients

IF the goal in predicting credit risk using high sensitivity (casting a wide net to most accurately predict bad credits, then the Naive Oversampling has the highest recall at 0.68 for high risk credits, vs 0.61 in the SMOTE model, and the F1 score only comes down to 0.78. Therefore if in predicting credit risk the client is more interested in avoiding any risky clients, the Naive Oversampling model performs slightly better.

Conclusion:

No model is perfect. If the client is a financial institution, they are likely driven by revenue and most likely interested in approving as many loans as possible without taking on undue credit risk. Under the conditions of wanting to approve the most good loans by predicting the highest number of good credits, with the highest accuracy and balance between recall of good and bad credits, the SMOTE model is the one of these four I recommend. If the goal of the institution is absolute risk avoidance, as reflected by wanting to have the highest recall aka sensitivity to predicting bad credits then the Naive Oversampling model performs the best, with small tradeoffs of slightly lower F1 (balance) and slightly lower overall accuracy.
