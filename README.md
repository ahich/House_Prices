# House Prices
Predicting the sale price of houses depending on parameters such as the neighborhood, number of the bedrooms, house type, area, city.

```
 house_id        city  sale_price   sale_date  months_listed  bedrooms  \
0   1217792  Silvertown       55943  2021-09-12            5.4         2   
1   1900913  Silvertown      384677  2021-01-17            6.3         5   
2   1174927   Riverford      281707  2021-11-10            6.9         6   
3   1773666  Silvertown      373251  2020-04-13            6.1         6   
4   1258487  Silvertown      328885  2020-09-24            8.7         5   

      house_type         area  
0  Semi-detached  107.8 sq.m.  
1       Detached  498.8 sq.m.  
2       Detached  542.5 sq.m.  
3           Det.  528.4 sq.m.  
4       Detached  477.1 sq.m.  
```

The work starts with a detailed Exploratory Data Analysis where both explicit NaN and non-NaN invalid values for the fields are treated through cleaning, insertion and text substitution.

Number of NaN occurrences for the fields:

```
house_id          0
city              0
sale_price        0
sale_date         0
months_listed    31
bedrooms          0
house_type        0
area              0
```
However, printing the unique values of each field unveils anomalies like for the house type:

```
['Semi-detached' 'Detached' 'Det.' 'Terraced' 'Semi' 'Terr.']
```
Appropriate text substitutions for this field and the area field, and transformation to the appropriate types are performed to prepare for visualization and modeling:

```
Column Name	Criteria
house_id	Nominal. Unique identifier for houses. Missing values not possible.
city	Nominal. The city in which the house is located. One of 'Silvertown', 'Riverford', 'Teasdale' and 'Poppleton' Replace missing values with "Unknown".
sale_price	Discrete. The sale price of the house in whole dollars. Values can be any positive number greater than or equal to zero.Remove missing entries.
sale_date	Discrete. The date of the last sale of the house. Replace missing values with 2023-01-01.
months_listed	Continuous. The number of months the house was listed on the market prior to its last sale, rounded to one decimal place. Replace missing values with mean number of months listed, to one decimal place.
bedrooms	Discrete. The number of bedrooms in the house. Any positive values greater than or equal to zero. Replace missing values with the mean number of bedrooms, rounded to the nearest integer.
house_type	Ordinal. One of "Terraced", "Semi-detached", or "Detached". Replace missing values with the most common house type.
area	Continuous. The area of the house in square meters, rounded to one decimal place. Replace missing values with the mean, to one decimal place.
```
