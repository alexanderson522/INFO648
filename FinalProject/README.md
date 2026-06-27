This Jupyter notebook builds multiple models (Random Forest & Logistic Regression) to forecast which states in the Mid Atlantic (NY, NJ, PA) will experience growth from 2020 to 2030. Models have been trained on 2010 data such as tract density, age makeup, demographics, and home ownership/vacancy and then fit to 2020 tract populations to measure efficacy of the models. Growth is defined as a percentage of tracts in the state that see growth from one census to the next.

Data was collected from the US Census and has been loaded in via raw .csv files. 
Data was filtered to just look at select states (NY, NJ, PA)
Data was then filtered to exclude tracts with a population of less than 50 - these tracts were considered to be non-residential (airports, industrial areas, etc.). No-land tracts were also filtered out (none seemed to exist in the region, but filter was run regardless).

Per tract numeric features were calculated to get rates of age, demographics, home ownership within each tract. These features were then used to train our models.

K-means clustering was performed and elbow method was used to determine that k=4 should be used. 

After clustering, our two models (logistic regression and random forest) were built and fitted with and without the clustering.

Upon evaluation, it was determined that clustering did not help our models, so forecasting was performed without the clustering.

The Random Forest model (without clustering) proved to be highly effective at predicting growth on a tract basis, with an AUC of 0.813. This model was then used to forecast growth from 2020 to 2030, where it predicted that New Jersey will have the highest percentage of tracts with growth of the three states. 

There are some important limitations to note for this model. First, the model simply gives a yes/no answer as to whether a tract will grow, it does not predict the rate of growth. 
Second, this model is trained using 2010 census data (with 2020 census population as the means to check growth). Any forecasting done on this model will be done with the assumption that trends from 2010 to 2020 can be carried over to other decades. 


**To Run this .ipynb**
1. Load given .csv into the python environment
2. Run all cells in order
3. Review results
