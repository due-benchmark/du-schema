# Introduction

The main aim of this project is to describe data format for storing information about datasets in Document Understanding domain. We decided to describe each dataset with using three different files:
 1. Dataset level - for storing general information about dataset (like name or version)
 1. Documents annotation level - for storing annotations and additional document metadata (like external identifiers) 
 1. Documents content level - for storing outputs from different processing tools (e.g. output from tesseract OCR Engine)

Our core assumption was to keep it simple and were possible used external format standards. Therefore, we decided to used JSON data format for describing single dataset/document.  

# Data format details

## Dataset level 

To store information on the dataset level we are using JSON-LD format based on well known schema.org Web standard (see  this link https://developers.google.com/search/docs/data-types/dataset for more information). 

## Documents annotation level 

To store information on the Documents annotation level for all DU datasets in the same manner we created data format (see `./schema/document.json` file) with using Json-schema standard. This help us to ensure that everything is well documented and properly validated. Additionally, for storing information about whole dataset we also decided to create single jsonl file for each split in the datasets. 

## Documents content level

To store information on the Documents content level for all DU datasets in the same manner we created data format (see `./schema/document_content.json` file) with using Json-schema standard. This help us to ensure that everything is well documented and properly validated. Additionally, for storing information about whole dataset we also decided to create single jsonl file for each split in the datasets. 

# Used external standards  

## JSON-LD

JSON-LD is a well known Web standard for organization Linked Data (see this link: https://json-ld.org/ for more information).

## Json schema

JSON Schema is a vocabulary that allows you to annotate and validate JSON documents (see this link: https://json-schema.org/ for more information).

## Jsonlines 

JSON Lines is a convenient format for storing structured data that may be processed one record at a time. It works well with unix-style text processing tools and shell pipelines (see this link: https://jsonlines.org/ for more information).


