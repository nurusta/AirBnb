# AirBnb



Istanbul Airbnb Data Analysis With Machine Learning Algorithms 



















CSE 585 Term Project










By Emine Nur Usta

Table Of Contents

1.Introduction
2.Data
3.Implementation
	3.1 Data Analyzing
	3.2 Machine Learning Methods
4.Conclusion
5.References





















1.Introduction
This project uses Airbnb data from Istanbul.

What is Airbnb?
Airbnb, Inc. is an American firm that runs an online marketplace for housing and tourism activities, primarily homestays for vacation rentals.


Why Airbnb?
Airbnb has evolved into a one-of-a-kind service that is used and recognized all over the world. The company's data analysis of millions of listings offered by Airbnb is a critical aspect. These millions of listings provide a tremendous amount of data, which may be studied.

In this project, I examined the Airbnb data, I asked some questions and tried to answer them. I will talk about them in the Implementation part of the paper.



2.Data

The dataset is obtained from Kaggle.  This dataset contains 16251 rows and 16 columns. Column names and types are given below.
id                                  int64
name                               object
host_id                             int64
host_name                          object
neighbourhood_group               float64
neighbourhood                      object
latitude                          float64
longitude                         float64
room_type                          object
price                               int64
minimum_nights                      int64
number_of_reviews                   int64
last_review                        object
reviews_per_month                 float64
calculated_host_listings_count      int64
availability_365                    int64
dtype: object
Some of the rows have missing values, so these rows are handled or cleaned. There is no available data in column["neighbourhood_group"], so I dropped this column.

I also obtained the Average Price of Neighborhoods.


3.Implementation
For this project, I used a jupyter notebook IDE with a python programming language to write the script. 

3.1 Data Analyzing
I made necessary changes on data before applying machine learning algorithms.I found missing values in the data.


A total of five columns have missing values:
'name' since i will not do text based analysis of the rental names, this column won't add too much to my analysis. Decision: DROP
'host_name' Here again, this column contains personal information and doesn't add much to my analysis. Decision: DROP 
'neighbourhood_group': it has no data Decision: DROP 
'last_review' Since these are all dates, a missing value most likely means that there has been no review for this rental. I won't be using this for any analysis or visualization. Decision: DROP 
'reviews_per_month' We might be able to do some analysis with this. This is the kind of situation where one's intuition supplements the analysis. In this column, missing values most likely do not mean that the data points were not recorded but that they don't exist, a contrast I've learned to appreciate when dealing with missing values. Decision: REPLACE missing values with 0's

Then I analyzed the data. The Room Type Columns have 3 different values.

Private room
Guests have exclusive access to the bedroom/sleeping area of the listing. Other parts such as the living room, kitchen, and bathroom are likely open either to the host or even to other guests.
Entire home/apt
Guests have the whole place for themselves. It usually includes a bedroom, bathroom, and kitchen.
Shared Room
Guests sleep in a bedroom or a common area that could be shared with others.
Hotel Room
A typical hotel room with its facilities. Since 2018, Airbnb allows some boutique hotels and high rated independent hotels to list their rooms on their site.


The Neighbourhood Column has 38 different values.

'Uskudar', 'Besiktas', 'Beyoglu', 'Sisli', 'Sariyer', 'Beykoz',
       'Atasehir', 'Fatih', 'Adalar', 'Kadikoy', 'Kagithane', 'Maltepe',
       'Bakirkoy', 'Esenyurt', 'Basaksehir', 'Kartal', 'Gaziosmanpasa',
       'Bahcelievler', 'Bagcilar', 'Buyukcekmece', 'Silivri',
       'Beylikduzu', 'Umraniye', 'Sile', 'Cekmekoy', 'Sancaktepe',
       'Tuzla', 'Pendik', 'Sultangazi', 'Eyup', 'Zeytinburnu',
       'Kucukcekmece', 'Avcilar', 'Gungoren', 'Catalca', 'Bayrampasa',
       'Esenler', 'Sultanbeyli', 'Arnavutkoy'

3.2 Machine Learning Methods
I used sklearn, pandas, and numpy libraries in this project. I splitted same data to train and test. 

My first question was; Can I predict the price using the other columns as a feature? My motivation here was How does neighborhood affect pricing?

Since the Neighbourhood and Room Types columns have string values, I used label encoding to add them to the prediction. I used Linear Regression to predict the price, the R Square was obtained 0,01 which is very low. So I can answer my question as I cannot predict the price using all other columns. I changed the features column, dropped some variables but the R Square did not change in a better way.

Second question was; Can I predict the room type using the other columns as a feature?

This time I used Logistic Regression, Since I used this algorithm, I don't need to do labeling.
Logistic Regression can predict categorical data. So the Accuracy of the model was 0.59.

Then I thought Can I classify these features?

I used the Decision Tree Classifier to classify neighborhoods, and the Accuracy of the model was 0,98. That means the model can classify neighbourhood %98 correctly.

Then I predicted the availability with Linear Regression, R Square was 0,03. Also I tried Logistic Regression and got 0.28 accuracy. I used the same model to predict the neighbourhood and  got 0.26 accuracy.


4.Conclusion
My motivation was to find out  if the neighborhood affects pricing? Or what features affect prcing. So I applied Regression algorithms to predict prices. And I saw that the neighborhood does not affect pricing. I found out room type can be predictable.

5.References

J. Dhillon et al., "Analysis of Airbnb Prices using Machine Learning Techniques," 2021 IEEE 11th Annual Computing and Communication Workshop and Conference (CCWC), 2021, pp. 0297-0303, doi: 10.1109/CCWC51732.2021.9376144.

Rezazadeh, Pouya & Nikolenko, Liubov & Rezaei, Hoormazd. (2019). Airbnb Price Prediction Using Machine Learning and Sentiment Analysis. 
