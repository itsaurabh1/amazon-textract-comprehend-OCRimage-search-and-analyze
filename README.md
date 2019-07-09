## Amazon Textract Comprehend Image Search with Elasticsearch
We will be using Amazon Textract, Amazon Comprehend, Amazon Elasticsearch with Kibana, Amazon S3,  Amazon Cognito to search and analyze over large number of images.


#Architecture
-----------

Architecture below shows the core components. 

![](arch.JPG)

In this architecture, Users upload image like purchase order, grocery receipt or phone bill to Amazon S3 bucket. Image can be uploaded by user facing frontend application like mobile app or desktop client. As soon as image uploaded into Amazon S3, a S3 upload event triggers AWS lambda function, which call Amazon Textract. 

Amazon Textract retrieve text from image and send it to Amazon Comprehend for analysis. Amazon comprehend perform key phrase analysis and topic modeling on retrieved text and store organized data into Amazon elastic search, which comes with Kibana as visualization layer. User can create log-in access with Amazon Cognito and access Kibana to analyze result by searching topics like purchase order items, purchase dates, vendor name etc.


## Image pipeline

1. User uplaods data in Amazon S3.
2. This event triggers a lambda function to call Textract.
3. Textract extract text from images.
4. Text is analyze by Amazon Comprehend.
5. Analyzed Result is stored in elasticsearch for search and analysis.
6. User logs in using Cognito to Kibana- Elasticsearch dashboard and analyzes the OCR data in the image.

## License Summary
This sample includes:

The documentation is made available under the Creative Commons Attribution-ShareAlike 4.0 International License. See the LICENSE file.
