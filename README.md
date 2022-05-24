# Project 2: Ames Housing Pricing Model

### Contents:
- [Problem Statement](#Problem-Statement)
- [Executive Summary](#Executive-Summary)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)
- [Data Dictionary](#Data-Dictionary)
- [Sources](#Sources)

### Problem Statement

Our firm wants to diversify our portfolio by getting into the real estate business in Ames, Iowa. Like any instrument, we want to know if our return will make the investment worthwhile.
Using available data, build a linear regression model for estimating the sale price of a home. Which types of attributes are good indicators of value and which detract? How accurate can we be?

### Executive Summary

The project is separated into two parts: (1) EDA and Cleaning (2) Regression and Analysis
<br><br>
(1) EDA and Date Cleaning
The workbook imports the Ames housing dataset comprised of 2051 individual residential properties sold in Ames, Iowa from 2006 to 2010. Each record included 78 exploratory variables and the target variable sale price. Each exploratory variable was cleaned, examined, and analyzed for inclusion in the final model. Techniques such as null-handling through imputation, dummy variables on categorical variables, and outlier removal were used as well as engineering new features from the data.
<br><br>
(2) Regression and Analysis
84 exploratory variables were initally available for modelling. An initial linear regression was performed across all exploratory variables and reviewed against a train-test split as well as cross validation scoring. The variables were then standard scaled to perform Lasso and Ridge regressions. Finally, feature selection through both Lasso cross validation and Ridge cross validation were performed, indicating that only 57 the original 84 exploratory variables were important to our model. These 57 variables were kept and linear regression was again performed on regular scaled dataset to generate our model's final coefficients.

### Conclusions and Recommendations

There are a wide range of exploratory variables that have an affect on the target variable sale price according to our model. Witihin the context of the magnitude of these variables' units, the most impacting variables were identified.

Three most positively impacting variables:
  *  Membership in Neighborhood Grouping 3
    *  a generated collection of neighborhoods that had a mean sale price one standard deviation above the overal sale price mean.
    *  membership here adds \$33k in expected sale price holding all else constant
  *  Above Grade Living Area (Square Footage):
    *  every 500 sqft adds \$25k in expected sale price holding all else constant
  *  Location in 'Floating Village Residential' zone
    *  houses sold in this zone see a \$15k increase in expected sale price holding all else constant
    *  for context, the second highest-scoring zone is 'Residential Low Density' at \$4k

Three most negatively impacting variables:
  *  Presence of a basement
    *  houses with a basement saw a \$23K decrease in expected sale price holding all else constant
  *  Home Age
    *  each year before 2010 that a home was built decreases the expected sale price \$200 holding all else constant
    *  this translates to a \$20K difference for a home over 100 years old
  *  Home Remodels
    *  houses that were remodeled saw a \$3.6K decrease in expected sale price holding all else constant

In place of sufficient values being available for the 57 variables included in the model, prioritizing the above variables will maximize impact on the expected sale price.

### Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|1st_flr_sf|*int*|Ames Housing Data|First Floor square feet|
|all_porch_sf|*int*|Ames Housing Data|Total square feet across all porch types|
|bedroom_abvgr|*int*|Ames Housing Data|Bedrooms above grade (does NOT include basement bedrooms)|
|bldg_type_1Fam|*int*|Ames Housing Data|Indicator for Type of dwelling being Singel-family Detached|
|bsmt_ALQ_sf|*float*|Ames Housing Data|Total square feet across basement finished areas rated Average Living Quarters|
|bsmt_BLQ_sf|*float*|Ames Housing Data|Total square feet across basement finished areas rated Below Average Living Quarters|
|bsmt_cond_is_TA_Gd_Ex|*int*|Ames Housing Data|Indicator for general condition of the basemetn being Excellent, Good, or Typical-slight dampness allowed|
|bsmt_GLQ_sf|*float*|Ames Housing Data|Total square feet across basement finished areas rated Good Living Quarters|
|bsmt_qual_Ex_Gd|*int*|Ames Housing Data|Indicator for height of the basement being 90+ inches|
|electrical_is_SBrkr|*int*|Ames Housing Data|Indicator for Electrical system being Standard Circuit Breakers & Romex|
|exter_qual_Ex_Gd|*int*|Ames Housing Data|Indicator for quality of the material on the exterior being Excellent or Good|
|exterior_has_HdBoard|*int*|Ames Housing Data|Indicator for Exterior covering on the house includes Hard Board|
|exterior_has_MetalSd|*int*|Ames Housing Data|Indicator for Exterior covering on the house includes Metal Siding|
|exterior_has_Plywood|*int*|Ames Housing Data|Indicator for Exterior covering on the house includes Plywood|
|exterior_has_VinylSd|*int*|Ames Housing Data|Indicator for Exterior covering on the house includes Vinyl Siding|
|exterior_has_Wd_Sdng|*int*|Ames Housing Data|Indicator for Exterior covering on the house includes Wood Siding|
|fireplace_qu_Ex_Gd|*int*|Ames Housing Data|Indicator for Fireplace quality being Excellent or Good|
|foundation_PConc|*int*|Ames Housing Data|Indicator for Type of foundation being Poured Concrete|
|garage_area|*float*|Ames Housing Data|Size of garage in square feet|
|garage_finish_Fin|*int*|Ames Housing Data|Indicator for Interior finish of the garage being Finished|
|garage_finish_RFn|*int*|Ames Housing Data|Indicator for Interior finish of the garage being Rough Finished|
|garage_new_2006|*int*|Ames Housing Data|Indicator for the Year garage was built being 2006 or newer|
|gr_liv_area|*int*|Ames Housing Data|Above grade (ground) living area square feet|
|has_alley|*int*|Ames Housing Data|Indicator for Alley access to the property|
|has_basement|*int*|Ames Housing Data|Indicator for house having a basement|
|has_bsmt_exposure|*int*|Ames Housing Data|Indicator for walkout or garden level wall exposure existing|
|has_central_air|*int*|Ames Housing Data|Indicator for Central air conditioning|
|has_fence|*int*|Ames Housing Data|Indicator for house having a fence|
|has_garage|*int*|Ames Housing Data|Indicator for house having a garage|
|has_porch|*int*|Ames Housing Data|Indicator for house having a porch|
|home_age|*int*|Ames Housing Data|The age of the house in 2010|
|home_has_remodel|*int*|Ames Housing Data|Indicator for the house having a remodel|
|is_fully_paved_drive|*int*|Ames Housing Data|Indicator for Type of road access to property being fully paved|
|is_functional|*int*|Ames Housing Data|Indicator for Home functionality being Typical functionality|
|is_heating_qc_Ex|*int*|Ames Housing Data|Indicator for Heating quality and condition being excellent|
|is_land_countour_hls|*int*|Ames Housing Data|Indicator for Flatness of the property being Hillside - significan slope from side to side|
|is_land_slope_mod|*int*|Ames Housing Data|Indicator for Slope of property being Moderate|
|is_lot_shape_regluar|*int*|Ames Housing Data|Indicator for General shape of property being Regular|
|kitchen_qual_Ex_Gd|*int*|Ames Housing Data|Indicator for Kitchen quality being Excellent or Good|
|lot_area|*int*|Ames Housing Data|Lot size in square feet|
|lot_config_Corner|*int*|Ames Housing Data|Indicator for Lot configuration being Corner lot|
|lot_frontage|*float*|Ames Housing Data|Linear feet of street connected to property|
|mas_vnr_area|*float*|Ames Housing Data|Masonry veneer area in square feet|
|mas_vnr_type_BrkFace|*int*|Ames Housing Data|Indicator for Masonry veneer type being Brick Face|
|mas_vnr_type_Stone|*int*|Ames Housing Data|Indicator for Masonry veneer type being Stone|
|ms_subclass_group_1|*int*|Ames Housing Data|Indicator for membership in a MS SubClass with an average mean sale price between $101,898 and $181,217|
|ms_zoning_FV|*int*|Ames Housing Data|Indicator for general zoning classification being Floating Village Residential|
|ms_zoning_RL|*int*|Ames Housing Data|Indicator for general zoning classification being Residential Low Density|
|neighborhood_group_1|*int*|Ames Housing Data|Indicator for membership in a Neighborhood with an average mean sale price between $101,898 and $181,217|
|neighborhood_group_3|*int*|Ames Housing Data|Indicator for membership in a Neighborhood with an average mean sale price $260,536 and above|
|overall_qual|*int*|Ames Housing Data|Rates the overal material and finish of the house on a scale from 1-10|
|roof_style_Hip|*int*|Ames Housing Data|Indicator for type of roof being Hip|
|sale_type_New|*int*|Ames Housing Data|Indicator for type of sale being New - Home just constructed and sold|
|total_baths|*float*|Ames Housing Data|Total amount of baths where full and half are both considered one bath|
|total_bsmt_sf|*float*|Ames Housing Data|Total amount of basement square feet|
|totrms_abvgrd|*int*|Ames Housing Data|Total rooms above grade (does not include bathrooms)|
|yr_sold_2006|*int*|Ames Housing Data|Indicator for sale date of house being in 2006|

### Sources
Ames, Iowa Assessor’s Office ([data info](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt))