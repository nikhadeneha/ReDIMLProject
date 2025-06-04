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
## <u>Steps taken to complete the project</u>

**1.Load the data**
- There are 10002 records in the dataset with 29 different features

**2.Data Preprocessing:**
- Filled missing values with the mean value for Average_rating, Owner_rating, Runtime, Release_year

**3.Data cleaning and preparation:**
- Removed duplicates and outliers from Runtime, Average_rating and Owner_rating
- Performed target encoding for features like Genre, Spoken_languages, Director, Countries, Original_language, cast

**4.Exploratory Data Analysis:**

- Univariate Analysis
- Bivariate Analysis
- Multivariate Analysis

<img src="/images/Exploratory_Data_Analysis.jpg" alt="Exploratory_Data_Analysis" width="700" height="600" />

## <u>Predictive Modeling:</u>
- features 'Genres_encoding','Cast_Count_encoding','Spoken_languages_encoding','Director_encoding','Countries_str_encoding','Original_language_encoding','Watches','Likes','Runtime','Fans','List_appearances','Countries_str_count'
- target = 'Average_rating'

**1.Comparing Model Performance.Feature importance based on HyperParameter Tuned XGBoost**
<img src="/images/Model_Comparision_Before_VIF.jpg" alt="Model Comparision Before VIF" width="400" height="250" /> <img src="/images/Feature_imp_Hypertune_withoutvif.jpg" alt="Feature Importance on Hypertune without vif" width="400" height="250" />

**2.Performed VIF on the data to handle the multicollinearity**
<img src="/images/VIF_Calculation.jpg" alt="VIF Image" width="800" height="500" />

**3.Comparing Model Performance after removing Multicorrelated columns.Feature importance based on HyperParameter Tuned XGBoost**

<img src="/images/Model_Comparision_After_VIF.jpg" alt="Model Comparision After VIF" width="400" height="250" /> <img src="/images/Feature_imp_randomsearched_vif.jpg" alt="Feature Importance" width="400" height="250" />

**4.Hypertuned XGBoost's Model Performance on Test Data**

<img src="/images/Model_Prediction_nonVIF.jpg" alt="Model Performance on Non-VIF Data" width="400" height="250" /> <img src="/images/Model_Prediction_VIF.jpg" alt="Model Performance on VIF Data" width="400" height="250" />

**Recommendations:**
- Rating prediction for New/Unreleased Movies
- Targeted improvements for poorly rated movies

---
