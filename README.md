# Netflix Pricing 

# Synopsis
In economics, there’s a concept called purchasing power parity, in which there’s a theoretical exchange rate that allows you to buy the same amount of goods and services in every country.

# Why Netflix? 
Netflix is a streaming service that offers a wide variety of award-winning TV shows, movies, anime, documentaries, and more on thousands of internet-connected devices. It is one of the most popular streaming services today. It is available on a wide variety of countries and its subscription price ranges from country to country as well. 

# Scraping Netflix Data From Source
On 'www.comparitech.com/blog/vpn-privacy/countries-netflix-cost/', there are a variety of data concerning netflix pricing across countries. For simplicity's sake, we choose the first table containing 12 random countries consisting of netflix prices with ads, one of those countries including Canada.

# Scraping GST Data From Source 
The website, 'https://taxsummaries.pwc.com/quick-charts/value-added-tax-vat-rates', consists of data involving VAT rated across countries. We will aggregate the VAT rates so that we could get a sense the full price with taxes in each country. 

# Tidying Up GST Data
In order to combine our data, we had to have a common table for the join function to work. 

Thus, we had to change the way the column "Territory" is formatted. It included when the country's vat was las reviewed. Purely for Analysis, we did not need that, so we had to get rid of it. We then relabeled "Territory" into "Country". From this, we created a temporary common in both tables without any spaces between the country names so that it will be completely identical. 

# Joining Netflix Data with GST Data
As we join our netflix table with our gst table, the countries in our netflix table only remained because it is the only country that is in common with the gst table. 

# Tidying Our Combined Data 
After scraping, we needed to so some data cleaning for the data to be interpretable for analysis. 
1. We dropped the unneccesarry columns.  
2. We split Prices Local into prices and currency codes. 
3. Dropped Brazil after some research as the VAT in the country is very complex. 
