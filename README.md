## Wikipedia-Web-Scraping-Project



# Wikipedia Web Scraping Project

Welcome to the Wikipedia Web Scraping Project repository! In this project, we will be utilizing Object-Oriented Programming (OOP) principles to scrape a static website on Wikipedia. We'll extract data using the BeautifulSoup and Requests libraries in Python.

## Table of Contents

- [Project Overview](#project-overview)
- [Technologies Used](#technologies-used)
- [Web Scraping Process](#web-scraping-process)
  - [Importing Modules](#importing-modules)
  - [Downloading Webpage](#downloading-webpage)
  - [Extracting Table Data](#extracting-table-data)
  - [Cleaning and Transforming Data](#cleaning-and-transforming-data)
  - [Saving the Dataset](#saving-the-dataset)
- [Getting Started](#getting-started)
- [Contributors](#contributors)
- [License](#license)

## Project Overview

The goal of this project is to demonstrate web scraping techniques using Python. We'll focus on scraping a static webpage from Wikipedia, specifically targeting a table containing information about the largest companies. By extracting, cleaning, and transforming the data, we aim to create a clean and structured dataset that can be saved for analysis.

## Technologies Used

- Python
- BeautifulSoup
- Requests
- Pandas

## Web Scraping Process

### Importing Modules

We begin by importing the necessary Python libraries, including BeautifulSoup, Requests, and Pandas, which will facilitate the web scraping process and data manipulation.

```python
import requests
from bs4 import BeautifulSoup
import pandas as pd
```

### Downloading Webpage

We use the Requests library to download the webpage's contents in text format. This downloaded content is stored in a variable named `response`.

```python
url = 'https://en.wikipedia.org/wiki/List_of_largest_companies_by_revenue'
response = requests.get(url).text
```

### Extracting Table Data

To extract the desired table, we identify its class name using the browser's inspect tool. In this case, the class is `'wikitable sortable'`. We create a BeautifulSoup object using the downloaded content and then extract the headers and rows from the table.

```python
soup = BeautifulSoup(response, 'html.parser')
table = soup.find('table', {'class': 'wikitable sortable'})

headers = [header.text.strip() for header in table.find_all('th')]
rows = []
for row in table.find_all('tr')[1:]:
    row_data = [cell.text.strip() for cell in row.find_all(['td', 'th'])]
    rows.append(row_data)
```

### Cleaning and Transforming Data

After obtaining the table data, we clean and transform it. We convert columns containing numeric values to integer using `.astype('int')`. We also remove unnecessary characters such as commas and percent signs from relevant columns using `.str.replace(',', '')` and `.str.replace('%', '')`.

```python
df = pd.DataFrame(rows, columns=headers)
df['Revenue (USD millions)'] = df['Revenue (USD millions)'].str.replace(',', '').astype(int)
df['Employees'] = df['Employees'].str.replace(',', '').astype(int)
df['Revenue growth'] = df['Revenue growth'].str.replace('%', '').astype(int)
```

### Saving the Dataset

The cleaned and structured data is saved as a CSV file. This file can then be used for analysis, visualization, and further exploration.

```python
df.to_csv('largest_companies_data.csv', index=False)
```

## Getting Started

1. Clone or download this repository to your local machine.
2. Ensure you have Python installed along with the required libraries (`BeautifulSoup`, `Requests`, and `Pandas`).
3. Open the main script and execute it to perform the web scraping and data cleaning.
4. The resulting cleaned dataset will be saved as a CSV file.

## Contributors

- [Your Name]

Feel free to contribute to this project by enhancing the code, improving the documentation, or suggesting additional features.

## License

This project is licensed under the [MIT License](LICENSE). Feel free to use, modify, and distribute the code as per the terms of the license.

Enjoy exploring the world of web scraping with Wikipedia data!

---
```

Please replace `[Your Name]` with your actual name and update any other placeholders as needed.
