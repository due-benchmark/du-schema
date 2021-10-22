# Introduction

The main aim of this project is to describe the data format dedicated to storing information about datasets in the Document Understanding domain. Each dataset is defined on three different levels:
 1. Dataset level - storing general information about the dataset (eg. name or version)
 2. Documents annotation level - storing annotations and additional document metadata (like external identifiers) 
 3. Documents content level - storing outputs from different processing tools (e.g. output from tesseract OCR Engine)

Our core assumption was to keep it simple. Therefore, we decided to use JSON data format for describing single dataset/document.  

# Data format details

## Dataset level 

To store information on the dataset level we are using JSON-LD format. It is based on well known schema.org Web standard (see [this link](https://developers.google.com/search/docs/data-types/dataset) for more information). 

## Documents annotation level 

To store information on the documents annotation level for all DU datasets in the same manner, we created data format (see `./schema/document.json` file) using JSON-schema standard. This helps us to ensure that everything is well documented and properly validated. 
Additionally, as we are storing information about the whole dataset, we also decided to create a single `document.jsonl` file for each split in the dataset. 

## Documents content level

Similarly like in the case of documents annotation level, we created data format (see `./schema/document_content.json` file) using JSON-schema standard in order to determine the way of storing information on documents content level. 
We also decided to create a single jsonl file for each split in the dataset. 

# Used external standards  

## JSON-LD

JSON-LD is a well-known Web standard for organization Linked Data (see [this link](https://json-ld.org/) for more information).

## JSON Schema

JSON Schema is a vocabulary that allows you to annotate and validate JSON documents (see [this link](https://json-schema.org/) for more information).

## JSON Lines 

JSON Lines is a convenient format for storing structured data that may be processed one record at a time. It works well with Unix-like text processing tools and shell pipelines (see [this link](https://jsonlines.org/) for more information).


