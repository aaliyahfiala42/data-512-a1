# Monthly Wikipedia Traffic
## A1: Data Curation Assignment 


## Project Overview
The goal of this assignment is to construct, analyze, and publish a dataset of monthly traffic on English Wikipedia from January 1 2008 through August 30 2021. Data about Wikipedia page traffic is accessed from two Wikimedia REST API endpoints and merged into a single dataset, where simple data processing is performed on the data, and then analyzed and visualized.

## Data Sources
In order to measure Wikipedia traffic from 2008-2021, data is collected from two different API endpoints, the Legacy Pagecounts API and the Pageviews API. For each API, data is collected for all months where data is available. The raw results are saved into 5 separate JSON source data files (one file per API query type).

### Wikipedia REST API

Terms of use: https://www.mediawiki.org/wiki/Wikimedia_REST_API#Terms_and_conditions

### Pagecounts API
The Legacy Pagecounts API provides access to desktop and mobile traffic data from December 2007 through July 2016.

Documentation: https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts

Endpoint: https://wikimedia.org/api/rest_v1/#/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end

### Pageviews API
The Pageviews API provides access to desktop, mobile web, and mobile app traffic data from July 2015 through last month.

Pageviews API Documentation:https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews

Endpoint: https://wikimedia.org/api/rest_v1/#/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end

## Datasets
There are 6 key data files stored for this project stored in the data folder. The first 5 are JSON files, where each JSON file is correlated with a single data call. The 5 JSON files are in the filename format: apiname_accesstype_firstmonth-lastmonth.json. 

The JSON files are: 

legacy_mobile-site_200801-201607.json (contains the following headers: Project, Access-Site, Granularity, Timestamp, Count)

legacy_desktop-site_200801-201607.json (contains the following headers: Project, Access-Site, Granularity, Timestamp, Count)

pageviews_mobile-app_201507-202108.json (contains the following headers: Project, Access-Site, Granularity, Timestamp, Views)

pageviews_mobile-web_201507-202108.json (contains the following headers: Project, Access-Site, Granularity, Timestamp, Views)

pageviews_mobile-web_201507-202108.json (contains the following headers: Project, Access-Site, Granularity, Timestamp, Views)


The 6th file is titled en-wikipedia_traffic_200712-202108.csv and is an CSV file that contains all of the finalized, processed data from both API calls. This file contains the year, month, all (desktop + mobile) views, desktop views, and mobile views from both the pagecount and pageview APIs. 

The column headers and types in parentheis display as:

year (YYYY)

month (MM)

pagecount_all_views (num_views)

pagecount_desktop_views (num_views)

pagecount_mobile_views (num_views)

pageview_all_views (num_views)

pageview_desktop_views (num_views)

pageview_mobile_views (num_views)

Steps for extracting each dataset are included in the hcds-a1-data-curation.ipynb Jupyter Notebook.

## Known Issues
There is 1 year of overlapping traffic data between the two APIs, July 2015 - July 2016. The number of views between these overlapping dates are not equal and vary quite a bit, especially when looking at desktop views. One way to possible account for this discrepancy is that the data from the Pageview API excludes spiders/crawlers, while data from the Pagecounts API does not.

There are several assumptions that were made when merging together the counts using the two API's, such as the assumption that both APIs count mobile views the same, as there has been an exponential climb in technological advancement over that last 20 years, espically on mobile interfaces, it is possible that the way that the counts are calculate on mobile has changed significantly. 

There are also several other known issues with the data communicated in the API documentation. See: https://wikitech.wikimedia.org/wiki/Analytics/Data_Lake/Traffic/Pageview_hourly#Changes_and_known_problems_since_2015-06-16

## Final Visualization: Monthly Wikipedia Traffic 2008-2021

The goal of the analysis performed below is to create a visulization that quickly summarizes the number of views that Wikipedia recieves every month for the following metrics: mobile traffic, desktop traffic, and all traffic (mobile + desktop).

The final visulization plots the total number of Wikipedia views by month and contains data from the both the Legacy Pagecounts and Pagviews APIs. All views are shown in blue, desktop views are shown in green, and mobile views are shown in orange. The Legacy Pagecount API is displayed in a lighter shade, to distinguish data from the 2 APIs, to allow for easy comparison.

Note that there is some overlap between data visualized for the two APIs during the period of July 2015 - July 2016. The number of views between these overlapping dates are not equal and vary quite a bit, especially when looking at desktop views. One way to possible account for this discrepancy is that the data from the Pageview API excludes spiders/crawlers, while data from the Pagecounts API does not.

<img src = '/wikipedia_traffic_200712-202108_visualization.jpg'>


## Author
Project Outline Credit: UW course Data Science 515 Human Centered Data Science taught by Dr. David W. McDonald.

Solution Created by: Aaliyah Hänni

## Sited Sources

https://towardsdatascience.com/how-to-parse-json-data-with-python-pandas-f84fbd0b1025 

https://www.codegrepper.com/code-examples/python/add+two+dataframes+pandas

https://www.codegrepper.com/code-examples/python/parse+string+in+pandas+dataframe

https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.merge.html

https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_csv.html

https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.plot.html
