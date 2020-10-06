

# DATA 512 A1: Data Curation
### By Mayank Goel

## License
The repostory follows MIT License as mention [here](https://github.com/mickkygoel/data-512/blob/main/data-512-a1/LICENSE).

## GOAL
For this assignment, we will combine data about Wikipedia page traffic from two different Wikimedia REST API (Links to an external site.) endpoints into a single dataset, perform some simple data processing steps on the data, and then analyze that data.

## API details
We will be using following two APIs.

1.  The Legacy Pagecounts API ([documentation](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts), [endpoint](https://wikimedia.org/api/rest_v1/#!/Pagecounts_data_(legacy)/get_metrics_legacy_pagecounts_aggregate_project_access_site_granularity_start_end)) provides desktop and mobile traffic data till July 2016.
2.  The Pageviews API ([documentation ](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews), [endpoint](https://wikimedia.org/api/rest_v1/#!/Pageviews_data/get_metrics_pageviews_aggregate_project_access_agent_granularity_start_end)) provides desktop, mobile web, and mobile app traffic data from July 2015 till last month.

Please read the Wikimedia Foundation REST API terms of use [here](https://www.mediawiki.org/wiki/Wikimedia_REST_API#Terms_and_conditions).


## Caveats
1. We're interested in organic (user) traffic, as opposed to traffic by web crawlers or spiders. The Pageview API is therefore filtered by agent=user.
2. There was about 1 year of overlapping traffic data between the two APIs. Both the sources are included for that period

## Reproduce
This repository should be straight forward to reproduce. Simply download the python notebook file and run it in your python environment. Teh code uses standard libraries and generates all outputs without any other manual step.

## Repository content
- Json raw data files 
	- *pagecounts_desktop-site_200801-201607.json*
	- *pagecounts_mobile-site_200801-201607.json*
	- *pageviews_desktop-site_201507-202008.json*
	- *pageviews_mobile-web_201507-202008.json*
	- *pageviews_mobile-app_201507-202008.json*

- CSV with formatted data: *en-wikipedia_traffic_200712-202008.csv*
- Python notebook containing all code and information: *A1.ipynb*
- Final visualization: *A1 final output.png*

## Final CSV format

1. *year* (int64): Year of data 
2. *month* (int64): Month of data 
3. *pagecount_all_views* (float64): Total traffic from Pagecounts API
4. *pagecount_desktop_views* (float64): Desktop traffic from Pagecounts API
5. *pagecount_mobile_views* (float64): Mobile traffic from Pagecounts API
6. *pageview_all_views* (float64): Total traffic from Pageviews API
7. *pageview_desktop_views* (float64): Desktop traffic from Pageviews API
8. *pageview_mobile_views* (float64): Mobile traffic from Pageviews API

For any further information, contact the author at mickkygoel@gmail.com
