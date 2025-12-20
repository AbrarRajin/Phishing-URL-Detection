
# Phishing URL detection from Web Characteristics using Machine Learning Techniques.





### Dataset acknowledgement:
```
Prasad, A., & Chandra, S. (2023). PhiUSIIL: A diverse security profile empowered phishing URL detection framework based on similarity index and incremental learning. Computers & Security, 103545. doi: https://doi.org/10.1016/j.cose.2023.103545
```
 
### Dataset Link:
 UC Irvine Machine Learning Repository:  
[Dataset Source Link](https://archive.ics.uci.edu/dataset/967/phiusiil+phishing+url+dataset)

---

### Dataset Information:
- Labeled - YES  
- Classification Type: Binary Classification  
- Number of Classes: Phishing (0) and Legitimate (1)  
- Number of Samples: 235,795
- Number of Features: 56
---


## Data Preprocessing

1. Data Cleaning  
Drops irrelevant columns: FILENAME, URL, DOMAIN, TLD, TITLE to avoid training issues and focus on numerical features.

    Selects only numeric columns via 
    ```
    df.select_dtypes(include=['number']).copy().
    ```

    Removes duplicate rows with 
    ```
    df.drop_duplicates().​
    ```

2. Train-Test Split  
    Splits features (X: all but last column) and target (y: last column) using train_test_split(test_size=0.2, random_state=42, stratify=y).

    Keeping 20% for Testing and Training the rest of the 80%.

3. Feature Scaling  
    Applies StandardScaler fitted on training data only, then transforms both train and test sets.

    Converts scaled data back to DataFrames preserving column names and indices.​

4. Handling Class Imbalance  
    Compares oversampling methods: SMOTE, ADASYN, BorderlineSMOTE by checking class distributions (ytrain.value_counts()).

    Applies SMOTE (SMOTE(random_state=42).fit_resample()) to create balanced training sets (Xtrainresampled, ytrainresampled).​

5. Feature Selection  
    Uses SelectKBest with ANOVA F-test (f_classif, k=20) on resampled training data.

    Selects top features, applies to test set, and visualizes F-scores with a horizontal bar plot.

    Outputs selected feature names and shapes for train/test selected sets.​


    
    ## Data Preprocessing
