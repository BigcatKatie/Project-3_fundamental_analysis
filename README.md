# Summary of the Data visualization project and Fundamental Analysis #

# To summarize the approach of this project, I began with data fetching from the FMP API, followed by data cleaning and preparation, created visualization using Chart.js. Overall, transformed raw data into visual analysis, tried to answered the three questions raised in the project planning stage: financial health, long-term growth potential, and the balance between income generation and financial stability. 

# To gauge financial health, radar charts highlighted the relative strength of each company's balance sheet, focusing on debt management and liquidity. For instance, companies like FSLR and ENPH showed strong financial health with low debt-to-equity ratios and high-interest coverage, indicating robust balance sheets. 

# The long-term growth potential was evaluated through line charts showing trends in revenue and net income growth over a five-year period. Companies such as ENPH and FSLR exhibited consistent growth in revenue and net income, suggesting they are well-positioned for future expansion within the clean energy sector.

# Finally, the balance between income generation and financial stability was analyzed using bubble charts to compare dividend yield and free cash flow per share. Companies like BEPC demonstrated a favorable balance with steady cash flows and reasonable debt levels, making them attractive for income-focused investors.

# Project 3 proposal: Data Visualization Stream
	# Topic: Fundamental Analysis on 10 Clean Energy companies
	# Dataset: from Financial Modelling Prep, a free stock market and financial statement API (only for US listed companies)
               # Website: https://site.financialmodelingprep.com/developer/docs
	# Objective: answer the following three questions using fundamental analysis, supported by data visualization
		# 1. How does financial health vary among the selected clean energy companies?
		# 2. Which Companies in the clean energy sector are positioned for Long-term growth?
		# 3. Which clean energy companies offer the best balance between income generation and financial stability?

# Part 1: Data Acquisition

# Data Acquisition: originally used yfinance API to fetch 5 years of data for each of the 10 Canadian companies from yahoo finance, however, turned out that it can only fetch the most recent (TTM) financial metrics. So switched to Financial Modeling Prep API, since it only has stock data for US listed companies so I picked 10 largest US clean energy companies, and fetched 5 years of key metrics using FMP API.
	# Function to Parse JSON Data
	# Initialize the FMPDataFetcher class to fetch data from FMP API for a list of stock symbols over a specified time range
	# Use the fetch and save all method to iterate through each stock symbol and fetches the key metrics for each year
	# get_key_metrics method constructs a URL to fetch key metrics for a given stock, then parses the JSON data and converts it into a Pandas dataframe.
	# Saves the Pandas dataframe to JSON files
	# Provide a list of stock symbols for which data will be fetched
	# Define the time range for which data will be fetched
	# Creates an instance of the ‘FMPDataFetcher’ class with the symbols, time range, and API Key
	# Calls the method to fetch and save the data for each stock symbol in the list

# Part 2: Data Preparation

# Step 1: Combing key metrics files into a single dataframe
	# Function loads JSON files for the given symbols and years, combining them into a singer Pandas dataframe
	# Initialize an empty dataframe

# Step 2: Data cleaning 
	# Drop columns with more than 50% missing values
	# Identify numeric columns only
	# Fill remaining missing values with the median of numeric columns
	# Ensure all numeric columns are of numeric type
	# Drop any rows with missing values that couldn’t be filled

# Step 3: Filter the Columns of Metrics needed for analysis by only keeping the columns that needed for the subsequent fundamental analysis 

# Step 4: Prepare datasets for Fundamental analysis
	# Question 1: Financial Health Analysis
	# Select relevant columns for financial health analysis
	# Convert DataFrame to a format suitable for Chart.js (radar chart format)
	# Metrics (excluding 'symbol' and 'calendarYear')
	# Filter out the symbol and calendarYear and calculate the mean for numeric columns only
	# Prepare the final JSON structure
	# Save to JSON file

	# Question 2: Long term growth analysis
	# Prepare data for line chart showing Revenue and Net Income Per Share Growth over multiple years, create a dataframe containing related columns
	# A list of dictionaries prepared for generating a line chart in Chart.js, extract and prepare the revenue and net income data for each symbol
	# Save to JSON file
	# Prepare data for scatter plot showing ROIC vs. ROE
	# A list of dictionaries prepared for generating a scatter plot in Chart.js, Calculate the mean values of ROIC and ROE for each symbol
	# Save to JSON file

	Question 3: Income Generation vs Financial Stability
	# Prepare data for bubble chart showing Dividend Yield vs. Free Cash Flow Per Share
	# A list of dictionaries prepared for generating a bubble chart in Chart.js, Calculate the mean values for each symbol.
	# Save to JSON file
	# Prepare data for bar chart showing Payout Ratio and Current Ratio, A dictionary structure for generating a bar chart in Chart.js, containing labels and 	datasets, Calculate the mean values for each symbol.
	# Save to JSON file

# Part 3: Data Visualization

	# HTML is used to structure a web page for visualizing datasets related to clean energy companies. The page includes multiple ‘canvas’ elements, each 	serving as a placeholder for different types of charts (radar, line, scatter, bubble, and bar charts). 

	# JavaScript, with the help of the Chart.js library, was employed to create there interactive charts. The datasets were predefined in JavaScript as objects 	containing data points for various financial metrics.

	# Event listeners and functions were implemented to allow user interaction, such as selecting a company from a dropdown menu

# Resources for the project:
#https://site.financialmodelingprep.com/developer/docs
#https://www.chartjs.org/docs/latest/samples/information.html
#https://github.com/FinancialModelingPrepAPI/Financial-Modeling-Prep-API
#https://github.com/chartjs/Chart.js
#https://pandas.pydata.org/docs/index.html
#https://stackoverflow.com/questions/44990517/displaying-json-data-in-chartjs
#http://microbuilder.io/blog/2016/01/10/plotting-json-data-with-chart-js.html
