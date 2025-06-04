# ReDIMLProject
## Letterboxd Dataset

**Where Was The Data Sourced?**  
The data was collected via webscraper on a Letterboxd List. The Letterboxd list was designed as a 'movie roulette' and has 10,002 entries ranging many genres and decades. The data was scrapped 4/8/2025.

**Full list of fields can be viewed below but some included are:**
- Film Title  
- Average User Rating (Out of 5)  
- Genre  
- Language  
- Number of Ratings (Total and by star (ie. 1/2 Star, 1 Star, 1 1/2 Star))  
- Watches  
- Likes  

**Known Issues:**  
- The `Release_year` field is fully blank. The webscraper as of posting this has a known unresolved issue pulling the release year data, that I didn't know about until after 3–4 hours of scraping. If anyone has ideas for how best to fix this issue let me know, but otherwise it will likely remain like this.  
- The `genre` data is also a little annoying to use, as it's formatted as a list in each entry.

---
**Steps taken to complete the project**

**Load the data**
- There are 10002 records in the dataset with 29 different features

**Data Preprocessing:**
- Filled missing values with the mean value for Average_rating, Owner_rating, Runtime, Release_year

**Data cleaning and preparation:**
- Removed duplicates and outliers from Runtime, Average_rating and Owner_rating
- Performed target encoding for features like Genre, Spoken_languages, Director, Countries, Original_language, cast

**Exploratory Data Analysis:**

<img src="/images/Correlation_Matrix.jpg" alt="Correlation Matrix" width="600" height="600" />

**Predictive Modeeling:**
- features = ['Genres_encoding','Cast_Count_encoding','Spoken_languages_encoding','Director_encoding','Countries_str_encoding','Original_language_encoding','Watches','Likes','Runtime','Fans','List_appearances','Countries_str_count']
- target = 'Average_rating'

**Here is the Important feature identified by the model ( Excluding VIF Columns)**
  <img src="/images/Feature_imp_randomsearched_vif.jpg" alt="Feature Importance" width="600" height="600" />

**Hyperparamenter Tuning**
 - Define the parameter distribution for RandomizedSearchCV
param_distributions = {
    'n_estimators': randint(50, 500),  # Number of boosting rounds
    'learning_rate': uniform(0.01, 0.3), # Step size shrinkage
    'max_depth': randint(3, 10),       # Maximum depth of trees
    'min_child_weight': randint(1, 6), # Minimum sum of instance weight (hessian) needed in a child
    'gamma': uniform(0, 0.4),          # Minimum loss reduction required to make a further partition
    'subsample': uniform(0.6, 0.4),    # Subsample ratio of the training instance
    'colsample_bytree': uniform(0.6, 0.4), # Subsample ratio of columns when constructing each tree
    'reg_alpha': uniform(0, 0.5),      # L1 regularization term on weights
    'reg_lambda': uniform(0, 0.5)      # L2 regularization term on weights
}

X = X_minmax.drop(columns=['Spoken_languages_encoding','Countries_str_encoding','Genres_encoding','Likes','Cast_Count_encoding']) # dropped these features as these where correlated to each other

**Here is the Comparision of different Models**

  <img src="/images/Comparision_of_all_models.jpg" alt="Comparison of all models" width="800" height="500" />

**Here is the Comparision of Actual data vs Predicted data**
  <img src="/images/Comparison_Actual_Predicted_randomsearched_vif.jpg" alt="Actual vs Predicted" width="600" height="600" />

**Recommendations:**
- Rating prediction for New/Unreleased Movies
- Targeted improvements for poorly rated movies

---
