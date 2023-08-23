# Webscraping-using-beautifulsoup

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

