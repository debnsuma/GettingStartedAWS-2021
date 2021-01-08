### Bunch of small demos 
-------------------------

**S3 Demo**
-----------
0. To to the S3 Demo Directory 

    - cd /home/ec2-user/environment/code/GettingStartedAWS-2021/myS3CloudFrontDemo

1. Create a bucket 

    - aws s3 mb s3://mys3demo-2021-123         # replace with your bucket name

2. Upload the index.html file into the bucket 

    - aws s3 cp index.html s3://mys3demo-2021-123/index.html

3. Open Console and go to S3 


**Lambda Demo**
---------------

1. Install Chalice 
    - sudo pip3.7 install chalice
2. Create a Chalice Project 
    - chalice new-project myLambdaDemo
    - cd myLambdaDemo
3. Edit "requirements.txt"
    - echo "boto3" > requirements.txt
    - echo "Pillow" >> requirements.txt
4. Edit the app.py code.
    - Input Bucket : demo-bucket-input-2021
    - Output Bucket : demo-bucket-output-2021

5. Install the packages 
    - sudo pip3.7 install -r requirements.txt

6. Deploy the app. 
    - chalice deploy 


**Glue/Athena Demo**
--------------------



Glue Data Catalog and Athena 
----------------------------

1. Store File in S3 
2. Collect metabada with Glue ETL 
3. Run Query using Athena 
----------------------------

1. Create a S3 bucket (Already Created : "aws-glue-suman")
    - Upload the raw data : yellow_tripdata_2020-06.csv   

2. Open Glue 
    - Crawler   > Name "taxi_data_crawler"
    - Path      > s3://aws-glue-suman/
    - IAM Role  > default
    - DB Name   > mydb
    - Prefix    > taxi_

3. Open Athena 
    
SELECT * FROM "mydb"."taxi_aws_glue_suman" limit 10;

SELECT * FROM "mydb"."taxi_aws_glue_suman" 
WHERE payment_type = 2
limit 10;