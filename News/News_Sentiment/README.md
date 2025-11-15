# News Sentiment Pipeline

### This code collected seven days' worth of unstructured news-article data and separated it into daily output files for future analysis.

### ***Code Outline***
* Create News_Sentiment folder, prepare README.md, set working directory, record run date
* Configure headless ChromeDriver (webdriver-manager) and start Selenium
* Load BBC News, collect deduplicated /news/ links (limit applied)
* For each URL: fetch HTML via Selenium with requests fallback
* Extract article text (BeautifulSoup selectors, newspaper3k fallback), clean and filter short items
* Build DataFrame with title, url, text, run_date, and text length
* Load NLTK sentence tokenizer and HF sentiment pipeline (DistilBERT on CPU)
* Split articles into sentences, run batched sentence-level sentiment, convert to signed scores
* Expand sentence results to a long table and save sentences_all_articles.csv
* Save per-article CSVs and top-sentences text files under ./sentences/
* Aggregate per-article polarity counts and mean score, save articles_sentiment_summary.csv and articles_sentiment.csv
* Write human-readable articles_texts.txt archive
* Log fetch/parse/sentiment errors, suppress HF symlink warning if set, and quit Selenium driver
* File aggregation and histogram visualization


### ***Link***
[BBC News Articles](https://www.bbc.com/news) 


### ***Directory***
| Column Name         | Description                                                                          | Data Type |
|:--------------------|:-------------------------------------------------------------------------------------|:---------:|
| article_index       | Unique identifier for each article                                                   | Integer   |
| title               | Title of the article                                                                 | String    |
| url                 | URL link to the article                                                              | String    |
| avg_label           | Average sentiment label (e.g., POSITIVE, NEGATIVE)                                   | String    |
| avg_score           | Average absolute signed score (0-1)                                                  | Float     |
| num_sentences       | Total number of sentences in the article                                             | Integer   |
| sentence            | A specific sentence extracted from the article                                       | String    |
| sent_label          | Sentiment label for the specific sentence (e.g., POSITIVE, NEGATIVE)                 | String    |
| sent_score          | Confidence score (0–1)                                                               | Float     |
| sent_value          | A numerical representation of the sentence score, possibly reflecting its sentiment  | Float     |


### ***Project Setup & Run Instructions***
|Action	                                                |Command / Notes                                                                                           |
|:------------------------------------------------------|:---------------------------------------------------------------------------------------------------------|
|Clone or fork the repo                                 |git clone https://github.com/ragogzheyan/Course_Work/tree/main/News                                       |
|Create & activate virtualenv (Git Bash)                |python -m venv venv         source venv/Scripts/activate                                                  | 
|Upgrade pip                                            |python -m pip install --upgrade pip                                                                       |
|Install from requirements.txt	                        |pip install -r requirements.txt                                                                           |
|Install packages manually (if no requirements.txt)  	|pip install selenium webdriver-manager beautifulsoup4 newspaper3k nltk transformers pandas numpy requests | 
|NLTK tokenizer setup (one-time)	                    |python -c "import nltk; nltk.download('punkt')"                                                           |
|Run the pipeline (Jupyter notebook)	                |jupyter lab or jupyter notebook — then open and run the project's notebook (e.g., run_pipeline.ipynb)     |
|Deactivate virtualenv (Git Bash)	                    |deactivate                                                                                                |


### ***AI tools & Provenance(APA)***
**Model**: GPT-5((OpenAI; accessed 2025-11-07-2025-11-14) 
**Role**: Assisted with Selenium configuration, rule generation, and sentence-level sentiment processing. 
**Prompts & outputs**: Archived: not available — prompts and important AI outputs are summarized below. 
**Settings**: model=gpt-5 

#### ***Selenium Fetch & Extraction***  
**Selenium config**: headless ChromeDriver via webdriver-manager; short wait (time.sleep(1)) after driver.get() to allow JS rendering. 
**Fetch logic**: Try Selenium first; if page_source length < 500 or Selenium errors, fallback to requests with timeout=8. 
**Extraction logic**: BeautifulSoup selectors: article, [role='main'], .story-body, .ssrcss-uf6wea-RichTextComponentWrapper; accept only extracts >200 chars — otherwise fallback to newspaper3k parsing. 
**Failure behavior**: On fetch/parse exceptions return empty string; errors. 
