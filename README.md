# Amazon customer sentiment analysis in MongoDB
### Project overview

This project aims to analyze customer sentiment on Amazon using MongoDB as the primary database for data storage and retrieval. The goal is to extract insights from customer reviews and feedback, enabling businesses to better understand customer sentiment and make data-driven decisions.

### Data Sources

Amazon customer sentiment data: The primary dataset used for this analysis is the "Amazon customer sentiment data.json", file containing detailed information about each customers sentiment on Amazon products. 

### Technologies Used

MongoDB: NoSQL database for storing and managing customer review data.

SQL: MSSQL for cleaning of customer data.

### Project Goals

Gain insights into customer sentiment towards Amazon products/services.

Enable businesses to identify trends and patterns in customer feedback.

Facilitate data-driven decision-making for product improvement and customer satisfaction enhancement.

### Data cleaning/ preparation

1. Clean and preprocess textual data.
2. Remove stopwords.
3. Perform lemmatization.


## EDA Process

EDA involved exploring the dataset to answer the following questions, such as:

1. What is the overall sentiment of customers review for different product categories?
   ``` mongoDB
   db.customer.aggregate[{$group: {...}}]id: "$product_categoryaverage_sentiment: {$avg: "$sentiment"}
   ```

   
![Mongo query 3](https://github.com/Emmaue/MongoDB-project/assets/87420794/f1ca46c3-fec6-4a50-ae0a-7e29417d0a10)



2. Which products have the highest average star ratings?
   ``` mongoDB
   db.customer.aggregate([{$group: {_id: "$product_id", average_rating: {$avg: "$star_rating"}}},{$sort: {average_rating: -1}}])
   ```

   
   ![mongo query 4](https://github.com/Emmaue/MongoDB-project/assets/87420794/6115fbd0-571b-4b0f-90bd-dceb09bf403c)



   3. Who are the top reviewers based on the count of reviews submitted?
         ``` mongoDB
       db.customer.aggregate([{$group: { _id: "$customer_id", total_reviews: { $sum: 1}}}{$sort: {total_reviews: -1}}])
   ```

   
![Mongo query 5](https://github.com/Emmaue/MongoDB-project/assets/87420794/39771d47-1209-4e2a-9aad-cd5962dd8323)



4. List of customers ID's without verified purchase.
     ``` mongoDB
       db.customer.find({verified_purchase: "N"}, {customer_id: 1, verified_purchase: 1})
   ```
     

![mongo query 6](https://github.com/Emmaue/MongoDB-project/assets/87420794/2927c897-e7ea-4d8e-9dfb-b36940e36e37)



5a. Count of customers with verified purchase.

   ``` mongoDB
       db.customer.find({verified_purchase: "Y"}).count()
   ```

5b. Without verified purchase

``` mongoDB
       db.customer.find({verified_purchase: "Y"}).count()
   ```



![mongo query 7](https://github.com/Emmaue/MongoDB-project/assets/87420794/8f2b87cc-2aae-4d4d-aebf-d4da2064f6de)

## Conclusion

In conclusion, the Amazon customer sentiment analysis project utilizing MongoDB presents a valuable opportunity to leverage data-driven insights for enhancing customer experience and making informed business decisions. By analyzing customer reviews and feedback, businesses can gain a deeper understanding of customer sentiment, identify areas for improvement, and prioritize product enhancements or service adjustments.

