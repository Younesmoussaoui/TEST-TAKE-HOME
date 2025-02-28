# TEST-TAKE-HOME
README - MongoDB Data Engineer Take-Home Test Solution
# Overview
This document provides a comprehensive and professional explanation of the solution implemented for the MongoDB Data Engineer Take-Home Test. 

The objective is to assess the ability to import, clean, analyze, and manage data in MongoDB using a dataset containing user and transaction data with various issues. 
The dataset, sourced from users_transactions_with_issues.json, is processed to create separate users and transactions collections, cleaned according to the test requirements, and analyzed using MongoDB aggregation queries. 
The solution includes an automated script for data cleaning and optional MongoDB Atlas hosting.

# Project Structure
Database: DATA 
Collections:
users: Contains user data  (1000 documents).

transactions: Contains transaction data (initially 3000 documents, cleaned to 2392 valid transactions).

users & transactions: Contains the mixed raw data (1 document with users and transactions arrays) ( json file ) .

Tools Used:

MongoDB (mongosh for queries, mongoimport/mongoexport for data management).
MongoDB Compass (optional, for visualization and verification).

Data Source : 

The dataset is derived from users_transactions_with_issues.json, which includes:

Users: Fields include _id, first_name, last_name, email, gender, and phone, with issues such as malformed emails, invalid phone numbers, and numeric names.

Transactions: Fields include _id, user_id, amount, timestamp, and status, with issues such as negative or missing amounts, invalid timestamps, statuses, and user references.

The data was initially imported into a single collection users & transactions, then separated into users and transactions collections for processing.

# Steps Taken
# 1. Data Import and Separation ( PHASE 1 DANS "CODE TEST MONGODB" ) 

## Objective: Import the mixed data and separate it into users and transactions collections.

## Action:

Used the  script to separate the data from users & transactions into users and transactions 

# 2. Data Cleaning ( PHASE 2 DANS "CODE TEST MONGODB" ) 

## Objective: Fix data issues in users and transactions as specified in the test.

## Users Collection:

Malformed or Missing Emails ( PHASE 2 / ETAPE 1 dans "CODE TEST MONGODB" ) 

Invalid Phone Numbers (Not Algerian MSISDN Format: +213 followed by 9 digits) ( PHASE 2 / ETAPE 2 dans "CODE TEST MONGODB" )

Numeric first_name and last_name ( PHASE 2 / ETAPE 3 dans "CODE TEST MONGODB" )

## Transactions Collection:

Invalid or Missing Amounts (Negative, Zero, or Absent) ( PHASE 2 / ETAPE 4 dans "CODE TEST MONGODB" ) 

Missing Timestamps ( PHASE 2 / ETAPE 5 dans "CODE TEST MONGODB" ) 

Invalid Statuses ( PHASE 2 / ETAPE 6 dans "CODE TEST MONGODB" ) 

Invalid user_id References ( PHASE 2 / ETAPE 7 dans "CODE TEST MONGODB" ) 

# 3. Aggregation Queries ( PHASE 3 DANS "CODE TEST MONGODB" )

## Objective: Perform the specified aggregation tasks after cleaning.

## Aggregation Task 1: Total Amount Spent by Each User ( PHASE 3 / ETAPE 1 dans "CODE TEST MONGODB" ) 

Result: Returned 20 users with the highest total spent, e.g., u709 with total_spent: 2972.07 (Jason Singh), confirming successful aggregation of positive transaction amounts.

## Aggregation Task 2: Users with At Least 3 Transactions ( PHASE 3 / ETAPE 2 dans "CODE TEST MONGODB" ) 

Result: Returned 20 users with 3 or more transactions, e.g., u878 with transaction_count: 7 (Adam Lyons), verifying the count and user identification.

## Aggregation Task 3: Patterns in Transaction Status : ( PHASE 3 / ETAPE 3 dans "CODE TEST MONGODB" )

Result: Returned status patterns, e.g., unknown: 1681 transactions, avg_amount: 256.39, FAILED: 357 transactions, avg_amount: 250.43, confirming status normalization and analysis.

## Aggregation Task 4: Users Without Transactions ( PHASE 3 / ETAPE 4 dans "CODE TEST MONGODB" )

Result: Returned 20 users without transactions, e.g., Austin Glass, Jason Martinez, confirming accurate identification of inactive users.

# Challenges and Assumptions:

Assumed data consistency post-separation and cleaning, ensuring all user_id references in transactions match _id in users.

Handled potential empty results by verifying data existence before aggregation.

# Automation Script ( PHASE 4 dans "CODE TEST MONGODB" )

Created an automated script clean_data.js to handle data cleaning consistently . 

This script automates the cleaning process, ensuring consistency and repeatability for future use. 

# NOTE: Please note that the shared CSV files contain the data results after the completion of the test.
