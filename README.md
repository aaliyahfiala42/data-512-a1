# Monthly Wikipedia Traffic
## A1: Data Curation Assignment 


## Project Goal
The goal of this assignment is to construct, analyze, and publish a dataset of monthly traffic on English Wikipedia from January 1 2008 through August 30 2021.

## Data Sources
The data used for this project comes from two seperate APIs that cover Wikipedia traffic over different time intervals. 

### Wikipedia REST API
Terms of use: https://www.mediawiki.org/wiki/Wikimedia_REST_API#Terms_and_conditions

### Pagecounts API

### Pageviews API

## Known Issues
There are several known issues communicated in the API documentation. One known issue is that the data from the Pageview API excludes spiders/crawlers, while data from the Pagecounts API does not.

There are several issues and possible issues made on assumptions from merging together the counts using the two API's. One is the overlap between APIs in months and inconsitency in counting views.

Assumption that both APIs count mobile views the same, as there has been an exponential climb in technological advancement over that last 20 years, espically on mobile interfaces, it is possible that the way that the counts are calculate on mobile has changed significantly. 

## Final Visualization
<img src = '/wikipedia_traffic_200712-202108_visualization.jpg'>


## Author
Project Outline Credit: UW course Data Science 515 Human Centered Data Science taught by Dr. David W. McDonald.

Solution Created by: Aaliyah Hänni

## Sited Sources
