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

This assignment aims to extract, clean and analyze a provided dataset, create a graph and find a potential story from the findings. The dataset is a subset of a City of Ottawa larger dataset, called ‘2024 Service Requests”, found on the City of Ottawa’s open data portal, last updated on October 3rd, 2024 and then featured 251,714 entries of service requests from various means: contact or client service centres, email and web-based service portals. According to the City of Ottawa (2024b), “the data provides a summary of requests for service that require action by City staff. Data is presented by the ward and shows the responsible City department and service description.” The service requests data containing the request type, description, status, address, longitude, latitude and ward. This analysis is conducted in 4 sections: getting data, understanding data (VIMO analysis, cleaning data, exploratory data analysis), potential story and conclusion.


[Link to the original dataset on Open Ottawa](https://open.ottawa.ca/documents/65fe42e2502d442b8a774fd3d954cac5/about).

[Link to the CSV version](https://raw.githubusercontent.com/jsmarier/course-datasets/refs/heads/main/ottawa-311-service-requests-august-2024.csv).



## 2. Getting Data

Instructions to import the data into Google Sheets: 

1. Right-click the link, click “Save link as…” and save the CSV file to your computer. It will save as a text file. 
2. Go to Google Sheets, File > Import, then upload the dataset text file. 
3. Once uploaded, select the comma for the separator type, and click import data. 
4. Once imported, the message, ‘Success! File imported. Open now >>” will appear. Click on the “Open now >>” blue hyperlink, and it will take you to the imported dataset. 

**This is a screenshot of the dataset right after it has been imported.** 

![Service request dataset after it has been imported](<datasetwhenfirstimportedUSETHISONE (1).png>)</br>
*Figure 1: This screenshot shows the dataset after it has been imported*.


[Link to the Google Sheet data spreadsheet](https://docs.google.com/spreadsheets/d/1eOZ1uVapeKvocDCgMW5fZFrOu2O9v17iskftLEeP6RE/edit?usp=sharing).


There are 11 columns, letters A to K, and 28539 rows of data. In terms of how the data is structured, every data is within their respective cells– but some data is hidden at first glance. It is revealed upon clicking on it by expanding it. Since it is a dataset from the City of Ottawa, the description is written in English and French, dragging the cell's length–impacting readability. What also impacts readability is the value of ‘\N’ in the cells of the address, latitude, longitude and sometimes ward columns, indicating restricted, hidden or missing data. We cannot fully assess the data given if values are unavailable, so we are limited to what we can read and take away. 

One question that arises when examining the raw data is **“Which ward has the most requests per type?”** since it is important to see what wards need service done to improve. Thus, columns A, C and J (the service request IDs, the type and ward number) are especially relevant in this analysis. Columns A and C contain nominal variables since they consist of categories and differ in names with no natural order (Touhidul Islam, 2024); the type and service request IDs are distinguished. As for column J, it consists of numeric variables since they are numbers and are discrete by being a specific value (ward number) (Islam, 2024).
These three columns are analyzed further, along with the rest of the dataset. 


## 3. Understanding Data

### 3.1. VIMO Analysis

The **VIMO** analysis is a method used to ensure the quality, accuracy and correctness of a given dataset. For a dataset to be accurate, the data values must be valid (not blank or missing and within a valid range) and correct (Statistics Canada, 2020, 1:43). **VIMO** is an acronym that stands for **valid**, **invalid**, **missing** and **outlier values**, which is how the dataset will be assessed.

For this analysis, columns A, C and J will be assessed since they are key to ‘’answer‘’ to our question. 

**VALID VALUES**

The first step in the **VIMO** analysis is to assess the **validity**, ensuring values are correct and accurate. 
Columns A and C contain valid values since there are no duplicate service request IDs, and the types are within the scope of options. As for column J, it is challenging to see what data is accurate and correct given some cell information is hidden by the value ‘\N’. It may appear like an error, but I assume it was intentional. According to the City of Ottawa (2024b), the address, latitude and longitude columns only display information for public service requests to avoid publishing personal information. However, it does not mention so for the ward column; therefore, we will assume that ‘\N’ means non-applicable instead of private information. 

**INVALID** and **MISSING VALUES**

**Invalid** values are impossible and cannot register as valid in the given context (Statistics Canada, 2020, 1:52). We already determined that columns A and C are valid– but column J’s non-applicable problem still stands. Since we cannot render these ‘\N’ values invalid because of their unknown content, it is better to assess them as **missing**, where a variable is left blank, and we must evaluate the remaining data (Statistics Canada, 2020, 2:06). 

**OUTLIER VALUES**

**Outlier** values are extremely small or large to relative expectations (Statistics Canada, 2020, 2:17). I would argue there are no outlier values. While the service request IDs are lengthy, it is a typical size for IDs. Column C has values that reflect the same types and no other value outside the assigned options. Column J (besides the ones that contain ‘\N’) are all within 1 - 24, the number of wards in the Ottawa region (City of Ottawa, n.d.-b).



### 3.2. Cleaning Data

**ADDING FILTERS** 

Since there are a lot of cases of non-applicable/hidden information, to clear the dataset, I only focused on requests that have public information easily available to us. 
I cleared every instance of \N in the address column (and thus, the longitude, latitude and ward column) using the “Create a filter” option in Google Sheets. 

Instructions (Marier, 2021, 6:03): 

1. Click Data >  Create a filter. 
2. Click the filter button (represented by three horizontal lines) next to the address column.
3. Click on Filter by condition, select ‘Text does not contain’, and input ‘\N’ 
4. Click  OK at the bottom in green. 
5. Copy and paste the entire dataset by clicking the gray box in the far left corner to apply the changes.

This makes it easier to create charts of public requests since we do not have to incorporate 28935 rows of data. Instead, we can focus on data that is available to us (the public requests).


**`SPLIT` FUNCTION**

Since the dataset is from the City of Ottawa, it included both English and French, but considering that English is more widely known, I removed the French in the dataset to be more clear. 
The French is in the description column. To remove the French, I used the `SPLIT` function; a function used to split text based on a separator into its own parts.


Instructions (Marier, 2021, 13:00;  Google, n.d.):

1. Add two columns to the right by right-clicking Column D. 
2. In E2, initialize the `ARRAYFORMULA` function by typing `=ARRAYFORMULA` (we will use `ARRAYFORMULA` to fill up the entire column, instead of using the fill handle).
3. Type in the brackets: 
```r
SPLIT(D2:D4393, “|”)
``` 
where the range is D2:D4393 and delimiter is “|”

4. Hit Enter.
5. Copy and Paste the entire English column (column E)
6. Right-click and go to Paste Special > Values only (allows us to remove the French description (column F) and mixed English and French description columns (column D)). 


**FREEZING COLUMNS**

Freezing columns and rows is useful for scrolling through the dataset and keeping track of the column or row you are in. This is useful, considering the dataset is large. 

Instructions (Marier, 2021, 5:42):

1. Click the number of where the column labels are (usually row one, thus the number one on the far right)
2. Click View > Freeze > Up to 1 row.

What this did was freeze that specific row, so while we scroll, the column label will follow along.


**Below is a screenshot of the dataset after cleanup.**

![Service request dataset after cleanup](<datasetaftercleaningTHISONE.png>)<br>
*Figure 2: This screenshot shows the dataset after it has been cleaned.*




### 3.3. Exploratory Data Analysis (EDA)

My thought process in creating the chart was to originally show how many requests wards receive per type of request, but since the dataset has been cleaned and modified, that question has now changed. I limited the data to only focus on public requests, or rows that display information instead of all 28935 rows since I did not want to overload the data onto the chart.
Limiting to public requests has left four types from the original 11: roads and transportation, city facilities, recreation and culture and social community service. The modification of only displaying public requests now allows for a significantly smaller portion of the data to be graphed, making it easier for the viewer to grasp. Instead of how many requests wards receive per type, my thought process was now how many public requests wards receive per the four types (assuming they are public) to highlight what issues they can solve from the requests.

As for creating the graph, I chose a stacked column chart since it is best to show what requests per type contribute to the overall total of ward’s requests. 

To create the pivot table:
Insert > Pivot Table
Then, add Ward under Rows
Type under Columns 
And
Service request ID under values. Ensure that the summarize by is set to COUNTA.

To create the graph
Insert > Chart, then select stacked column chart, and it should autmoatcailly create the graph


Furthermore, according to Statistics Canada, “stacked bar charts can be very difficult to analyze if too many items are in each stack” (insert cite), but since I limited the chart to four types, there would be less difficulty in analyzing the number of requests. Additionally, since all the information is in one graph, rather than four graphs to depict the requests per type, according to Cleveland and Mcgill’s hierarchy of elementary perceptual tasks, it allows for the viewer to digest the information easily and compare the values (insert cite) 

These variables can tell a story of the areas that are well, and the areas that need work in the four types of the wards. Immediately, the amount of requests for roads and transportation is noticeable. It seems that all wards one to 24 receive a lot of issues when it comes to road or transportation. Another noticeable variable is the lack of city facilities requests. Only wards 18 and 23 have received requests on city facilities, which can potentially indicate that wards 18 and 23 have work to do revolving around their city facilities, while every other ward is performing well. As for social community service, some wards have a lot of requests and others have little to none at all; this highlights the type of work that needs to be done in those wards. As for recreation and culture, every ward seems to receive a handful of requests.


**This section should include a screen capture of your pivot table, like so:**

![](pivot-table-screen-capture.png)<br>
*Figure 2: This pivot table shows...*

**This section should also include a screen capture of your exploratory chart, like so:**

![](chart-screen-capture.png)<br>
*Figure 3: This exploratory chart shows...*

## 4. Potential Story

To tell the story of which wards need improvements and where they perform well, gathering more data or variables, such as how much were resolved, cancelled or are currently active reflected in the original dataset can be useful. 
While we do see how many requests are made, we cannot see if the request was resolved, cancelled or is active, so we cannot know if areas are being improved if requests were cancelled or are currently worked on. 
To gather insight, we could interview the councilors respective to their ward to see how requests get handled accordingly. For example, we saw that only wards 18 and 23 have city facilities requests from our graph, so we can interview councilor’s Marty Carr and Allan Hubley to see why there are instances of such (insert cite).
Furthermore, digging deeper into Ottawa’s funds can determine why some requests are not fulfilled. On August 8th 2024, which is recent to the date of service requests in the dataset (August 1st), there was a statement from mayor Mark Sutcliffe issuing that Ottawa is facing a financial crisis. Sutcliffe (insert cite) claims “Our city is facing unprecedented financial challenges that are not of our making” and that “this can’t continue or we will face historic challenges in our next budget.” This statement highlights that there’s a possibility that some areas cannot be improved at the moment since there is a lack of budget or income, which will add to the story. 


## 5. Conclusion

My thought process throughout this assignment was to clean the data in a way to easily create a graph. The most challenging part would be cleaning the data. It was difficult to find what can be edited considering that I found all the data too important, hence why I only ended up removing the ‘\N’ since it served no purpose– I felt everything else served some importance though. I identified a gap in my knowledge when it came to applying the cleaning techniques, since the majority of time was spent searching for cleaning techniques online and figuring out how to remove, edit, etc. on the Google sheet. 

The rewarding part would be creating the graph based on my cleaned dataset. Knowing that I had made a graph out of an idea in mind from the data that I had cleaned and making connections was rewarding since I felt I was presenting my own vision of a portion of the data. It made me feel like I was cut out for this type of work involving graphs, data, etc. 

What I could have done differently is implemented more cleaning methods. I felt that I did not really explore what other data I could edit–I played it safe by keeping the majority of the data. I could have removed data that did not serve my vision, or use other functions like =CONCATENATE to merge it with other data. That way, it would have been an honest and experimental attempt of cleaning data. 


## 6. References

Cairo, A. (2016). *The Truthful Art: Data, Charts, and Maps for Communication*. New Riders. [https://learning.oreilly.com/library/view/the-truthful-art/9780133440492/ch05.html#ch05](https://learning.oreilly.com/library/view/the-truthful-art/9780133440492/ch05.html#ch05)

City of Ottawa. (n.d.-a). *Mayor and City Councillors*. City of Ottawa. [https://ottawa.ca/en/city-hall/mayor-and-city-councillors](https://ottawa.ca/en/city-hall/mayor-and-city-councillors)

City of Ottawa. (n.d.-b). *Ward maps and school board zones*. City of Ottawa. [https://ottawa.ca/en/city-hall/elections/ward-maps-and-school-board-zones#section-c7309d83-a827-4604-a3f6-7f29f875ad7a](https://ottawa.ca/en/city-hall/elections/ward-maps-and-school-board-zones#section-c7309d83-a827-4604-a3f6-7f29f875ad7a)

City of Ottawa. (2024a, August 8). *Mayor says Ottawa is facing financial crisis based on shortfall in federal and provincial funding*. City of Ottawa. [https://ottawa.ca/en/city-hall/city-news/newsroom/mayor-says-ottawa-facing-financial-crisis-based-shortfall-federal-and-provincial-funding](https://ottawa.ca/en/city-hall/city-news/newsroom/mayor-says-ottawa-facing-financial-crisis-based-shortfall-federal-and-provincial-funding)

City of Ottawa. (2024b, September 4). *2024 Service Requests*. Open Ottawa. [https://open.ottawa.ca/documents/65fe42e2502d442b8a774fd3d954cac5/about](https://open.ottawa.ca/documents/65fe42e2502d442b8a774fd3d954cac5/about)

Google. (n.d.). *ARRAYFORMULA*. Google Help. [https://support.google.com/docs/answer/3093275?hl=en](https://support.google.com/docs/answer/3093275?hl=en)

Marier, J.-S. (2021). *Cleaning Data in Google Sheets* [Video]. YouTube. [https://www.youtube.com/watch?v=U4yigiawIEU](https://www.youtube.com/watch?v=U4yigiawIEU)

Statistics Canada. (2010, September 2). *5.2 Bar Chart*. Statistics Canada. [https://www150.statcan.gc.ca/n1/edu/power-pouvoir/ch9/bargraph-diagrammeabarres/5214818-eng.htm](https://www150.statcan.gc.ca/n1/edu/power-pouvoir/ch9/bargraph-diagrammeabarres/5214818-eng.htm)

Statistics Canada. (2020, September 23). *Data Accuracy and Validation: Methods to ensure the quality of data*. Statistics Canada. [https://www.statcan.gc.ca/en/wtc/data-literacy/catalogue/892000062020008](https://www.statcan.gc.ca/en/wtc/data-literacy/catalogue/892000062020008)

Touhidul Islam, M. (2021, February 25). *Levels of Measurement (Nominal, Ordinal, Interval, Ratio) in Statistics*. Data Science Central. [https://www.datasciencecentral.com/levels-of-measurement-nominal-ordinal-interval-ratio-in/](https://www.datasciencecentral.com/levels-of-measurement-nominal-ordinal-interval-ratio-in/)


