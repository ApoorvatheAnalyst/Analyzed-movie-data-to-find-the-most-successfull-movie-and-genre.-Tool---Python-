# Analyzed-movie-data-to-find-the-most-successfull-movie-and-genre.-Tool---Python-
# The data is analysed by slicing the data,handling outliers, missing value treatment and performing EDA (exploratory data analysis), ETL # (Extract, Transform, and Load) and Data Visualization on the data.
-----------------------------Capstone Project - Python-----------------------------------------
# Importing the libraries
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import statistics as st
import seaborn as sns
Task-1
Load the movie dataset in python notebook. Display the number of rows and columns in the data set. Display the titles and genres of the first 50 movies.
df = pd.read_csv("C:/Users/Win-10/DS1_C8_V3_ND_Sprint2_Data Analysis Using Python_Dataset.csv") #reading the file
df
budget	genres	homepage	id	keywords	original_language	original_title	overview	popularity	production_companies	production_countries	release_date	revenue	runtime	spoken_languages	status	tagline	title	vote_average	vote_count
0	237000000	[{"id": 28, "name": "Action"}, {"id": 12, "nam...	http://www.avatarmovie.com/	19995	[{"id": 1463, "name": "culture clash"}, {"id":...	en	Avatar	In the 22nd century, a paraplegic Marine is di...	150.437577	[{"name": "Ingenious Film Partners", "id": 289...	[{"iso_3166_1": "US", "name": "United States o...	10-12-2009	2787965087	162.0	[{"iso_639_1": "en", "name": "English"}, {"iso...	Released	Enter the World of Pandora.	Avatar	7.2	11800
1	300000000	[{"id": 12, "name": "Adventure"}, {"id": 14, "...	http://disney.go.com/disneypictures/pirates/	285	[{"id": 270, "name": "ocean"}, {"id": 726, "na...	en	Pirates of the Caribbean: At World's End	Captain Barbossa, long believed to be dead, ha...	139.082615	[{"name": "Walt Disney Pictures", "id": 2}, {"...	[{"iso_3166_1": "US", "name": "United States o...	19-05-2007	961000000	169.0	[{"iso_639_1": "en", "name": "English"}]	Released	At the end of the world, the adventure begins.	Pirates of the Caribbean: At World's End	6.9	4500
2	245000000	[{"id": 28, "name": "Action"}, {"id": 12, "nam...	http://www.sonypictures.com/movies/spectre/	206647	[{"id": 470, "name": "spy"}, {"id": 818, "name...	en	Spectre	A cryptic message from Bond’s past sends him o...	107.376788	[{"name": "Columbia Pictures", "id": 5}, {"nam...	[{"iso_3166_1": "GB", "name": "United Kingdom"...	26-10-2015	880674609	148.0	[{"iso_639_1": "fr", "name": "Fran\u00e7ais"},...	Released	A Plan No One Escapes	Spectre	6.3	4466
3	250000000	[{"id": 28, "name": "Action"}, {"id": 80, "nam...	http://www.thedarkknightrises.com/	49026	[{"id": 849, "name": "dc comics"}, {"id": 853,...	en	The Dark Knight Rises	Following the death of District Attorney Harve...	112.312950	[{"name": "Legendary Pictures", "id": 923}, {"...	[{"iso_3166_1": "US", "name": "United States o...	16-07-2012	1084939099	165.0	[{"iso_639_1": "en", "name": "English"}]	Released	The Legend Ends	The Dark Knight Rises	7.6	9106
4	260000000	[{"id": 28, "name": "Action"}, {"id": 12, "nam...	http://movies.disney.com/john-carter	49529	[{"id": 818, "name": "based on novel"}, {"id":...	en	John Carter	John Carter is a war-weary, former military ca...	43.926995	[{"name": "Walt Disney Pictures", "id": 2}]	[{"iso_3166_1": "US", "name": "United States o...	07-03-2012	284139100	132.0	[{"iso_639_1": "en", "name": "English"}]	Released	Lost in our world, found in another.	John Carter	6.1	2124
...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...	...
4798	220000	[{"id": 28, "name": "Action"}, {"id": 80, "nam...	NaN	9367	[{"id": 5616, "name": "united states\u2013mexi...	es	El Mariachi	El Mariachi just wants to play his guitar and ...	14.269792	[{"name": "Columbia Pictures", "id": 5}]	[{"iso_3166_1": "MX", "name": "Mexico"}, {"iso...	04-09-1992	2040920	81.0	[{"iso_639_1": "es", "name": "Espa\u00f1ol"}]	Released	He didn't come looking for trouble, but troubl...	El Mariachi	6.6	238
4799	9000	[{"id": 35, "name": "Comedy"}, {"id": 10749, "...	NaN	72766	[]	en	Newlyweds	A newlywed couple's honeymoon is upended by th...	0.642552	[]	[]	26-12-2011	0	85.0	[]	Released	A newlywed couple's honeymoon is upended by th...	Newlyweds	5.9	5
4800	0	[{"id": 35, "name": "Comedy"}, {"id": 18, "nam...	http://www.hallmarkchannel.com/signedsealeddel...	231617	[{"id": 248, "name": "date"}, {"id": 699, "nam...	en	Signed, Sealed, Delivered	"Signed, Sealed, Delivered" introduces a dedic...	1.444476	[{"name": "Front Street Pictures", "id": 3958}...	[{"iso_3166_1": "US", "name": "United States o...	13-10-2013	0	120.0	[{"iso_639_1": "en", "name": "English"}]	Released	NaN	Signed, Sealed, Delivered	7.0	6
4801	0	[]	http://shanghaicalling.com/	126186	[]	en	Shanghai Calling	When ambitious New York attorney Sam is sent t...	0.857008	[]	[{"iso_3166_1": "US", "name": "United States o...	03-05-2012	0	98.0	[{"iso_639_1": "en", "name": "English"}]	Released	A New Yorker in Shanghai	Shanghai Calling	5.7	7
4802	0	[{"id": 99, "name": "Documentary"}]	NaN	25975	[{"id": 1523, "name": "obsession"}, {"id": 224...	en	My Date with Drew	Ever since the second grade when he first saw ...	1.929883	[{"name": "rusty bear entertainment", "id": 87...	[{"iso_3166_1": "US", "name": "United States o...	05-08-2005	0	90.0	[{"iso_639_1": "en", "name": "English"}]	Released	NaN	My Date with Drew	6.3	16
4803 rows × 20 columns

df.shape #displaying the number of rows and colums in the dataset
titles = df['title'].head(50)
genres = df['genres'].head(50)
print("first 50 titles are \n ",titles)
print("first 50 genres are \n ",genres)
TASK-2
Identify the null values and perfgorm the null value treatment. (Choose the imputration method based on the type o f data in the in the columns of interest)
df.info() # checking the details of the data.
df.isnull().sum() #checking the total number of null values in the data
Here we can see the data have null values in 5 column. So, we will perform data imputation based on the type of data in the columns.
We can see in the data that 3 columns have a small number of missing values so we can delete the rows from the data and for the other 2since they are categorical we will impute the data wil mode.
df_1 = df.dropna(how = 'any', subset = ['overview', 'release_date', 'runtime']) #deleting the rows of 3 columns
df_1.shape
df_1.isnull().sum()
df_1['homepage'] = df_1['homepage'].fillna(df_1['homepage'].mode()[0]) #filling the missing values in the columns with mode
df_1['tagline'] = df_1['tagline'].fillna(df_1['tagline'].mode()[0]) #filling the missing values in the columns with mode
import warnings
warnings.filterwarnings("ignore")   #to ignore warnings
df_1.isnull().sum() #total of missing values
We can see there are no missing values in the data df_1 now
TASK-3
Display the movie categories which have a budget greater than $220,000
df_1[(df_1.budget) > 220000] # filtering the data where budget is greater than $220,000
TASK-4
Display the movie categories which have a budget greater than $961,000,000
df_1[(df_1.budget) > 961000000]  # filtering the data where budget is greater than $961,000,000
TASK-5
In the data set there are some movies for which the budget and revenue columns have the value 0, which means unknown values. Remove the rows with the values 0 for both the columns
df_1.drop(df_1.loc[df_1['budget']==0].index, inplace=True) #dropping the rows with values 0 in budget column
df_1.drop(df_1.loc[df_1['revenue']==0].index, inplace=True) #dropping the rows with values 0 in revenue column
df_1.shape
TASK-6
List the Top 10 movies with highest revenue and top 10 movies with least budget
df_1.sort_values('revenue').head(10) # top 10 movies with highest revenue
df_1.sort_values('budget').tail(10) # top 10 movies with least budget
TASK-7
How are popularity of movies related with the movie budget. Are they related or totally unrelated to each other?
relation = df_1['popularity'].corr(df_1['budget']) 
print("The correlation between popularity iand budget is",relation)
sns.lmplot(x="popularity", y="budget", data=df_1)
plt.title("Correration")
plt.show()
plt.scatter(df_1['budget'], df_1['popularity'])  
Here we can see the realtion coeffient is +ve so as the budget increases the popularity is also increased.
TASK-8
Identify and display the names of all production companies along with number of times they appear in the datasets
df_1.production_companies.value_counts()
Here we can see Paramount Pictures occures 48 times, Universal Pictures occurs 35 times, New Line Cinema occurs 29 times, Columbia Pictures occurs 28 times and others occurs only 1 time in the dataset
TASK-9
Display the names of the top 25 production companies based on the number of the movies they have produced in decreasing order of the number of the number of movies produced
df_2=df_1
df_2['count'] = df_2.groupby('production_companies')['id'].transform('count') # adding a column in the data 'count' will the count of number of movies of each production 
df_2
df_2.sort_values('count', ascending=False).head(25) #displaying the top 25 most count of production
TASK-10
Sort the data in descending order based on revenue and filter the top 500 movies. Find the measure of central tendencies for the columns --- budget, revenue and runtime .
Perfom outlier analysis for all 3 columns
df_1.sort_values('revenue', ascending=False).head(500) #sorting data in descending order based on revenue and filtering the top 500 movies
# creating a function to fide mean , median and mode of the columns
​
def central(col):
    mean = st.mean(col)
    median = st.median(col)
    mode = st.mode(col)
    print("the mean is",mean)
    print("the median is",median)
    print("the mode is",mode)
central(df_1.revenue) #central tendencies of revenue
central(df_1.budget) #central tendencies of budget
central(df_1.runtime) #central tendencies of runtime
# creating a user defined function to find the outliers in the data
​
def outliers(column):
    q1=column.quantile(0.25)
    q3=column.quantile(0.75)
    IQR=q3-q1
    upper_fence = q3+(1.5*IQR)
    lower_fence = q1-(1.5*IQR)
    outliers_lower = []
    outliers_upper = []
    
    for i in column:
        if i>upper_fence:
            outliers_upper.append(i)
        elif i< lower_fence:
            outliers_lower.append(i)
    print("Upper fence is",upper_fence)  
    print("Lower fence is",lower_fence)   
    print("Upper outliers are \n", outliers_upper)    
    print("Lower outliers are \n", outliers_lower)  
outliers(df_1['revenue']) #using the funtion to find outliers
# Outlier analysis for the column Revenue using boxplot
plt.figure(figsize=(15,7))
sns.boxplot(x=df_1["revenue"])
plt.title("Outliers of Revenue")
plt.show()
d=df_1[(df_1["revenue"]<-176938013.5)|(df_1["revenue"]>340230022.5)]
df_1=df_1.drop(d.index,axis=0,errors="ignore") #deleting the outliers
outliers(df_1['budget']) #using the funtion to find outliers
# Outlier analysis for the column budget using boxplot
plt.figure(figsize=(15,7))
sns.boxplot(x=df_1["budget"])
plt.title("Outliers of Budget")
plt.show()
d=df_1[(df_1["budget"]<-44000000.0)|(df_1["budget"]>100000000.0)]
df_1=df_1.drop(d.index,axis=0,errors="ignore") #deleting the outliers
outliers(df_1['runtime']) #using the funtion to find outliers
# Outlier analysis for the column runtime using boxplot
plt.figure(figsize=(15,7))
sns.boxplot(x=df_1["runtime"])
plt.title("Outliers of Runtime")
plt.show()
d=df_1[(df_1["runtime"]<60.0)|(df_1["runtime"]>156.0)]
df_1=df_1.drop(d.index,axis=0,errors="ignore") #deleting the outliers
df_3 = df_1
There are multiple outliers in the data of all 3 columns
TASK-11
Identify and display the name sof the movies along with their run times for those movies that have above average run time
df_3["runtime"].mean() #getting the mean of column runtime
df_4 = df_3[(df_1["runtime"]>107.42256075444324)] #creating a new dataframe with the runtime greater than mean
df_4
columns = df_4[['runtime', 'title']]
columns # printing the runtime and title of the data
df.iloc[:,1:2]
genres
0	[{"id": 28, "name": "Action"}, {"id": 12, "nam...
1	[{"id": 12, "name": "Adventure"}, {"id": 14, "...
2	[{"id": 28, "name": "Action"}, {"id": 12, "nam...
3	[{"id": 28, "name": "Action"}, {"id": 80, "nam...
4	[{"id": 28, "name": "Action"}, {"id": 12, "nam...
...	...
4798	[{"id": 28, "name": "Action"}, {"id": 80, "nam...
4799	[{"id": 35, "name": "Comedy"}, {"id": 10749, "...
4800	[{"id": 35, "name": "Comedy"}, {"id": 18, "nam...
4801	[]
4802	[{"id": 99, "name": "Documentary"}]
4803 rows × 1 columns

df.loc[0:5,['genres','budget']]
genres	budget
0	[{"id": 28, "name": "Action"}, {"id": 12, "nam...	237000000
1	[{"id": 12, "name": "Adventure"}, {"id": 14, "...	300000000
2	[{"id": 28, "name": "Action"}, {"id": 12, "nam...	245000000
3	[{"id": 28, "name": "Action"}, {"id": 80, "nam...	250000000
4	[{"id": 28, "name": "Action"}, {"id": 12, "nam...	260000000
5	[{"id": 14, "name": "Fantasy"}, {"id": 28, "na...	258000000
df.index()
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
~\AppData\Local\Temp/ipykernel_5816/1030647034.py in <module>
----> 1 df.index()

TypeError: 'RangeIndex' object is not callable

df['name']=df.(df['genres']).transform('name')
​
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
~\AppData\Local\Temp/ipykernel_5816/1106216894.py in <module>
----> 1 df['name']=df['genres'].transform('name')

~\anaconda3\lib\site-packages\pandas\core\series.py in transform(self, func, axis, *args, **kwargs)
   4240         # Validate axis argument
   4241         self._get_axis_number(axis)
-> 4242         result = SeriesApply(
   4243             self, func=func, convert_dtype=True, args=args, kwargs=kwargs
   4244         ).transform()

~\anaconda3\lib\site-packages\pandas\core\apply.py in transform(self)
    231             obj.index
    232         ):
--> 233             raise ValueError("Function did not transform")
    234 
    235         return result

ValueError: Function did not transform

df
