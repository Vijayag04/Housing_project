
# Project Title : Housing Project


**Objective**
- The goal of this project is to develop a model that will predict house prices in King County as accurate as possible.

# Loading Data 

We've given a dataset with housing prices and other features, such as size of the house, 
how many bedrooms, overall condition and<br> others. Let's take a look at features we have and their meaning:




- **id** - A notation for a house
- **date** - Date house was sold
- **price** - Price is prediction target
- **bedrooms** - Number of Bedrooms/House
- **bathrooms** - Number of bathrooms/bedrooms
- **sqft_living** - Square footage of the home
- **sqft_lot**- Square footage of the lot
- **floors** - Total floors (levels) in house
- **waterfront** - House which has a view to a waterfront
- **view** - Has been viewed
- **condition** - How good the condition is ( Overall )
- **grade**- Overall grade given to the housing unit, based on King County grading system
- **sqft_above** - square footage of house apart from basement
- **sqft_basement** - square footage of the basement
- **yr_built** - Built Year
- **yr_renovated** - Year when house was renovated
- **zipcode** - Zipcode
- **lat**- Latitude coordinate
- **long** - Longitude coordinate
- **sqft_living15** - Living room area in 2015 (implies-- some renovations) This might or might not have affected the lotsize area
- **sqft_lot15** - Lot size area in 2015 (implies-- some renovations)


**Setting Up Our Data**:  The modules I imported were:

- pandas for data analysis
- numpy for scientific computation
- matplotlib for basic plotting
- seaborn for advanced plotting
- statsmodel for  modeling & evaluations
- sci-kit learn for modeling & evaluations

# Cleaning the Data

During this stage, we'll focus on preprocessing our data. Important steps such as identifying and removing null values, dealing <br>with outliers and normalizing data,

**Checking correlation between the features of dataframe.**

![image1.png](attachment:image.png)

- The darkest red outputs illustrate the strongest positive linear relationships as far as we can strictly from
correlation<br> coefficients and the blue values are the negative linear relationships.
- The values that describe each house's sqft_living and grade,sqft_living and price are often strongly
correlated<br> with each other
- There is strong correlation between sqft_living and sqft_above, it would be reasonable to remove one of them.

**Most House Sales in a Month**

![image2.png](attachment:image.png)

The most house were sold in the months of May, April and July.

Usually location plays considerable role in forming house price. Below you can find locations of houses that has been sold and their price ranges. <br>A Scatterplot of king county, longitude with latitude on the price range.

![image3.png](attachment:image.png)

# Linear Regression Model

We could explore Linear regression for all variables vs. price to see how they affect saleprice individually (R squared) and<br>also verify if the independent variables selected are statistically significant (p-value....the lower they are for the corresponding <br>variables the more statistically significant they are). After trying few models  finally used this 
model since it has R^2 value as 75%.

Data was scrubbed to get better r^2 value in following ways
- Handled the null values and dropped few columns.

- Eliminated the outliers on columns 
 - price < 4000000
 - sqft_living < 8000
 - sqft_lot < 500000
 - bedrooms < 5
 - bathrooms < 4 

- Transformed the categorical variables like waterfront, view, grade, condition, zipcode and yr_renovated<br>
- Performed Logarithmic Transformation on price, sqft_living, sqft_lot, bathrooms

**Checking for Normality<br>**
We should check to ensure that our residuals are normally distributed. As we've seen before, a Q-Q plot is a helpful visual for analyzing this.

Train MSE: 0.061275157957496704<br>
Test MSE: 0.062086696973421146<br>
RMSE Train: 0.24753819494675303<br>
RMSE Test: 0.24917202285453546<br>
R2 Score: 0.752

![image4.png](attachment:image.png)

 Overall, looks fairly robust, although there are some violations near the tails.

# **Checking for Homoscedasticity**<br>

Checking whether the model's errors are indeed homoscedastic or if they violate this principle and display heteroscedasticity.

![image6.png](attachment:image.png)

Scatter plot shows the data are homoscedastic (means the residuals are equal across the regression line).

# Conclusion


- After making necessary cleaning and modification of our data, model-4 performs with 75% accuracy across all of the data.

- Selected important features and rejected the ones that can negatively impact result of the prediction.

- Location and size of the house have biggest impact on house price.
