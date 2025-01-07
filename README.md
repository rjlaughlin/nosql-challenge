# NoSQL Challenge: UK Food Establishments Analysis

## Overview

This project involves analyzing the food hygiene ratings data from the UK Food Standards Agency to assist the editors of the food magazine *Eat Safe, Love* in identifying establishments for future articles. Using MongoDB for data storage and querying, this project aims to provide insights into the data through exploratory analysis and database manipulation.

## Project Structure

This project is divided into three main parts:

### Part 1: Database and Jupyter Notebook Setup

In this section, the setup for the database is performed. The establishments data from a JSON file is imported into a MongoDB database, and the connection to the database is verified.

#### Key Tasks:
- **Data Import**: Import the `establishments.json` file into a MongoDB database named `uk_food` with a collection named `establishments`.
- **MongoDB Connection**: Use PyMongo to connect to MongoDB and verify the database setup by:
  - Listing available databases.
  - Displaying a sample document from the collection using `find_one`.
- **Preparation for Analysis**: Assign the `establishments` collection to a variable for further use.

### Part 2: Update the Database

In this section, database updates are performed based on specific requirements from the magazine editors.

#### Key Tasks:
1. **Add a New Restaurant**: Insert the a new restaurant named *Penang Flavours* to the establishements collection:
2. **Update Restaurant Details**:
   - Retrieve the `BusinessTypeID` for "Restaurant/Cafe/Canteen" and update the new restaurant entry.
3. **Remove Documents for Dover**:
   - Identify and delete all establishments with the `LocalAuthorityName` as "Dover".
   - Verify the deletion by counting the remaining documents.
4. **Data Type Adjustments**:
   - Convert `latitude`, `longitude`, and `RatingValue` fields from strings to appropriate numeric types using `update_many`.

### Part 3: Exploratory Analysis

This section answers specific queries to assist the magazine editors in their analysis.

#### Key Tasks:
1. **Hygiene Score of 20**:
   - Identify establishments with a `Hygiene` score of 20.
   - Display the count, a sample document, and the first 10 rows of the results in a DataFrame.
2. **London Establishments with High Ratings**:
   - Query establishments in London with a `RatingValue` of 4 or higher using `$regex`.
   - Display the count, a sample document, and the first 10 rows of the results in a DataFrame.
3. **Top Establishments near "Penang Flavours"**:
   - Find the top 5 establishments with a `RatingValue` of 5, sorted by the lowest `Hygiene` score, within a 0.01-degree proximity of "Penang Flavours".
   - Display the results in a DataFrame.
4. **Hygiene Score of 0 by Local Authority**:
   - Use an aggregation pipeline to find the count of establishments with a `Hygiene` score of 0, grouped by `LocalAuthorityName`.
   - Sort the results from highest to lowest and display the top 10 in a DataFrame.

## Files

- **NoSQL_setup.ipynb**: Jupyter Notebook for database setup and updates.
- **NoSQL_analysis.ipynb**: Jupyter Notebook for exploratory analysis.
- **establishments.json**: JSON file containing the dataset.

## Setup and Dependencies

Before starting, ensure you have the following installed:

- MongoDB
- Python Libraries:
```python
    from pymongo import MongoClient
    from pprint import pprint
    import pandas as pd
```

## Running the Analysis
- Clone the repository and navigate to the project directory.
- Install dependencies as shown above.
- Run the Jupyter Notebooks to generate the analyses.