# FINAL PROJECT

## POPULAR SONGS 

### SELECTED TOPIC

Throughout the class we have aquired tools and learned skills that I will be exploiting to achieve a goal that will soothe the mind, this insipred me to choose a topic about music as it is a pleasant sound which combines melodies and harmony to soothe the soul, just like coding is for the mind, This topic is about analyzing popular songs in order to build a prediction tool to determine if a track will be popular or not. I will use Python, Flask, Tableau, pgAdmin and other useful tools to achieve the goal of creating an application that will allow the user to input characteristics of a song to predict if this the song will be popular or not.

### WHY THIS TOPIC?

I strongly believe that I'm not talking just for myself when I say music is one of the greatest things in life, The great German philosopher
Friedrich Nietzsche once wrote:
>"Without music, life would be a mistake.".

I chose this topic because it fuses my two passions, coding and music.

### SOURCE DATA

in order to build our predictive tool, we first needed the data to analyze and manipulate accordingly, Kaggle is a subsidiary of Google LLC that provides among other interesting things a public data platform, numerous variaties of datasets are available on the website and ready to be downloaded and used, So I turned to it to find useful data and found it [here](https://www.kaggle.com/datasets/zaheenhamidani/ultimate-spotify-tracks-db).\
A .csv file named under the name SpotifyFeatures which contains more than 232,000 songs, approximately 10,000 tracks per genre and a totality of 26 genres as mentioned in Kaggle. A further Python coding was made to better understand the dataset, The jupyter notebook is provided in this repository in the "Jupyter Notebooks" directory under the name: first_analyse.ipynb.\
The raw dataset has 18 columns:
- **genre :** a string specifying the genre of the track (e.g. Movie, R&B...).
- **artiste_name :** a string mentioning the artist that made the track.
- **track_name :** a string specifying the track's name.
- **track_id :** a string mentioning the Spotify ID for the track.
- **popularity :** an int measure ranging between 0 and 100 mentioning the popularity of the track.
- **acousticness :** a float which is a confidence measure from 0.0 to 1.0 of whether the track is acoustic. 1.0 represents high confidence the track is acoustic.
- **danceability :** a float that describes how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity. A value of 0.0 is least danceable and 1.0 is most danceable.
- **duration_ms :** an int determining the duration of the track in milliseconds.\
the rest of the columns are: **energy**, **instrumentalness**, **key**, **liveness**, **loudness**, **mode**, **speechiness**, **tempo**, **time_signature**, **valence** 

### QUESTIONS TO BE ANSWERED

- What makes a track popular?
- How can we make a track that will be popular?


### DATA PEPARATION

We used `pandas` python library to load our csv file into a dataframe, we then proceedeed into cleaning the **genre** column, we then check if the dataframe had any null values. After this we created a new binary column for popularity 0 for unpopular songs and 1 for popular songs, we used the existing **popularity** column with a threshold of 50 to binarize the new column. We then dropped the columns that we first found to be ineffective in determining the popularity of a song such as the name of the track or the artist's name. The **time_signature** column was dropped as well as most of the tracks had the same time_signature.
Later we custom encoded the **genre** column and One hot encoded the columns **key** and **mode**.

### DATA TO DATABASE

in order to convert our dataframes to SQL tables using SQLAlchemy, the database was names **Spotify_data** with three tables **songs** and **info** and **encoded**.

here's the ERD:

![erd](/assets/ERD.png)



### MACHINE LEARNING

I used the sklearn library and split the DataFrame extracted from the table encoded into testing part and training part in order to predict the popularity of a track, we scaled the data using **StandardScaler**, using **RandomForestClassifier** and got the following results:

![classification_report](/assets/classification_report_first.PNG)

In this report, the classifier has a precision of 0.95 for class 0 and 0.96 for class 1, a recall of 0.96 for class 0 and 0.95 for class 1, and an f1-score of 0.95 for class 0 and 0.96 for class 1.

Overall, the classifier performs very well, with an accuracy of 0.96 and good precision, recall, and f1-scores for both classes.


### Dashboard

#### blueprint for Google Slides Storyboard

the storyboard will be available [here](https://docs.google.com/presentation/d/e/2PACX-1vTqpsljA7XP9a0TlY1wD8qDnQqbDBlbLfxc7TLcXYecThPYyc6-D-P79wV7d_4hK5GuJRINQpm6rq0G/pub?start=true&loop=true&delayms=3000)
