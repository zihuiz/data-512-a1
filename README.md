# Data 512 A1 Data curation

## Project Description
The goal of this assignment is to analyze the traffic on English Wikipedia from January 1 2008 through August 30 2021, and construct related datasets. In this project, data about Wikipedia traffic is collected from two Wikimedia REST api, and then combined into a single file for analysis. All the code used in this project is stored in the jupyter notebook `hcds-a1-data-curation.ipynb`. All the raw data from the two APIs are stored in the five JSON files. The cleaned data is stored in `en-wikipedia_traffic_200712-202108.csv`. 

## Licenses and Terms of use
The project used s data from [Wikimedia Foundation REST API](https://www.mediawiki.org/wiki/Wikimedia_REST_API). It is licensed under the CC-BY-SA 3.0 and GFDL licenses. 
The term of use for the Wikimedia Foundation REST API can be accessed from [here](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions).
The privacy policy for the Wikimedia Foundation REST API can be accessed from [here](https://foundation.wikimedia.org/wiki/Privacy_policy)

## Data Sources
The project used the following REST APIs:
- The Legacy Pagecounts API ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts), [endpoint](https://wikimedia.org/api/rest_v1/#!/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end)).
- The Pageviews API ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews), [endpoint](https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end)).

## Final Data File
The processed data is stored in a CSV file named `en-wikipedia_traffic_200712-202108.csv`. The table contains the following attributes:
| Name      | Description |
| ----------- | ----------- |
| year      | YYYY       |
| month   | MM        |
|pagecount_all_views |num_views. The combined views from desktop and mobile from Legency Pagecounts API |
|pagecount_desktop_views |num_views. The views from desktop from Legency Pagecounts API |
|pagecount_mobile_views |num_views. The views from mobile from Legency Pagecounts API |
|pageview_all_views |num_views. The combined views from desktop and mobile from Pageviews API |
|pageview_desktop_views |num_views. The combined views from desktop from Pageviews API |
|pageview_mobile_views |num_views. The combined views from mobile from Pageviews API |

## Considerations
- We extract data from the two APIs for different periods of time. For the Legacy Pagecounts API, we collect data from December 2007 through July 2016. For the Pageviews API we collect data from July 2015 through August 2021. Notice that the Legacy Pagecounts API started to collect mobile data after October 2014. Thus the true time range for mobile traffic from the Legacy Pagecounts API is October 2014 to July 2016.
- In this project, we are only interested in organic (user) traffic. The Pageview API allows us to filter by agent=user. So the data collected from the Pageviews API contains only user data, while the data collected from the Legacy Pagecounts API may contains other traffic, such as traffic by web crawlers or spiders. 
