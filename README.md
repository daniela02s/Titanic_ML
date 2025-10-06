# Data Science Challenge from Kaggle

The "Titanic: Machine Learning from Disaster" dataset from Kaggle is a classic example for learning and practicing Machine Learning, specifically for **classification tasks**. This project offers a comprehensive view of the field, enabling the development of essential skills in exploring real data, manipulating information, and creating a predictive model.

Despite the well-known tragic story of the sinking, the available data reveals that survival was not purely random. Through analysis, it's possible to go beyond the historical narrative and discover hidden patterns that indicate which groups of people had a significantly higher chance of being saved.

---

### **Development Sequence**
This project followed a standard Data Science workflow:
1.  **Problem Understanding and Environment Setup**: Defining the objective and setting up the tools.
2.  **Data Exploration**: Loading the data and performing an initial analysis of variables.
3.  **Preprocessing and Feature Engineering**: Cleaning the data and creating new variables to optimize the model.
4.  **Modeling and Evaluation**: Applying Machine Learning models and analyzing their performance.
5.  **Final Results and Analysis**: Generating the submission for the challenge.

---

### **Problem Understanding and Environment Setup**
1.  **Project Goal**: The objective is to build a model that can accurately predict whether a passenger survived the Titanic's sinking, using the data provided in the `train.csv` and `test.csv` files.
2.  **Understanding the Variables**: Familiarize yourself with the description of each variable in the dataset, such as `PassengerId`, `Survived`, `Pclass`, `Name`, `Sex`, `Age`, `SibSp`, `Parch`, `Ticket`, `Fare`, `Cabin`, and `Embarked`.

---

### **Data Exploration**
The initial data analysis revealed crucial information about the passengers:
* **Data and Missing Values**: The training set has 891 entries, and a large number of missing values were identified in the `Cabin` column, with fewer in `Age` and `Embarked`.
* **Key Correlations**:
    * **Sex**: The `Sex` variable was the strongest factor for predicting survival. Women had a significantly higher survival probability (approx. 74%) than men (approx. 19%).
    * **Pclass**: Passenger class (`Pclass`) is a crucial indicator of survival, with a clear inverse correlation: the higher the class, the higher the survival rate.
    * **Age**: Survival does not have a linear correlation with `Age`. The data shows that young children and the oldest passenger had high survival rates, while young adults (15-25 years old) had the lowest.

---

### **Preprocessing and Feature Engineering**
This phase was dedicated to cleaning and transforming the data to make it suitable for the model:
* **Handling Missing Values**:
    * **`Embarked`**: The most frequent port of embarkation (`S`) was identified and used to fill the two missing values.
    * **`Fare`**: The missing `Fare` value in the test set was filled with the median of the column.
    * **`Age`**: Missing `Age` values were imputed with the median age for each combination of `Sex` and `Pclass`.
* **Creating New Variables**:
    * **`Title`**: A new `Title` variable was created from the passenger's `Name` and converted into a numerical format.
    * **`Family_Size` and `Is_Alone`**: These were created to represent family size and whether the passenger was traveling alone, respectively.
    * **`Age*Class`**: A new variable was created to capture the interaction between a passenger's age and class.
* **Converting Features**: Categorical variables like `Sex` and `Embarked` were converted to numerical values, and continuous variables `Age` and `Fare` were categorized into ordinal bands.
* **Removing Unnecessary Variables**: Columns such as `Name`, `PassengerId`, `Parch`, `SibSp`, and `Family_Size` were removed as they were not needed for the final model.

---

### **Modeling and Evaluation**
In this stage, several classification models were trained and evaluated using accuracy to determine the best-performing one.

| Model | Training Accuracy |
| :--- | :--- |
| **Random Forest** | 99.00% |
| **Decision Tree** | 99.00% |
| **K-Nearest Neighbors (KNN)** | 86.00% |
| **Support Vector Machines (SVC)** | 85.00% |
| **Logistic Regression** | 81.00% |
| **Perceptron** | 79.00% |
| **Gaussian Naive Bayes** | 78.00% |
| **Artificial Neural Network** | 77.00% |
| **SGDClassifier** | 77.00% |

**Modeling Conclusion**:
The **Random Forest** model achieved the highest training accuracy, making it the most robust and reliable choice for the final Kaggle submission. While the high accuracy could indicate overfitting, Random Forest is an ensemble model that generally handles this problem well.

### **Observations:**

* **Sex and Survival**: The `Sex` variable is the strongest factor for predicting survival. Women had a significantly higher survival probability than men, confirming the historical "women and children first" protocol.
* **Socioeconomic Status and Survival**: The passenger class (`Pclass`) is a crucial indicator of survival. There is a clear inverse correlation: the higher the class, the higher the survival rate. This suggests access to lifeboats was influenced by socioeconomic status.
* **Age and Survival**: Survival is not linearly correlated with `Age`. The data shows that very young children and the oldest passenger had high survival rates, while young adults between 15 and 25 years old had a very low survival rate.
* **Family Size**: The analysis of `Family_Size` and `Is_Alone` reveals that passengers traveling alone or in very large groups had a lower chance of survival, whereas those in a moderately-sized family (2-4 people) had a better chance.
* **Port of Embarkation (`Embarked`)**: The port of embarkation also correlates with survival, with Cherbourg (`C`) having the highest survival rate. This could be related to the socioeconomic status of passengers who boarded there.
