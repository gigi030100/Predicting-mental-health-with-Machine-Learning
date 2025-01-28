# Predicting-mental-health-with-Machine-Learning
My project aims to utilise machine learning techniques to identify early adolescents at high-risk of mental disorders during late adolescence. It will specifically focus on how well the combined effects of different facets of familial characteristics at the age of 14 can identify high risk cohort members at the age of 17.


![Screenshot 2025-01-28 at 11 41 15](https://github.com/user-attachments/assets/9da55b92-5ef3-458c-a87a-347a9f455515)

# Methodology
<img width="460" alt="Screenshot 2025-01-28 at 12 05 56" src="https://github.com/user-attachments/assets/e01b961f-6c2f-4b9f-a539-729b18e19b58" />

Image above shows a flowchart for building machine learning model. 

## Dataset
The Millenium Cohort Study was used (URL: https://beta.ukdataservice.ac.uk/datacatalogue/series/series?id=2000031) which contains longitudinal data from age 14 to 17.

### Predictor variables at the age of 14
#### 1. Parent-reported Kessler Psychological Distress Scale.
This 6-item measure aims to capture non-specific psychological distress as a form of indication for mental illness among the general population using a scale of 1-5 to measure parental mental illness.
#### 2. Parental education
This is obtained by looking at the highest national vocational qualification gained across all sweeps.
#### 3. Parent-reported Alcohol use disorder idenfiication test.
This 5-item measure acts as a screening tool for identifying those with alcohol use disorders.
#### 4. Parent-child relationship
This was captured based on cohort members and parent's rating of closeness and frequency of arguments with each other.
#### 5. Household income.
Household income was divided into 5 categories: (1) bottom quintile: (2) second quintile: (3) third quintile: (4) fourth quintile: (5) top quintile, with each quintile representing 20% of the population. I.e., bottom quintile contains 20% households with the lowest income.

### Target variable at the age of 17
#### Strengths and Difficulties Questionnaire. 
An emotional and behavioural screening tool aimed to evaluate 17 year-old's mental health. Scores were rated by parents using a 3-point likert scale. The scale was designed to measure 5 subscales (emotional symptoms, conduct problems, hyperactivity/Inattention, peer relationship problems, and prosocial behaviour). Mental health was operationalised by summing up the scores from all subscales, except prosocial behaviour, to derive the total difficulties score. This score was then transformed into binary classes (high-risk vs low risk) using a threshold score of 17 which indicates abnormality (Goodman, 1997).

## Data pre-processing and Exploratory data analysis
After downloading and merging the dataset, the data types of each column was corrected to ensure the dataset is properly pre-processed. Data imputation was also used to combat missing values to preserve the number of cohort members analysed. However, as our dataset possesses a mixture of data types, multiple imputation and mode imputation was used to replace missing float/integer and categorical data types respectively. 11,261 duplicated rows were also removed to reduce data redundancy, leaving us with 28,912 total sample. Exploratory data analysis was also implemented to extract data patterns and obtain insight.

<img width="472" alt="Screenshot 2025-01-28 at 12 12 29" src="https://github.com/user-attachments/assets/15d40a54-c802-45e4-a457-28a3fd14f99d" />

<img width="673" alt="Screenshot 2025-01-28 at 12 13 07" src="https://github.com/user-attachments/assets/9f8b078a-8f5d-4f00-a603-9bec1709dc3a" />

<img width="500" alt="Screenshot 2025-01-28 at 12 14 51" src="https://github.com/user-attachments/assets/da622b88-b3d6-4c62-b334-0736ebdc553d" />

As you can see above an unbalanced proportion of high and low risk of mental health issues, Synthetic Minority Over-sampling Technique for Nominal and Continuous features (SMOTE-NC) was incorporated which oversamples the minority class.

Categorical data, such as parental education and household income, was converted into numerical format as machine learning models often require numerical data. For this, label encoding was employed as our categorical variable exhibits an inherent order.

## Data splitting
The dataset was also split into training and testing subset using 80:20 ratio respectively. 
The training subset will be further split into training and validation set using 90:10 ratio respectively, leaving us with 3 data subsets in total (training, validation, and testing set).

## Data normalisation
As most of the features exhibited outliers and differing range of values, Robust Scaler was used on all numerical features except parental education and household income to mitigate the influence of outliers and the varied range of values.

# Building machine learning models
For my project, I incorporated 3 machine learning models:
1. Extreme Gradient Boosting
2. Support Vector Machine 
3. K-Nearest neigbours

## Model validation and optimisation
The default hyperparameters of these 3 machine learning models were validated using the validation set. After validation, hyperparameters of all 3 models were also optimised using the validation set. To identify the most optimal combinations of hyperparameters, GridSearchCV with 5-fold cross validation from sklearn library will be utilised for its ability to display high precision in learning. This works by assessing predictive performance via iterating over all possible combinations of hyperparameter values predefined within the search space. Using the optimised hyperparameter identified by GridSearchCV, all 3 models was re-trained on a combination of training and validation dataset to ensure optimised models were developed on unseen data to reduce overfitting.

## Model evaluation
The optimised models were evaluated on the testing set to check their generalisability to unseen data. The accuracy, precision, recall, and F1-score were used as evaluation metrics to provide a more comprehensive picture of the models’s performances.

<img width="500" alt="Screenshot 2025-01-28 at 12 36 36" src="https://github.com/user-attachments/assets/1e7f0d86-e85a-4784-9b27-8676dc0f4557" />

Graph above shows the the performance of the 3 models before hyperparameter tuning.

<img width="439" alt="Screenshot 2025-01-28 at 12 39 03" src="https://github.com/user-attachments/assets/086d1ff0-f475-4360-90e4-d75b023e652e" />

Graph above shows the performance of the 3 models after hyperparameter tuning. 

The XGBoost classifier with optimised hyperparameters remained the top performing model compared to the other two ML models, with each performance metric all exceeding 0.95.

# Conclusion
In summation, this study demonstrates the competence of ML, integrated with human knowledge and established screening instruments, as a screening tool for common mental disorders. Given the high predictive performances of all three models developed in this project, with XGBoost being the best, this depicts important implications on the early identification of high risk individuals. By doing so, early interventions are implemented, thus preventing symptoms from exacerbating further.

