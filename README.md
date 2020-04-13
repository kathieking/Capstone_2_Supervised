# Capstone_2_Supervised
## Predicting 30-day Readmission for Heart Failure Patients

### Background 
In an effort to reduce 30-day readmissions for certain chronic diseases, the Centers for Medicare & Medicaid Services (CMS) created the Hospital Readmission Reduction Program (HRRP) in October 2012. By reducing Medicare payments to hospitals with excess 30-day readmissions for the conditions specified in the HRRP, this program encourages hospitals to improve communication and care coordination efforts and better engage patients and caregivers with respect to post-discharge planning. 

This Capstone attempts to accurately predict the 30-day readmission rate for heart failure by participating hospital, as well as provide the important variables that influence the readmission ratio, in order to provide actionable information when developing improved discharge planning protocols.


* Part I. Preparing the data
* Part II. Using Supervised Learning methods to predict 30-day readmission ratio for heart failure and feature importance 

## Part I: Preparing the data :scissors:

### The Data
The data was obtained from: https://healthdata.gov/dataset/hospital-readmission-reduction/resource/f3830eb1-2d22-496c-b663-46b54e175d9f. The data was collected in November 2019. 

#### Original Data Files :card_index_dividers: 
- [x]  Unplanned readmissions – number of unplanned readmissions
- [x]  Readmission reduction – provides predicted readmission ratio (CMS predicted) and excess readmission ratio (exceeding CMS prediction); calculate actual readmission ratio (target value) for each hospital
- [x]  Mortality measures – deaths from heart failure
- [x]  Hospital Consumer Assessment of Healthcare Providers and Systems (HCAHPS) – results of standardized survey of hospital patients	
- [x]  Overall Hospital rating and general hospital information

### Additional Data
The data was obtained from: https://www.cdc.gov/nchs/data_access/urban_rural.htm#Data_Files_and_Documentation and https://data.world/niccolley/us-zipcode-to-county-state/workspace/file?filename=ZIP-COUNTY-FIPS_2018-03.csv. The data was collected in November 2019.  

#### Original Data Files :card_index_dividers: 
- [x]  NCHS FIPS – geographical classification codes by county/state
- [x]  ZIP FIPS – match FIPS to ZIP of hospital to provide geographical location of each hospital 

#### Data cleaned/wrangled, files merged, outliers transformed, data normalized 

#### Feature engineering using a combination of visual exploration, correlation, heat-maps, and variable combination


## Part II. Supervised Learning Models :chart_with_upwards_trend:

#### Models Tested:
- [x]  Linear regression model
- [x]  LassoCV
- [x]  RidgeCV
- [x]  ElasticNetCV
- [x]  KNN regression
- [x]  Decision trees
- [x]  Random Forest Regressor 


#### Trials:
* multiple runs of all regression model 
* adjustments for overfitting including cross-validation and train/test
* feature engineering with feature importance
* hyperparameter tuning with random grid search
* key metrics: 
  *   R^2 sq and R^2-adjusted for both train/test 
  *   Cross Validation mean
  *   MAE, MSE, RMSE, MAPE
  *   goal to maximize accuracy of R^2 test and CV mean while guarding against overfitting

#### Supervised Models: Best Results: :bar_chart:
* Model: Random Forrest, top 15 features, tuned hyperparameters
* Results: 
  * R^2 train: **.992**, R^2 test **.974**
  * CV mean **.927**
  * Base: accuracy **.988**, average error 0.0112 degrees
  * HP tuned: accuracy **.999**, average error 0.0090 degrees

#### Evaluation: :clipboard:
The model performed very well in predicting the actual 30-day readmission ratio for heart failure. Although there are concerns for overfitting, the test run and CV run of the model also performed well, 97.4% and 92.7% respectively. In addition to accurately predicting 30-day readmission ratio (heart failure) for each hospital, the model also provides a number of "important features" that influence the 30-day readmission ratio (heart failure). While many of the features, e.g. geographic location or the presence of emergency services, are not readily changable, there are a number of features that represent opportunities for the hospital staff and administration to improve upon. An example of these features include the more general goal of increasing the hospital's STAR rating, while more specific and directly actionable items include both physician communication with the patient and the discharge communication of all staff with the patient. Armed with this knowledge, the focus on improving physician communication at discharge appears to be one of the most effective ways to reduce 30-day readmissions for heart failure. 

The weakness of the model includes a relativley small data set (n=5039), due to the specific focus on heart failure. Although the Random Forest Regressor is well-accepted, there does remain some concern regarding the "black box" workings of the model. 

### Future Goals: :dart:
* Reduce potential variable features with improved understanding of feature engineering 
* Increase the data set by using additional survey cycles as they become available 
 
