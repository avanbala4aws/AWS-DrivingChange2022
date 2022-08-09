# DrivingChange

---

Description - This project is a serverless and asynchronous solution for John L Scott, a real estate firm in the Washington Area, to detect and highlight restrictive language in their historical documents.  

## Architecture

<p align="center">
  <img src="architecture/workstream1-part1.png" alt="Size Limit CLI" width="738">
</p>

<p align="center">
  <img src="architecture/workstream1-part2.png" alt="Size Limit CLI" width="738">
</p>

<p align="center">
  <img src="architecture/workstream2.png" alt="Size Limit CLI" width="738">
</p>

## How it Works

1. WorkStream 1 - Document Ingestion
   - This workstream completes the splitting and conversion of uploaded documents. Documents can be in the form of PDF,PNG,JPEG,TIFF and will be converted to PNGs for the Textract API to detect.

2. WorkStream 1 - Text Extraction
   - Workstream 1 is continued here as Textract will detect and extract the text and/or handwriting on each page of the document.

3. WorkStream 2 - Language Identification
   - The second workstream is the final step of this application, as the textract outputs are matched with the restrictive words list provided by the customer. The original document will be highlighted with a red box around such language using fuzzy string matching. 


## Dependencies

- [Docker](https://docs.docker.com/get-docker/)

- [AWS SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install.html)

- [Python](https://www.python.org/downloads/)


## Install

1. Build
    ```commandline
    sam build --template-file template.yaml --use-container
    ```
   
2. Deploy
    ```commandline
    sam deploy --stack-name ***** --template-file .aws-sam/build/template.yaml --capabilities CAPABILITY_IAM --resolve-s3
    ```
   _Input a [valid](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-using-console-create-stack-parameters.html) value for stack name_
   
   
## Clean Up

```commandline
sam delete --stack-name *****
```
_Input a [valid](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-using-console-create-stack-parameters.html) value for stack name_
