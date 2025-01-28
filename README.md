# Predicting-mental-health-with-Machine-Learning
My project aims to utilise machine learning techniques to identify early adolescents at high-risk of mental disorders during late adolescence. It will specifically focus on how well the combined effects of different facets of familial characteristics at the age of 14 can identify high risk cohort members at the age of 17.


![Screenshot 2025-01-28 at 11 41 15](https://github.com/user-attachments/assets/9da55b92-5ef3-458c-a87a-347a9f455515)

# Methodology

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
