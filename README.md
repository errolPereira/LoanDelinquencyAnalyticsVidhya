### Because of Gods grace and help I was able to score a Rank of  in the Public Leaderboard. All thanks to the God Almighty and Jesus Christ for the help and knowledge he provided me.

# LoanDelinquencyAnalyticsVidhya
India ML Hiring Hackathon 2019
This year, India will be celebrating its 73rd Independence Day !  For us proud Indians, this a day to celebrate our past, enjoy the present and be optimistic about our country's bright future.
 
What else could be the best way to do this but to help build career of future data scientists of India ! and that is exactly what we will be doing this Independence Day.
 
On this year's Independence, Analytics Vidhya is proud to present the "India Machine Learning Hiring Hackathon- 2019" - India's Largest Hiring Hackathon where every data science aspirant and professional will get an opportunity to showcase their talent and get the chance to interview with top organizations for job roles in Data Science, Machine Learning & Analytics. Be it Bengaluru, Delhi NCR, Mumbai, Pune, Chennai or Hyderabad; here is a chance to perform and get placed with a top company at your preferred location.
 
Data Science is already helping solve various kinds of problems in India and power projects like - Smart India, power the agriculture industry, define and deploy policies to uplift the social strength, improve the healthcare, electricity & water services and much more.  Get ready to solve an exciting data science challenge this Independence week and become a part of India's Next-gen Data Science Ecosystem- Jai Hind !
 
It's time to democratise data science and give more and more career opportunities to the data science community of India.

# Problem Statement
## Loan Delinquency Prediction
Loan default prediction is one of the most critical and crucial problem faced by financial institutions and organizations as it has a noteworthy effect on the profitability of these institutions. In recent years, there is a tremendous increase in the volume of non – performing loans which results in a jeopardizing effect on the growth of these institutions.
 
Therefore, to maintain a healthy portfolio, the banks put stringent monitoring and evaluation measures in place to ensure timely repayment of loans by borrowers. Despite these measures, a major proportion of loans become delinquent. Delinquency occurs when a borrower misses a payment against his/her loan.

Given the information like mortgage details, borrowers related details and payment details, our objective is to identify the delinquency status of loans for the next month given the delinquency status for the previous 12 months (in number of months)



## Models Tried:
1. Logistic Regression
2. Decision Tree
3. Random Forest
4. GradientBoosting Classifier
5. Light Gradient Boosting
6. XGBoost
7. AdaBoost
8. SVC
9. Catboost

## Features Created
1. EMI - with the formula   (P * R * (1 + R)^N) / (((1 + R)^N) - 1)
2. Total payabale amount : EMI * loan_term
3. monthly salary : EMI / debt_to_income * 100
4. downpayment>20 : if insurance taken then 0 else 1
5. Balance : monthly salary - EMI
6. Home Value : unpaid_principal_bal / (loan to value / 100) 
7. downpayment_amount : home value - unnpaid principal balance
8. M : adding all the m's (m0 - m12)

## Thing tried:
1. Created the above new features.
2. dropped financial institution as it was adding noise in the data.
3. Created Categorical features out of the origination and first_payment date. They were not proving any information when extracted their date features and hence used them as categorical variable which provided good information.
4. One hot encoded categorical features and also feature having values 0 and 1 i.e insuance_tye.
5. Used smote to increase the samples of the minority class. Only increased small amount of the minority class using ratio= 0.059 i.e 5.9% (greatly increased the F1 score)
7. Tried different models such as XGBoost, GBM, lgbm, AdaBoost, Catboost, RF, DecisionTree. Out of these AdaBoost gave me the highest F1 score.
8. Tuned the hyperparameters of the models which also helped in improving the score.

## Things did not work.
1. I tried Scaling the features which reduced my F1 score. As I was using only tree based models which does not assume the form of the data and are not affected by the variance in the data, Scaling did not matter much, so left the data unscaled.
2. The many features created were only adding noise in the data and was not helping in the splitting of the data into hetrogenous groups. So dropped the newly created features, only kept M and the categorical features created.
3. Linear model susch as logistic did not work at all and also SVC did not improved the score.
4. Tried doing PCA with n_components = 1 and 2 and added those components as a feature in the dataset but did not help.
5. Deleting the m0-m12 features reduced the F1 scores.
6. Using financial_institution as a feature added noise in the data and reduced the model accuracy.
7. Mean encoding the categorical features did not help in splitting the  data.

## Things that worked.
1. Not scaling the features and using them as they were.
2. Converting date features to categorical features.
3. Using OHE instead of mean/target encoding.
4. Keeping and creating categorical features.
5. Smote with the ratio of 0.059. Applying smote with default parameters did not work. Used these parameters instead:
ratio = 0.059, k_neighbors=10, random_state=10
6. Algorithms such as GBM, XGBoost, AdaBoost and LGBM worked much better than the others.
7. Kept the max_depth as 2 for all the models which imporved the F1 score greatly.
