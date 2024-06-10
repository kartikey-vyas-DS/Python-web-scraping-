# Web Scraping Project

This project demonstrates how to scrape a personal website to extract project details using Python's `requests` and `BeautifulSoup` libraries. The scraped data includes project titles, links, and descriptions.

## Overview

The script fetches the HTML content of the webpage, parses it using `BeautifulSoup`, and extracts information about the projects listed on the page. The extracted data is then structured into a list of dictionaries for further use.

## Installation

To run this project, you need to have Python installed. Additionally, you need to install the required libraries:

```bash
pip install requests
pip install beautifulsoup4
```

- Here's the code used for scraping the website:
    import requests
    from bs4 import BeautifulSoup

    # URL of the website to scrape
    url = "https://kartikey-vyas-ds.github.io/"

    # Fetch the HTML content of the page
    response = requests.get(url)

    # Check if the request was successful
    if response.status_code == 200:
        html_content = response.text
        print("HTML content fetched successfully!")
    else:
        print(f"Failed to fetch the page. Status code: {response.status_code}")

    # Parse the HTML content using BeautifulSoup
    soup = BeautifulSoup(html_content, 'html.parser')

    projects = []
    for link in soup.find_all('h3', class_='heading'):
        a_tag= link.find('a')
        href = a_tag.get('href')
        title = a_tag.text.strip()

        p_tag = link.find_next_sibling('p',class_= 'justified-text')
        description= p_tag.text if p_tag else ''
        projects.append({
            'heading':title,
            'Links': href,
            'Description':description
        })

    projects
### Here are the projects extracted by the script:
- Target Business Case study using SQL: Analyzed this Ecommerce company's data to understand Sales fluctuations over time and ways to boost sales.
- Data Analysis on Car features's Impact on prices using Advanced Excel: Operated advanced Excel techniques to analyze a dataset ('Car Features and MSRP') comprising over 11,000 data points. Conducted EDA to identify key factors driving consumer behaviour and profitability trends in the automotive industry.
- Tableau Dashboard on IMDB Movie Dataset: Designed a Tableau dashboard for a dataset on IMDB Scores, identified most profit making movies, highest budget, best directors and impact of Users and Critique reviews on IMDB Scores.
- Traffic Volume forecasting using Python & ML: Demonstrated expertise in data preprocessing, feature engineering, and model optimization, culminating in significant improvement in model performance.
- Stock Market Forecasting as a Classification Model: Imported YFinance to gather real-time data on selected stocks and indexes. Generated technical indicators and developed a custom "rsi package" (RSI) values, defined function for closing ratio and trend identification across 5 time frames, further applied several models to solve the Classification Problem.


## Screenshots
- Here are some screenshots of the website:

- here's how the scraped section looks like 
![alttext]['ss1.png']

- i inspected the Html content to read Tags and classes using "Inspect" in chrome browser
![alttext]['ss2.png']



## Contact

If you have any feedback/are interested in collaborating, please reach out to me at [<img height="40" src="https://img.icons8.com/color/48/000000/linkedin.png" height="40em" align="center" alt="Follow Kartikey on LinkedIn" title="Follow Kartikey on LinkedIn"/>](https://www.linkedin.com/in/kartikey-vyas-2a29b9273) &nbsp; <a href="mailto:kvsvyas@gmail.com"> <img height="40" src="https://img.icons8.com/fluent/48/000000/gmail.png" align="center" />





## License

[MIT](https://choosealicense.com/licenses/mit/)

