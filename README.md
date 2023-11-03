# Amazon-Web-Scrapper

Amazon-Web_Scrapping project was a project I carried out with speicial Python web scrapping librarires.
I used Python to pull out the price of an amazon shirt, the posted date and the rating for the day.

## Special Python Libraries in this Project

```
  Python

from bs4 import BeautifulSoup
import requests
import smtplib
import datetime

   ```

- Automation of the scrapping Project using this codes



```
  Python
#automate it

def check_price():
    url ='https://www.amazon.com/Funny-Data-Systems-Business-Analyst/dp/B07FNW9FGJ/ref=sr_1_3?dchild=1&keywords=data%2Banalyst%2Btshirt&qid=1626655184&sr=8-3&customId=B0752XJYNL&th=1%27'

    headers = {"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/116.0.0.0 Safari/537.36 Edg/116.0.1938.76", "Accept-Encoding":"gzip, deflate", "Accept":"text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8", "DNT":"1","Connection":"close", "Upgrade-Insecure-Requests":"1"}
    
    page = requests.get(url, headers = headers)

    soup1 = BeautifulSoup(page.content, 'html.parser')

    soup2 = BeautifulSoup(soup1.prettify(), 'html.parser')

    title = soup2.find(id = 'productTitle').get_text()

    price = soup2.find(class_ = "a-price aok-align-center reinventPricePriceToPayMargin priceToPay").get_text().strip()
    
    import datetime

    today = datetime.date.today() 
    
    import csv


    header = ['Title', 'price', 'review', 'Date']

    data = [title, price, review, today]
    
    with open('Amazonscrapper.csv', 'a+', newline = '', encoding = 'UTF8') as f:
         writer = csv.writer(f)
         writer.writerow(data)
         writer.writerow(review)
 ```

- Importing the scrapped data into CSV

```
Python

import csv

header = ['Title', 'price', 'review', 'Date']
data = [title, price, review, today]
type(data)

with open('Amazonscrapper.csv', 'w', newline = '', encoding = 'UTF8') as f:
    writer = csv.writer(f)
    writer.writerow(header)
    writer.writerow(data)
    writer.writerow(review)
```
