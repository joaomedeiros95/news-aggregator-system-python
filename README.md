# News Aggregator System

## Tech Stack
- Python
- FastAPI
- MongoDB

## Project Plan
- Environment Setup (1h15min)
	- Virtual Environment (15min)
		- FastAPI & uvicorn, pymongo, lib for scraping (BeautifulSoup/Scrapy)
	- Dockerfiles and compose (45min)
	- Initial FastAPI config (15min)
- Create the scraper (3h45min)
	- Identify patterns on the news article webpage for the fields (title, date, news_provided_by, content) (20min)
	- Write a scraping script to work with one URL (2h)
	- Implement some error handling to deal with connection errors and missing fields (40min)
	- Implement unit tests to make sure that the scraper is working properly (45min)
- Clean and format the data (1h)
	- Create a function to clean and format the data scraped from the newswire (30min)
	- Add some validations to ensure data correctness (15min)
	- Write unit tests (15min)
- Mongo DB (1h15min)
	- Create schemas to define how to store the data (15min)
	- Define the indexes based on the query needs (15min)
	- Create the function to insert the data (15min)
	- Define how to avoid duplicated data, probably create a unique index on some identifier from the article (30min)
- Setup FastAPI (1h)
	- Define the endpoint structure for FastAPI (30min)
	- Create the query endpoint to filter data using a variety of fields (30min)
- Define monitoring (45min)
	- Define how to monitor the scraping tasks (15min)
	- Write the monitoring system (30min)
- Test the whole system(2h)
	- Create some integration and unit tests to make sure everything is working well (2h)
- Write the documentation about the project (1h)
	- Add missing parts that were not added during the coding phase (1h)
- **Total:** 12 hours to complete the required code
- **Bonus 1:** 1h30min
- **Bonus 2:** 1h30min
- **Total:** 15h
