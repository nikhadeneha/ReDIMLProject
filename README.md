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

**Here is the Comparision of different Models**

  <img src="/images/Comparision_of_all_models.jpg" alt="Comparison of all models" width="500" height="500" />

**Here is the Comparision of Actual data vs Predicted data**
  <img src="/images/Comparison_Actual_Predicted_randomsearched_vif.jpg" alt="Actual vs Predicted" width="600" height="600" />

---
