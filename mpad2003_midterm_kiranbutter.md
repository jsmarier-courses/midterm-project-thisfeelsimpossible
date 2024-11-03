**November 4th, 2024**<br>
**MPAD2003 Introductory Data Storytelling**<br>
**Kiran Butter**<br>
**Presented to Jean-Sébastien Marier**<br>

# Midterm Project: Exploratory Data Analysis (EDA)

Use one hashtag symbol (`#`) to create a level 1 heading like this one. - yo did I fix the issue?

## Foreword

For this assignment, you must extract data from a dataset provided by the instructor. You must then clean and analyze the data, create exploratory charts/visualizations, and find a potential story idea. Your assignment must clearly detail your process. You are expected to write about 1500-2000 words, and to include several screen captures showing the different steps you went through. Your assignment must be written with the Markdown format and submitted on GitHub Classroom.

I have been assigning different versions of this project to my digital journalism and data storytelling students for a few years now. Its structure was inspired by the main sections/chapters of [*The Data Journalism Handbook*](https://datajournalism.com/read/handbook/one/). This version was further inspired by the [Key Capabilities in Data Science](https://extendedlearning.ubc.ca/programs/key-capabilities-data-science) program offered by the University of British Columbia (UBC).

**Here are some useful resources for this assignment:**

* [GitHub's *Basic writing and formatting syntax* page](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
* [The template repository for this assignment in case you delete something by mistake](https://github.com/jsmarier/jou4100_jou4500_mpad2003_project2_template)

Did you notice how to create a hyperlink? In Markdown, we put the clickable text between square brackets and the actual URL between parentheses.

And to create an unordered list, we simply put a star (`*`) before each item.

## 1. Introduction

Insert text here.

## 2. Getting Data

Use two hashtag symbols (`##`) to create a level 2 heading like this one.

To include a screen capture, use the sample code below. Your images should be saved in the same folder as your `.md` file.

![](import-screen-capture.png)<br>
*Figure 1: The "Import file" prompt on Google Sheets.*

To import the data into google sheets, I clicked save link as and saved the CSV file on my computer; it will save as a text file.
I then went to Google Sheets, clicked the File option in the top menu, clicked on import, then uploaded the data set text file. 
Then, I selected the comma option for the separator type, and clicked the import data. Once that has been clicked, the message ‘Success! File imported. Open now >>” will appear, and then click the Open now blue hyperlink and it will bring you to the imported dataset. 


This is the dataset right after it has been imported. 


Since it is a dataset from the City of Ottawa, for any description, it is written in both English and French, making the cell's length dragged out when clicked on. Looking at the dataset, there are 11 columns, letters A to K, and 28539 rows of data. In terms of how the data is structured, every data is within their respective cells–there is no overlapping into other cells. The majority of the address, latitude, longitude and ward columns will have \N in their cells, leaving gaps in the dataset. 


Columns A to D, G and K contain nominal variables since they consist of categories and differ from one another in names with no natural order (such as the status, type, description, etc.) (insert cites), whereas, columns E, F, H, I and J consist of numeric variables since they are numbers, and are either continuous within a given interval (such as the longitude or latitude) or discrete by only being specific values (like the wards) (insert cites).  

One question that comes to mind when I examine the raw data is “What is the most common type of request that gets asked?” since there are a handful of types listed in the column which determine the specific action for the city to partake. 


**Here are examples of functions and lines of code put in grey boxes:**

1. If you name a function, put it between "angled" quotation marks like this: `IMPORTHTML`.
1. If you want to include the entire line of code, do the same thing, albeit with your entire code: `=IMPORTHTML("https://en.wikipedia.org/wiki/China"; "table", 5)`.
1. Alternatively, you can put your code in an independent box using the template below:

``` r
=IMPORTHTML("https://en.wikipedia.org/wiki/China"; "table", 5)
```
This also shows how to create an ordered list. Simply put `1.` before each item.

## 3. Understanding Data

### 3.1. VIMO Analysis

Use three hashtag symbols (`###`) to create a level 3 heading like this one. Please follow this template when it comes to level 1 and level 2 headings. However, you can use level 3 headings as you see fit.

Insert text here.

Support your claims by citing relevant sources. Please follow [APA guidelines for in-text citations](https://apastyle.apa.org/style-grammar-guidelines/citations).

**For example:**

As Cairo (2016) argues, a data visualization should be truthful...


The VIMO analysis is a method used to ensure the quality, accuracy and correctness of a given dataset. In order for a dataset to be accurate, the data values must be valid (not blank or missing and within a valid range) and correct (insert cites). VIMO is an acronym that stands for valid, invalid, missing and outlier values, which is how the dataset will be assessed.

As for our dataset, it is challenging to see what data is accurate and correct given the information that is hidden. At first glance, it may seem like an error with the dataset with plenty of cells containing an \N, but that is done on purpose. For the columns containing the address, latitude and longitude, according to the City of Ottawa page, the field is only displayed for public service requests, since private service requests can display personal information (insert cites). Given that our dataset is limited, the VIMO analysis will consequently be limited to the information available. 

The first step in the VIMO analysis is to assess the validity. Valid values are variables that are correct and accurate within the dataset. The service requests ID’s, status, type, description, opened dates and channel columns seem to contain correct data within a range. When the latitude, longitude and address are available, they are valid as well and point to the Ontario and Quebec region (insert cite). 


Invalid values are values that are impossible, meaning they cannot register as valid in that context (insert cites maybe?). In this case, we cannot determine whether the hidden data represented by \N is invalid since we do not know its content. While the closed date and ward columns do contain hidden data and were not specified to in the dataset’s background, they could be deemed as non-applicable even. Rather than assessing that these values are invalid, it is better to assess them as missing.


Missing values is when the variable is left blank (insert cites) and we must evaluate what is left. Any \N in the data set is considered to be missing values since it is hidden and we do not know its content.

### 3.2. Cleaning Data

Insert text here.

### 3.3. Exploratory Data Analysis (EDA)

Insert text here.

**This section should include a screen capture of your pivot table, like so:**

![](pivot-table-screen-capture.png)<br>
*Figure 2: This pivot table shows...*

**This section should also include a screen capture of your exploratory chart, like so:**

![](chart-screen-capture.png)<br>
*Figure 3: This exploratory chart shows...*

## 4. Potential Story

Insert text here.

## 5. Conclusion

Insert text here.

## 6. References

Include a list of your references here. Please follow [APA guidelines for references](https://apastyle.apa.org/style-grammar-guidelines/references). Hanging paragraphs aren't required though.

**Here's an example:**

Bounegru, L., & Gray, J. (Eds.). (2021). *The Data Journalism Handbook 2: Towards A Critical Data Practice*. Amsterdam University Press. [https://ocul-crl.primo.exlibrisgroup.com/permalink/01OCUL_CRL/hgdufh/alma991022890087305153](https://ocul-crl.primo.exlibrisgroup.com/permalink/01OCUL_CRL/hgdufh/alma991022890087305153)
