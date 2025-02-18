#import libraries
from bs4 import BeautifulSoup
import requests

#connect to website
url = 'https://en.wikipedia.org/wiki/World_Tourism_rankings'
page = requests.get(url)
soup = BeautifulSoup(page.text, 'html')

#Verifying that I am pulling text from the right table and what the table is called in HTML
soup.find_all('table')[1]
soup.find_all('table')[3]
soup.find_all('table')[4]
soup.find_all('table')[5]
soup.find_all('table')[6]

#Pull text from table called Wikitable sortable
soup.find('table', class_='wikitable sortable')

#creating 6 tables 
table1 = soup.find_all('table')[1]
table2 = soup.find_all('table')[3]
table3 = soup.find_all('table')[4]
table4 = soup.find_all('table')[5]
table5 = soup.find_all('table')[6]
table6 = soup.find_all('table')[7]

#pull the column titles('th') from each table and import them to header1-6
header1 = table1.find_all('th')[0:6]
header2 = table2.find_all('th')[0:7]
header3 = table3.find_all('th')[0:8]
header4 = table4.find_all('th')[0:7]
header5 = table5.find_all('th')[0:8]
header6 = table6.find_all('th')[0:7]

#Clean the Header titles that were pulled from the html script to make more readable and remove spaces and/or blanks
import re
table1_titles = [title.text.strip() for title in header1]
table2_titles = [title.text.strip().replace('\n',' ') for title in header2]
table3_titles = [title.text.strip() for title in header3]
table4_titles = [title.text.strip() for title in header4]
table5_titles = [title.text.strip() for title in header5]
table6_titles = [title.text.strip() for title in header6]

#creating a new empty data table structure using pandas library for each table
import pandas as pd
df = pd.DataFrame(columns = table1_titles)
df2 = pd.DataFrame(columns = table2_titles)
df3 = pd.DataFrame(columns = table3_titles)
df4 = pd.DataFrame(columns = table4_titles)
df5 = pd.DataFrame(columns = table5_titles)
df6 = pd.DataFrame(columns = table6_titles)

#pull the row titles/text('tr') from each table and import them to column1-6
column1_data = soup.find_all('tr')[2:12]
column2_data = table2.find_all('tr')[1:11]
column3_data = table3.find_all('tr')[1:11]
column4_data = table4.find_all('tr')[1:11]
column5_data = table5.find_all('tr')[1:11]
column6_data = table6.find_all('tr')[1:11]


#using for loops to fill in the data that is 
for row in column1_data:
    row_data = row.find_all('td')
    individual_row_data = [data.text.strip() for data in row_data]
    length = len(df)
    df.loc[length] = individual_row_data
    
for row in column2_data:
    row_data2 = row.find_all('td')
    individual_row_data2 = [data.text.strip() for data in row_data2]     
    length2 = len(df2)
    df2.loc[length2] = individual_row_data2

for row in column3_data:
    row_data3 = row.find_all('td')
    individual_row_data3 = [data.text.strip() for data in row_data3]  
    length3 = len(df3)
    df3.loc[length3] = individual_row_data3

for row in column4_data:
    row_data4 = row.find_all('td')
    individual_row_data4 = [data.text.strip() for data in row_data4]  
    length4 = len(df4)
    df4.loc[length4] = individual_row_data4

for row in column5_data:
    row_data5 = row.find_all('td')
    individual_row_data5 = [data.text.strip() for data in row_data5]  
    length5 = len(df5)
    df5.loc[length5] = individual_row_data5

for row in column6_data:
    row_data6 = row.find_all('td')
    individual_row_data6 = [data.text.strip() for data in row_data6]  
    length6 = len(df6)
    df6.loc[length6] = individual_row_data6
