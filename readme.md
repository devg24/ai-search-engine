# search-engine

## Demo 

https://drive.google.com/file/d/1_798jx_geXRxVc9Zlw5timWmlooymbOf/view?usp=share_link

## Overview

This is a simple search engine that can be used to gather information about a research author from the web. It uses the [Trafilatura](https://trafilatura.readthedocs.io/en/latest/) and [SERP API](https://serpapi.com/?gclid=Cj0KCQjwuNemBhCBARIsADp74QRTiRPvwLM2Ot-D1TV9h1L4cfAtzRNrEs4bJb1e7M1aIU1bLoSV-gMaAvnYEALw_wcB) libraries to gather relevant documents and then parse those documents using various techniques.

## setup

1. Use the yml file to create a conda environment:
    
    ```bash
    conda env create -f environment.yml
    ```
2. Activate the environment:
    
    ```bash
    conda activate research
    ```
3. Repo structure:
    - `Documents/`: contains the Documents extracted from the web
    - `doc_retrieval.ipynb`: contains the notebook used for the project
    - `environment.yml`: contains the conda environment used for the project
    - `README.md`: this file
    - `report.pdf`: contains the report for the project

## Usage

1. In the `doc_retrieval.ipynb` notebook, change the Query variable to the author you want to search for and feel free to add questions to the list of questions you want the answer to.

2. Run the notebook and wait for the results to be displayed.

3. Optionally, you can comment the last cell to keep the documents that were extracted from the web.


## algorithmic design

The algorithm is composed of 3 main steps:

1. **Document Retrieval**: This step is used to gather relevant documents from the web. It uses the SERP API to get the top 10 results for the query and then uses the Trafilatura library to extract the text from the documents.

2. **Document Processing**: This step is used to process the documents that were retrieved in the previous step. It uses regular expressions and other custom functions to clean the text and divide it into sections.It then uses sentence BERT to embed the passages. The passages are then put into a dataframe and a KNN model is used to find the k most relevant sections for each question.

3. **Answer Generation**: This step is used to generate the answer from the sections that were retrieved in the previous step.

## Issues and Future Work

- The algorithm is fully accurate. This is due to the fact that the SERP API has a limit of 10 requests per minute and the Trafilatura library is not very efficient.

- The model is unable to extract the answer to some questions. This is due to the fact that the model is not very good at extracting answers from long passages.

## Change Log