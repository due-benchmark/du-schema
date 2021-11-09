# Introduction

The main aim of this project is to describe the data format dedicated to storing information about datasets in the Document Understanding domain. Each dataset is defined on three different levels:
 1. Dataset level - storing general information about the dataset (e.g. name or version)
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

# Standards used

## JSON-LD

JSON-LD is a well-known Web standard for organization Linked Data (see [this link](https://json-ld.org/) for more information).

## JSON Schema

JSON Schema is a vocabulary that allows you to annotate and validate JSON documents (see [this link](https://json-schema.org/) for more information).

## JSON Lines 

JSON Lines is a convenient format for storing structured data that may be processed one record at a time. It works well with Unix-like text processing tools and shell pipelines (see [this link](https://jsonlines.org/) for more information).

## Common format

The aim of the `documents_content` schema is to store outputs from external tools. 
We decided to create a format - _common format_ - for storing information about documents' contents.
The main advantage of a common format, compared to hOCR, is easier parsing and the use of less disk space. 

Information that is stored in the common format is a list of tokens created from the document's text, 
positions of those tokens represented by bounding boxes, and confidence scores of the OCR engine. What
is more, it stores also information about pages of a document and lines of text. For both, 
a list of token identifiers is stored, so that tokens are mapped to pages and lines. Also,
it contains information about bounding boxes for each page and each line of text. 
For more details please refer to descriptions in `schema/common_format.json`.

# Examples
Please refer to `examples` directory to see fragments of AxCell and DocVQA datasets defined according to the format. 

Moreover, in `examples` directory one may find two one-document examples of schema-compliant descriptions: `examples/simple_example` and `examples/group_examples`.
Both examples contain `document.jsonl` and `documents_content.jsonl` files. 

`simple_example` dataset consists of the three-lines one-page document with English text:

On the 12th of January 2021  
we met in Kingston 

Values that were annotated for this document are: `city: Kingston` and `date: 12.01.2021`. 
Also, different formats of dates are allowed. 

`group_example` dataset consists of one one-page document with three-line English text:

John Smith and Mary Jones were  
grouped together, the same as Kate  
TAYLOR and Alex Armstrong. 

Values which were annotated are groups: group 1 is John Smith and Mary Jones, group 2 is Kate Taylor and Alex Armstrong.
We would like to allow surnames also in lower and upper case modes. 
