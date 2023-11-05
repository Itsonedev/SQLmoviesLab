# SQLmoviesLab
### Create a database and Movies Table
> mysql> create database movie_lab;
>
> mysql> use movie_lab;
>
> mysql> CREATE table movies(
>
>> Title VARCHAR(35) NOT NULL DEFAULT '',
>>
>> Runtime INT UNSIGNED NOT NULL DEFAULT 0,
>> 
>> Genre VARCHAR(20) NOT NULL DEFAULT '',
>> 
>> IMDB_Score DECIMAL(3,1) NOT NULL DEFAULT 00.0,
>> 
>> Rating CHAR(5) NOT NULL DEFAULT '',
>> 
>> PRIMARY KEY (Title)
>>
>> );
>
> mysql> insert into movies values
> 
>> ('Howard the Duck', 110, 'Sci-fi', 4.6, 'PG'),
>>
>> ('Lavalantula', 83, 'Horror', 4.7, 'TV-14'),
>> 
>> ('Starship Troopers', 129, 'Sci-fi', 7.2, 'PG-13'),
>> 
>> ('Waltz With Bashir', 90, 'Documentary', 8.0, 'R'),
>> 
>> ('Spaceballs', 96, 'Comedy', 7.1, 'PG'),
>> 
>> ('Monsters Inc.', 92, 'Animation', 8.1, 'G');
>
> ### Add two more movies of your choosing
>
> mysql> insert into movies values
>
>> ('Training Day', 122, 'Thriller', 7.7, 'R'),
>> 
>> ('Constantine', 12, 'Drama', 7.0, 'R');
>
> ### Query to find all movies in the Sci-fi Genre
>
> mysql> select * from movies WHERE Genre = 'Sci-fi';
>
> ### Query to find all movies with at least a 6.6 on IMDB
>
> mysql> select * from movies WHERE IMDB_Score > 6.5;
>
> ### Query for movies that Runtime < 100 & Rating either PG or G
>
> mysql> select * from movies WHERE Runtime < 100 AND Rating IN('PG','G');
>
> ### Query for AVG Runtime of movies < 7.5 on IMDB Grouped by Genre
>
> mysql> select Genre, AVG(Runtime) AS Avg_Runtime FROM movies WHERE IMDB_Score < 7.5 GROUP BY Genre;
>
> ### Query to find Starship Troopers by its Title and change Rating to R
>
> mysql> UPDATE movies SET Rating = 'R' WHERE Title = 'Starship Troopers';
>
> ### Query to show Title and Rating for all Horror & Documentaries
>
> mysql> select Title, Rating FROM movies WHERE Genre IN ('Horror','Documentary');
>
> ### Average, Min & Max IMDB Score grouped by Rating
>
> mysql> select Rating, AVG(IMDB_Score) AS Avg_Score, MAX(IMDB_Score) AS Max_Score, MIN(IMDB_Score) AS Min_Score FROM movies GROUP BY Rating;
>
> ### Edit previous query so that it shows only Ratings with multiple movies
>
> mysql> select Rating, AVG(IMDB_Score) AS Avg_Score, MAX(IMDB_Score) AS Max_Score, MIN(IMDB_Score) AS Min_Score FROM movies GROUP BY Rating HAVING COUNT(*) > 1;
>
> ### Delete all movies of Rating R
>
>  DELETE FROM movies WHERE Rating = 'R';
>
> ### Delete the movies table then delete the database
>
> mysql> DROP TABLE movies;
>
> mysql> DROP DATABASE movie_lab;
