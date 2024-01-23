# NoSQL Challenge: Eat Safe, Love Database Analysis

## Overview

This project involves evaluating the hygiene ratings data provided by the UK Food Standards Agency for various establishments across the United Kingdom. The goal is to assist the editors of food magazine, "Eat Safe, Love," in analyzing the ratings data to help their journalists and food critics decide where to focus future articles.

## Files

- `NoSQL_setup_starter.ipynb`: Jupyter Notebook for setting up the database and performing initial operations.
- `NoSQL_analysis_starter.ipynb`: Jupyter Notebook for exploratory analysis and answering specific questions.


## Part 1: Database and Jupyter Notebook Set Up 

1. **Imported Data:** Used the `mongoimport` command to import data from the `establishments.json` file in terminal.
   - `mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json`
2. **Created Database and Identified Collection:** Created the database `uk_food` using `mongosh` and `MongoDB` and identified the collection `establishments`.
3. **Imported Libraries and Created Client:** Imported PyMongo and Pretty Print (`pprint`) libraries. Created an instance of the Mongo Client.
4. **Confirmed Setup:** Listed databases and collections in MongoDB to confirm setup. Used `find_one()` and `pprint` to display one document.
5. **Assigned Variable:** Assigned the `establishments` collection to a variable to prepare collection for use.

## Part 2: Database Update

1. **Inserted New Data:** Inserted data for the new restaurant, "Penang Flavours," into the `establishments` collection.
2. **Queried BusinessTypeID:** Performed a query to find the `BusinessTypeID` for "Restaurant/Cafe/Canteen" and returned specific fields.
3. **Updated Document:** Updated the "Penang Flavours" document with the correct `BusinessTypeID`.
4. **Deleted Documents:** Checked and removed documents with "Dover Local Authority" from the database. Verified using `count_documents()`.
5. **Converted Data Types:** Used `update_many()` to convert latitude and longitude fields from strings to decimals and `RatingValue` to integers.

## Part 3: Exploratory Analysis

`count_documents` function used to display number of documents and `pprint` used to display first result for each question. Results were then coverted to 
Pandas DataFrames for analysis. Outputs used to answer following questions:

### Question 1: 
Which establishments have a hygiene score equal to 20?
- There are 41 establishments that have a hygiene score equal to 20.
- Refer to `hygiene_df` for detailed list of all establishments.
- Examples of some include 'The Chase Rest Home', 'Brenalwood' and 'Melrose Hotel'. 

### Question 2: 
Which establishments in London have a RatingValue greater than or equal to 4?
- There are 33 establishments that have a RatingValue greater than or equal to 4.
- Refer to `ratingvalue_df` for detailed list of all establishments.
- Examples of some include 'Charlie's', 'Mv City Cruises Erasmus' and 'Benfleet Motor Yacht Club'.

### Question 3: 
What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?
- In descending order: 'Iceland', 'Howe and Co Fish and Chips - Van 17', 'Volunteer', 'Plumstead Manor Nursery', & 'Atlantic Fish Bar'.
- There are 87 establishments in total.
- Refer to `best_df` for details of top 5 establishments.

### Question 4: 
How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.
- Refer to `pipeline_df` for complete establishment counts in each area.
- There are 55 different Local Authority areas.
- Top 10 results printed from pipeline:

<div style="text-align: center;">
  <table border="1" class="dataframe">
    <thead>
      <tr style="text-align: right;">
        <th></th>
        <th>_id</th>
        <th>count</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <th>0</th>
        <td>Thanet</td>
        <td>1130</td>
      </tr>
      <tr>
        <th>1</th>
        <td>Greenwich</td>
        <td>882</td>
      </tr>
      <tr>
        <th>2</th>
        <td>Maidstone</td>
        <td>713</td>
      </tr>
      <tr>
        <th>3</th>
        <td>Newham</td>
        <td>711</td>
      </tr>
      <tr>
        <th>4</th>
        <td>Swale</td>
        <td>686</td>
      </tr>
      <tr>
        <th>5</th>
        <td>Chelmsford</td>
        <td>680</td>
      </tr>
      <tr>
        <th>6</th>
        <td>Medway</td>
        <td>672</td>
      </tr>
      <tr>
        <th>7</th>
        <td>Bexley</td>
        <td>607</td>
      </tr>
      <tr>
        <th>8</th>
        <td>Southend-On-Sea</td>
        <td>586</td>
      </tr>
      <tr>
        <th>9</th>
        <td>Tendring</td>
        <td>542</td>
      </tr>
    </tbody>
  </table>
</div>

