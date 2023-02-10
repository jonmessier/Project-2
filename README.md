# Predict students' dropout and academic success

Problem Statement:
Overview found [HERE](https://archive-beta.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success)

A dataset created from a higher education institution (acquired from several disjoint databases) related to students enrolled in different undergraduate degrees, such as agronomy, design, education, nursing, journalism, management, social service, and technologies. The dataset includes information known at the time of student enrollment (academic path, demographics, and social-economic factors) and the students' academic performance at the end of the first and second semesters. The data is used to build classification models to predict students' dropout and academic sucess. The problem is formulated as a three category classification task, in which there is a strong imbalance towards one of the classes.

- For what purpose was the dataset created? The dataset was created in a project that aims to contribute to the reduction of academic dropout and failure in higher education, by using machine learning techniques to identify students at risk at an early stage of their academic path, so that strategies to support them can be put into place. The dataset includes information known at the time of student enrollment – academic path, demographics, and social-economic factors. The problem is formulated as a three category classification task (dropout, enrolled, and graduate) at the end of the normal duration of the course.

- Who funded the creation of the dataset? This dataset is supported by program SATDAP - Capacitação da Administração Pública under grant POCI-05-5762-FSE-000191, Portugal.

- Are there recommended data splits? The dataset was used, in out project, with a data split of 80% for training and 20% for test.

- Was there any data preprocessing performed? We performed a rigorous data preprocessing to handle data from anomalies, unexplainable outliers, and missing values.

- Has the dataset been used for any tasks already? The dataset was used in a pilot project to provide the tutoring team at our higher education institution with an estimate of the risk of dropout and failure. With this information, the tutoring team provides more accurate help to students.

- Citation Requests/Acknowledgements: If you use this dataset in experiments for a scientific publication, please kindly cite our paper: M.V.Martins, D. Tolledo, J. Machado, L. M.T. Baptista, V.Realinho. (2021) "Early prediction of student’s performance in higher education: a case study" Trends and Applications in Information Systems and Technologies, vol.1, in Advances in Intelligent Systems and Computing series. Springer. DOI: 10.1007/978-3-030-72657-7_16

- License: This dataset is licensed under a Creative Commons Attribution 4.0 International (CC BY 4.0) license. This allows for the sharing and adaptation of the datasets for any purpose, provided that the appropriate credit is given.

---
# Data Dictionary
Please see the [Data Dictionary](https://archive-beta.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success)

## Columns dropped

Through Exploratory visual analysis the following columns were deemed incomplete or insignificant in modeling the dropout rate.  
- `Marital status`
- `Previous qualification`
- `Nacionality`
- `Curricular units 1st sem (credited)`
- `Curricular units 1st sem (without evaluations)`
- `Curricular units 2nd sem (credited)`
- `Curricular units 2nd sem (without evaluations)`

## Target Variable 
- `Target` - The target variable shows students graduating (60.1%) while the minority dropped out (39%).  The data imbalance was addressed using over-\under-\SMOTE for each of the models used.  The choice varied for each model
---
# Visualizations
## Heatmap
Using a heatmap I determined which features had the strongest correlation to the target variable.

![png](https://drive.google.com/uc?id=19dnZ9T6yEh1O9Z5NWU8RiGgYQFrIJ3lk)

## Grades/Dropout rates
The correlation between good grades and graduating is not understated in this data. While my initial thoughts were to look at socio-economic factors for predicting dropout rates, I was left with the simple fact that good students who get good grades have the strongest tendancy to graduate. This will be made obvious in the next graphics. These graphics show the distribution of student grades and their dropout rates. I observe:

- Graduates shown in blue have a 1st semester mean grade of 13.1 with a tight distribuition bewtween 10 and 17. Outliers are to the high side. In the second semester the mean graduate grade is 13.14 with a tight distribution from 10 to 17.
- Dropouts shown in orange have a 1st semester mean grade of 12.1 with a wide distribuition bewtween 0 and 12.5. There are a few outliers on high side. In the second semester the mean dropout grade is 12.07 with a wide distribution from 0 to 12.5.

**NOTE** in these graphics I don not show the count of students with a zero score for their semester grade in the histogram plots on the left. The mean grade values for graduate and dropouts is calculated without the 0-values. In the box plots on the right of the image I include the 0-value grades. I do this to show how narrow the grade range is for graduates and how wide it goes for dropouts

![png](https://drive.google.com/uc?id=1AIUredxVWf97g0HJOq3WQUcicvnpruEI)
![png](https://drive.google.com/uc?id=1ANCjPLg0hQbLm1t2pFjYTCOTCW4IeAo3)

---
# Classification models
For each model a comparison of Accuracy, Precision, Recall, and F1 scores was complied for various implementations. These implementations included:
1. Under-\Over-\SMOTE to balance the target variable
2. Using Principal Component Analysis (PCA) to reduce dimensionality
3. Tuning model hyperparmeters (GridSearchCV)
4. Tuning with PCA

## Random Forest Classifier scores
![png](https://drive.google.com/uc?id=19fbOLUaqi63WsisQwYFUxR9JpldBaq9j)

## K Nearest Neighbors Classifier scores
![png](https://drive.google.com/uc?id=19kkmW460WupAjE8krRoSLEU8-5bjTRvF)

---
#Conclusion

Based on the model scores, the Gridsearch CVRandom Forest Classifier without PCA shows the highest Accuracy, Precision, Recall and F1. 

![png](https://drive.google.com/uc?id=1AP_t1g6x2UJc718-NhDN_T9UtZivFNZV) ![png](https://drive.google.com/uc?id=19fbOLUaqi63WsisQwYFUxR9JpldBaq9j)
---
#Limitations
