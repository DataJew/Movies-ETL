# Movies ETL
## Background
Amazing Prime loves the dataset and wants to keep it updated on a daily basis. Britta needs your help to create an automated pipeline that takes in new data, performs the appropriate transformations, and loads the data into existing tables. You’ll need to refactor the code from this module to create one function that takes in the three files—Wikipedia data, Kaggle metadata, and the MovieLens rating data—and performs the ETL process by adding the data to a PostgreSQL database.

## Overview of Project
> Wikipedia has a ton of information about movies, including budgets and box office returns, cast and crew, production and distribution, and so much more. Luckily, one of Britta's coworkers created a script to go through a list of movies on Wikipedia from 1990 to 2018 and extract the data from the sidebar into a JSON. Unfortunately, her coworker can't find the script anymore and just has the JSON file. We'll need to load in the JSON file into a Pandas DataFrame.

## Project Deliverables

1. ***Deliverable 1***: Write an ETL Function to Read Three Data Files
2. ***Deliverable 2***: Extract and Transform the Wikipedia Data
3. ***Deliverable 3***: Extract and Transform the Kaggle Data
4. ***Deliverable 4***: Create the Movie Database

## Deliverable 1:  Write an ETL Function to Read Three Data Files
### Deliverable Requirements:
Using your knowledge of Python, Pandas, the ETL process, and code refactoring, write a function that reads in the three data files and creates three separate DataFrames.

1. An ETL function is written to read in the three data files. 
2. The function converts the Wikipedia JSON file to a Pandas DataFrame, and the DataFrame is displayed in the `ETL_function_test.ipynb file`.
3. The function converts the Kaggle metadata file to a Pandas DataFrame, and the DataFrame is displayed in the `ETL_function_test.ipynb file`.
4. The function converts the MovieLens ratings data file to a Pandas DataFrame, and the DataFrame is displayed in the `ETL_function_test.ipynb` file.

![name-of-you-image](https://github.com/DataJew/Movies-ETL/blob/main/Resources/images/Deliverable%201/wiki_movies_df.png)

![name-of-you-image](https://github.com/DataJew/Movies-ETL/blob/main/Resources/images/Deliverable%201/kaggle_metadata.png)

![name-of-you-image](https://github.com/DataJew/Movies-ETL/blob/main/Resources/images/Deliverable%201/ratings_df.png)


## Deliverable 2: Extract and Transform the Wikipedia Data
### Deliverable Requirements:
Using your knowledge of Python, Pandas, the ETL process, and code refactoring, extract and transform the Wikipedia data so you can merge it with the Kaggle metadata. While extracting the IMDb IDs using a regular expression string and dropping duplicates, use a `try-except` block to catch errors.

1. The TV shows are filtered out, and the `wiki_movies_df` DataFrame is created.
2. A `try-except` block is used to catch errors while extracting the IMDb IDs with a regular expression and dropping duplicate IDs.
3. The extraction and transformation of the Wikipedia data in the ETL function does the following:
    1. A list comprehension is used to keep columns with non-null values.
    2. The non-null box office data is converted to string values using the lambda and join functions.
    3. A regular expression is used to match the six elements of "form_one" of the box office data.
    4. A regular expression is used to match the three elements of "form_two" of the box office data.
    5. The following columns are cleaned in the Wikipedia DataFrame:
        1. The box office column
        2. The budget column
        3. The release date column
        4. The running time column​
4. The cleaned Wikipedia data is converted to a Pandas DataFrame, and the DataFrame is displayed in the `ETL_clean_wiki_movies.ipynb` file.

![name-of-you-image](https://github.com/DataJew/Movies-ETL/blob/main/Resources/images/Deliverable%202/wiki_movies_df.png)

![name-of-you-image](https://github.com/DataJew/Movies-ETL/blob/main/Resources/images/Deliverable%202/wiki_movies_df_columns.png)


## Deliverable 3: Extract and Transform the Kaggle Data
### Deliverable Requirements:
Using your knowledge of Python, Pandas, the ETL process, and code refactoring, extract and transform the Kaggle metadata and MovieLens rating data, then convert the transformed data into separate DataFrames. Then, you’ll merge the Kaggle metadata DataFrame with the Wikipedia movies DataFrame to create the `movies_df` DataFrame. Finally, you’ll merge the MovieLens rating data DataFrame with the `movies_df` DataFrame to create the `movies_with_ratings_df`.

1. The extraction and transformation of the Kaggle metadata using the ETL function does the following:
    1. The Kaggle metadata is cleaned.
    2. The Wikipedia and Kaggle DataFrames are merged.
    3. The following is performed on the merged Wikipedia and Kaggle DataFrames to create the `movies_df`:
        1. Unnecessary columns are dropped.
        2. A function is used to fill in the missing Kaggle data.
        3. The `movies_df` DataFrame is filtered to keep specific columns.
        4. The `movies_df` DataFrame columns are renamed.
2. The extraction and transformation of the MovieLens ratings data using the ETL function does the following:
    1. The ratings counts are cleaned.
    2. The `movies_df` DataFrame is merged with the cleaned ratings DataFrame to create the `movies_with_ratings_df` DataFrame.
    3. The empty values in the `movies_with_ratings_df` DataFrame are filled with “0”.
3. The `movies_with_ratings_df` and the `movies_df DataFrames` are displayed in the `ETL_clean_kaggle_data.ipynb` file.

![name-of-you-image](https://github.com/DataJew/Movies-ETL/blob/main/Resources/images/Deliverable%203/movies_df.png)

![name-of-you-image](https://github.com/DataJew/Movies-ETL/blob/main/Resources/images/Deliverable%203/movies_with_ratings_df.png)


## Deliverable 4: Create the Movie Database
### Deliverable Requirements:
Use your knowledge of Python, Pandas, the ETL process, code refactoring, and PostgreSQL to add the `movies_df` DataFrame and MovieLens rating CSV data to a SQL database.

1. The data from the `movies_df` DataFrame replaces the current data in the movies table in the SQL database, as determined by the `movies_query.png`.
2. The data from the MovieLens rating CSV file is added to the `ratings` table in the SQL database, as determined by the `ratings_query.png`.
3. The elapsed time to add the data to the database is displayed in the `ETL_create_database.ipynb` file.

![name-of-you-image](https://github.com/DataJew/Movies-ETL/blob/main/Resources/images/movies_query.PNG)

![name-of-you-image](https://github.com/DataJew/Movies-ETL/blob/main/Resources/images/rating_query.PNG)

![name-of-you-image](https://github.com/DataJew/Movies-ETL/blob/main/Resources/images/rating_query2.PNG)
