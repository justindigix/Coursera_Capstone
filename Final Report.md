# Capstone Project - The Battle of Neighborhoods 

## Finding the most suitable neighborhood in Toronto

### 1. Introduction

The purpose of this project is to suggest a more suitable neighborhood in a new city for a new immigrant or a visitor for a staying over months,  in terms of living costs, social presence, traffic connectivity, and joyful equipment. 

Toronto is the capital city of the Canadian province of Ontario. With a recorded population of 2,731,571, it is the most populous city in Canada and the fourth most populous city in North America. The city is the anchor of the Golden Horseshoe, an urban agglomeration of 9,245,438 people (as of 2016) surrounding the western end of Lake Ontario, while the Greater Toronto Area (GTA) proper had a 2016 population of 6,417,516. Toronto is an international center of business, finance, arts, and culture and is recognized as one of the most multicultural and cosmopolitan cities globally.

The diverse population of Toronto reflects its current and historical role as an important destination for immigrants to Canada. More than 50 percent of residents belong to a visible minority population group, and over 200 distinct ethnic origins are represented among its inhabitants. While most Torontonians speak English as their primary language, over 160 languages are spoken in the city.

### 2. Data description

#### 2.1 Postal codes of Toronto

Data Link: https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M

This data source contains the borough, neighbourhoods in terms of postal codes.

#### 2.2 Location coordinates with respect to postal codes of Toronto

Data Link: http://cocl.us/Geospatial_data

This data source contains the locations of boroughs/neighbourhoods (latitude and longitude) in terms of postal codes.

#### 2.3 Foursqure API

The data retrieved from Foursquare contained information of venues within a specified distance of the longitude and latitude of the postcodes.

#### 2.4 Housepricehub (web scrapping)

Data Link: https://housepricehub.com/cities/city/Toronto

This data source is added for fetching the average house prices in city Toronto.

#### 2.5 Data specifications:

1. Neighborhood
2. Neighborhood Latitude
3. Neighborhood Longitude
4. Venue
5. Name of the venue e.g. the name of a store or restaurant
6. Venue Latitude
7. Venue Longitude
8. Venue Category
9. House price
10. Numbers of schools

### 3. Methodology Section

#### 3.1 Clustering approach:

To categorize the neighborhoods in city Toronto, we decided to segment the neighborhoods in terms of the postal codes. Then, we explore the venues of all neighborhoods and group the venues into unique types, which are defined by Foursqure. After one-hot encoding, we obtain the appearences of grouped venues' types for each neighborhood and apply K-means clustering algorithms with respect to the normalized frequencies of appearences.

- Applying K-Means Clustering Approach with k optimization

![K-means](https://raw.githubusercontent.com/justindigix/Coursera_Capstone/master/k_means.png)

`k=7` is the most proper value.

- Most Common venues in the neighborhoods:

![Most Common venues](https://raw.githubusercontent.com/justindigix/Coursera_Capstone/master/most%20common%20venues.png)

### 4. Results section

Map of clusters in Toronto

![Map of clusters](https://raw.githubusercontent.com/justindigix/Coursera_Capstone/master/clustering%20map.png)

Average Housing Price for each neighborhood in Toronto

![Average Housing Price](https://raw.githubusercontent.com/justindigix/Coursera_Capstone/master/average%20prices.png)

### 5. Discussion Section

The School numbers are too sparse and therefore cannot be applied as a significant independent values. We can solve this problems by using another data source, i.e., census data of school rating. 

The results shows that the geo-distribution of clustering is briefly consistent to the tiers of average house prices. In the conclusion section, we will see it.

### 6. Conclustion Section

Finally, we obtained an overview of the categories of neighborhoods in city Toronto underneath,

- Cluster 0: downtown with high living cost or crowded space. A reversed 'T' formed region can be obviously discovered. The price tier of this region is about 1M-3M. This cluster should be the best choices of people working in the downtown and can bear the small space with affordable price. 
- Cluster 1: Luxury areas. The price tier can approach to '>5M'. This cluster is suitable for rich people.
- Cluster 2: Mid-high living cost. it is teared apart by Cluster 0 from the middle. This cluster is the best for the mid-class.
- Cluster 3-7: neighbours far away from the center with different features. 
