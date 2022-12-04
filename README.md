# Netflix Pricing 

# Synopsis
In economics, there’s a concept called purchasing power parity, in which there’s a theoretical exchange rate that allows you to buy the same amount of goods and services in every country.

# Why Netflix? 
Netflix is a streaming service that offers a wide variety of award-winning TV shows, movies, anime, documentaries, and more on thousands of internet-connected devices. It is one of the most popular streaming services today. It is available on a wide variety of countries and its subscription price ranges from country to country as well. 

# Scraping Netflix Data From Source
On 'www.comparitech.com/blog/vpn-privacy/countries-netflix-cost/', there are a variety of data concerning netflix pricing across countries. For simplicity's sake, we choose the first table containing 12 random countries consisting of netflix prices with ads, one of those countries including Canada.

# Scraping GST Data From Source 
On 'https://taxsummaries.pwc.com/quick-charts/value-added-tax-vat-rates', there consists of data involving VAT rated across countries. We will aggregate the VAT rates so that we could get a sense the full price with taxes in each country. 

# Joining Netflix Data with GST Data

# Tidying GST Data 
After scraping, we needed to so some data cleaning for the data to be interpretable for analysis. 
1. We dropped the unneccesarry columns.  
2. We split Prices Local into prices and currency codes. 
3. Dropped Brazil after some research as the VAT in the country is very complex. 
