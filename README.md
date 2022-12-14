# Netflix Index 
Authors: Maria Onido and Aditi Padhi

![This is an image](https://upload.wikimedia.org/wikipedia/commons/7/7a/Logonetflix.png "Netflix")

## Synopsis
"In economics, there’s a concept called purchasing power parity, in which there’s a theoretical exchange rate that allows you to buy the same amount of goods and services in every country."


## Why Netflix? 
"Netflix is a streaming service that offers a wide variety of award-winning TV shows, movies, anime, documentaries, and more on thousands of internet-connected devices." It is one of the most popular streaming services today. It is available on a wide variety of countries and its subscription price ranges from country to country as well. 


## Step 1. Netflix Data 
On 'www.comparitech.com/blog/vpn-privacy/countries-netflix-cost/', there are a variety of data concerning Netflix pricing across countries. For simplicity's sake, we choose the first table containing 12 random countries consisting of netflix prices with ads, one of those countries including Canada. Upon getting this data, we only selected the necessary columns. 



## Step 2. VAT Data
The website, 'https://taxsummaries.pwc.com/quick-charts/value-added-tax-vat-rates', consists of data involving VAT rates across countries. We will aggregate the VAT rates to the Netflix pricing data. 


## Step 3: Creating a Temporary Common Column 
In order to combine our data, we had to have a common table for the join function to work. 

Thus, we had to change the way the column "Territory" is formatted in our VAT table. It included when the country's VAT was last reviewed. For Analysis, we didn't need that, so we had to get rid of it. We then removed all the white spaces between the territory names so that we have a temporary common column. We also added a temporary common column in our Netflix table without the white spaces in the country names. This is so that it will be completely identical for our join function. 

![code_two](A4A0F750-7FCE-4A56-92DE-BFC413F98386_4_5005_c.jpeg "Code2")
![code_one](46957E22-D4BB-4CDF-BA33-27A2DD7EE9AF_4_5005_c.jpeg "Code1")
#### Why? 
"South Korea " (with space at the end) is not the same as "South Korea" (without the space at the end). 

## Step 4: Joining Netflix and VAT  
As we join our Netflix table with our VAT table, the countries in our Netflix table only remained because it is the only country that is in common with the VAT table. We then dropped the temporary country column and kept the "Country" column from the Netflix pricing table. 


## Step 5: Tidying up Combined Data 
After scraping, we needed to so some data cleaning for the data to be interpretable for analysis.   
1. We split Prices Local column in our Netflix table into 2 columns; Prices and Currency Codes.
2. Dropped Brazil after some research as the VAT in the country is very complex.
3. Cleaned the 'Standard VAT rate %' column by determining the value base on the original column and some research.
![code_four](5FCB0B27-C053-4931-AA17-50D9712DB4D4_1_201_a.jpeg "Code4")


## Step 6: Calculating Local Prices with VAT rates 
Our prices and VAT rates are now floats and are ready to work with. We multiplied each price with the corresponding VAT percentage (as a decimal) and added that value to the original price. In this way we get an idea of how much you will eventually pay. 


## Step 7: Converting Local Prices with VAT rates into Canadian Dollars 
This is the conversion function we used. It is inspired from a very similar function from CMPUT 174. It will take three arguments:
- Argument 1 is the currency you are converting from 
- Argument 2 is the currency you are converting to 
- Argument 3 is the amount in the currency you are converting from 

![code_five](50E26EA2-F2E3-4152-A52C-2D3E5C777E6C_4_5005_c.jpeg "Code5") 

To obtain a conversion to column, we had to make an array of 'CAD' the same length as our table. We converted all the prices with VAT rates added using a conversion function we made. In this way all of the prices are all in the same units - Canadian Dollars. 



## Step 8: The Differences 
Since all of the prices are now in the same units, we subtracted Canada's price with VAT from each of the countries. This is if you live in Canada, which country could you find the price for Netflix the cheapest out of all the ones we have. We removed Canada because it is the country we are basing the difference from. 


### Price Differences From Candian Price 
![difference](difference.png "Difference")

As you can see South Korea is the only country that is in the slight negatives, meaning it is lower than Canada's price with taxes. The rest of the countries have prices higher than Canada. 


## Step 9: External Factor - Internet Usage Per Country 
Since Netflix heavily involves access to the internet, we choosed the percentage of internet usage per country for our external factor. 
We gathered the csv file with this Data from 'https://www.kaggle.com/datasets/tanuprabhu/list-of-countries-by-number-of-internet-users'. 
Upon reading the csv file into a table, we only selected the necessary columns for analysis. 


## Step 10: Cleaning Internet Usage Per Country Data 
This data set also needed some cleaning. We cleaned the 'Percentage' column by getting rid of the % and other excess information. We then turned whatever we had left into a float type. 

### Internet Usage Percentage Per Country 
![percentage](internet_percentage.png "Percentage") 

South Korea has the highest internet usage at 95.1 and Italy has the lowest at 65.1. 


## Step 11: Plotting the Correlation Between the Differences and Internet Usage Per Country

### Correlation Between Prices Differences and Internet Usage Per Country 
![scatter](scatter.png "Scatter")  

From the scatterplot, there is a weak negative correlation between the differences and internet usage per country. The correlation calculated is around -0.3. This means that there is a slight trend that as the internet usage goes up, the price of Netflix goes down. 

## Does this Imply Causation? 
No, it does not imply causation. There are confounding factors involve. 
1. Number of movies available in each country can affect the subscription price.
2. Netflix might introduce a new product feature that can up their price.
3. Fluctuations in the economy. For Example, as fears of recession and cost of living goes up, some people might re-evaluate their expenses and this can affect the price of Netflix. 
* These are just examples, there's more that is involved. 

## Conclusion
In this assignment, we have learnt that a Netflix subscription is the cheapest in South Korea. 

So, if you want to buy a Netflix subscription at a cheaper price than Canada and save some money every month, you should plan on moving to South Korea


## Citations
https://upload.wikimedia.org/wikipedia/commons/7/7a/Logonetflix.png
https://docs.google.com/document/d/11eFi3iy0TIwzh9KY3BYRP5IhXcS7WRZswExTSKYOz8w/edit - for synopsis
https://www.netflix.com/ca/ - What is Netflix? 
