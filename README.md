# News Aggregator System

## Tech Stack
- Python
- FastAPI
- MongoDB

## Project Plan
- [ ] Environment Setup (1h15min)
	- [x] Virtual Environment (15min)
		- [x] FastAPI & uvicorn, pymongo, lib for scraping (BeautifulSoup/Scrapy)
	- [ ] Dockerfiles and compose (45min)
	- [ ] Initial FastAPI config (15min)
- [ ] Create the scraper (3h45min)
	- [x] Identify patterns on the news article webpage for the fields (title, date, news_provided_by, content) (20min)
	- [ ] Write a scraping script to work with one URL (2h)
	- [ ] Implement some error handling to deal with connection errors and missing fields (40min)
	- [ ] Implement unit tests to make sure that the scraper is working properly (45min)
- [ ] Clean and format the data (1h)
	- [ ] Create a function to clean and format the data scraped from the newswire (30min)
	- [ ] Add some validations to ensure data correctness (15min)
	- [ ] Write unit tests (15min)
- [ ] Mongo DB (1h15min)
	- [ ] Create schemas to define how to store the data (15min)
	- [ ] Define the indexes based on the query needs (15min)
	- [ ] Create the function to insert the data (15min)
	- [ ] Define how to avoid duplicated data, probably create a unique index on some identifier from the article (30min)
- [ ] Setup FastAPI (1h)
	- [ ] Define the endpoint structure for FastAPI (30min)
	- [ ] Create the query endpoint to filter data using a variety of fields (30min)
- [ ] Define monitoring (45min)
	- [ ] Define how to monitor the scraping tasks (15min)
	- [ ]Write the monitoring system (30min)
- [ ] Test the whole system(2h)
	- [ ] Create some integration and unit tests to make sure everything is working well (2h)
- [ ] Write the documentation about the project (1h)
	- [ ] Add missing parts that were not added during the coding phase (1h)
- **Total:** 12 hours to complete the required code
- **Bonus 1:** 1h30min
- **Bonus 2:** 1h30min
- **Total:** 15h

## Project Setup
### Dependencies
You might need to take a look at [Scrapy platform specific installation requirements](https://docs.scrapy.org/en/latest/intro/install.html#platform-specific-installation-notes)

### Requirements
Run the following command to install requirements:

```bash
# if you're on a local environment
pip install -r requirements/local.txt
# if you're on production
pip install -r requirements/production.txt
```

## Scraper
### Selectors
- Title: `response.xpath("//h1/text()").get().strip()`
- Date: `response.xpath('//p[@class="mb-no"]/text()').get()`
- Provided By: `response.xpath('//p[@class="mb-no"]/../a/strong/text()').get().strip()`
Content:
```python
all_data = response.xpath('//article/section//div[@class="col-lg-10 col-lg-offset-1"]')
for paragraph in all_data.xpath('.//p | .//b'):
	texts = paragraph.xpath('.//text()').getall()
	text_formatted = ''.join([text for text in texts]).strip()
	print(text_formatted)
```
