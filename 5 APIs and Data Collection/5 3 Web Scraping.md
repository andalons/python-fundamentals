# 5.3 Web Scraping

## Introduction to web scraping

Web scraping, also known as web harvesting or web data extraction, is the process of extracting information from websites or web pages. It involves automated retrieval of data from web sources. People use it for various applications such as data analysis, mining, price comparison, content aggregation, and more.

## How web scraping works

- **HTTP request**
The process typically begins with an HTTP request. A web scraper sends an HTTP request to a specific URL, similar to how a web browser would when you visit a website. The request is usually an HTTP GET request, which retrieves the web page's content.
- **Web page retrieval**
The web server hosting the website responds to the request by returning the requested web page's HTML content. This content includes the visible text and media elements and the underlying HTML structure that defines the page's layout.
- **HTML parsing**
Once the HTML content is received, you need to parse the content. Parsing involves breaking down the HTML structure into components, such as tags, attributes, and text content. You can use BeautifulSoup in Python. It creates a structured representation of the HTML content that can be easily navigated and manipulated.
- **Data extraction**
With the HTML content parsed, web scrapers can now identify and extract the specific data they need. This data can include text, links, images, tables, product prices, news articles, and more. Scrapers locate the data by searching for relevant HTML tags, attributes, and patterns in the HTML structure.
- **Data transformation**
Extracted data may need further processing and transformation. For instance, you can remove HTML tags from text, convert data formats, or clean up messy data. This step ensures the data is ready for analysis or other use cases.
- **Storage**
After extraction and transformation, you can store the scraped data in various formats, such as databases, spreadsheets, JSON, or CSV files. The choice of storage format depends on the specific project's requirements.
- **Automation**
In many cases, scripts or programs automate web scraping. These automation tools allow recurring data extraction from multiple web pages or websites. Automated scraping is especially useful for collecting data from dynamic websites that regularly update their content.

## HTML structure

![Captura de pantalla 2024-12-19 a las 15.49.59.png](Captura_de_pantalla_2024-12-19_a_las_15.49.59.png)

Hypertext markup language (HTML) serves as the foundation of web pages. Understanding its structure is crucial for web scraping.

- `<html>` is the root element of an HTML page.
- `<head>` contains meta-information about the HTML page.
- `<body>` displays the content on the web page, often the data of interest.
- `<h3>` tags are type 3 headings, making text larger and bold, typically used for player names.
- `<p>` tags represent paragraphs and contain player salary information.

### Composition of an HTML tag

HTML tags define the structure of web content and can contain attributes.

- An HTML tag consists of an opening (start) tag and a closing (end) tag.
- Tags have names (`<a>` for an anchor tag).
- Tags may contain attributes with an attribute name and value, providing additional information to the tag.

### HTML document tree

You can visualize HTML documents as trees with tags as nodes.

- Tags can contain strings and other tags, making them the tag's children.
- Tags within the same parent tag are considered siblings.
- For example, the `<html>` tag contains both `<head>` and `<body>` tags, making them descendants of `<html` but children of `<html>`. `<head>` and `<body>` are siblings.

![Captura de pantalla 2024-12-19 a las 15.50.27.png](Captura_de_pantalla_2024-12-19_a_las_15.50.27.png)

### HTML tables

HTML tables are essential for presenting structured data.

- Define an HTML table using the `<table>` tag.
- Each table row is defined with a `<tr>` tag.
- The first row often uses the table header tag, typically `<th>`.
- The table cell is represented by `<td>` tags, defining individual cells in a row.

![Captura de pantalla 2024-12-19 a las 15.51.11.png](Captura_de_pantalla_2024-12-19_a_las_15.51.11.png)

## Web Scraping Tables using Pandas

The Pandas library in Python contains a function `read_html()` that can be used to extract tabular information from any web page.

Consider the following example:

Let us assume we want to extract the list of the largest banks in the world by market capitalization, from the following link:

`URL = 'https://en.wikipedia.org/wiki/List_of_largest_banks'`

We may use `pandas.read_html()` function in python to extract all the tables in the web page directly. 

We can see that the required table is the first one in the web page. 

We may execute the following lines of code to extract the required table from the web page. 

```python
import pandas as pd
URL = 'https://en.wikipedia.org/wiki/List_of_largest_banks'
tables = pd.read_html(URL)
df = tables[0]print(df)
```

This will extract the required table as a dataframe `df`. The output of the print statement would look as shown below.

![Captura de pantalla 2024-12-20 a las 7.49.22.png](Captura_de_pantalla_2024-12-20_a_las_7.49.22.png)

![A snapshot of the webpage](Captura_de_pantalla_2024-12-20_a_las_7.46.30.png)

A snapshot of the webpage

Although convenient, this method comes with its own set of limitations.

Firstly, web pages may have content saved in them as tables but they may not appear as tables on the web page. For instance, consider the following URL showing the list of countries by GDP (nominal).

`URL = 'https://en.wikipedia.org/wiki/List_of_countries_by_GDP_(nominal)'`

The images on the web page are also saved in tabular format:

![Captura de pantalla 2024-12-20 a las 7.51.10.png](Captura_de_pantalla_2024-12-20_a_las_7.51.10.png)

![A closer look at table 3 in the image shown above indicates that there are many hyperlink texts which are also going to be treated as information by the pandas function.](Captura_de_pantalla_2024-12-20_a_las_7.52.14.png)

A closer look at table 3 in the image shown above indicates that there are many hyperlink texts which are also going to be treated as information by the pandas function.

Secondly, the contents of the tables in the web pages may contain elements such as hyperlink text and other denoters, which are also scraped directly using the pandas method. This may lead to a requirement of further cleaning of data.

We can extract the table using the code shown below.

```python
import pandas as pd
URL = 'https://en.wikipedia.org/wiki/List_of_countries_by_GDP_(nominal)'
tables = pd.read_html(URL)
df = tables(2) # the required table will have index 2
print(df)
```

The output of the print statement is shown below.

![Note that the hyperlink texts have also been retained in the code output.](Captura_de_pantalla_2024-12-20_a_las_7.53.31.png)

Note that the hyperlink texts have also been retained in the code output.

It is further prudent to point out, that this method exclusively operates only on tabular data extraction. BeautifulSoup library still remains the default method of extracting any kind of information from web pages.

## Web scraping tools / libraries

In the field of data science, web scraping plays an integral role. It involves extracting information from web pages using Python an it is used for various purposes such as:

1. **Data Collection:** Web scraping is a primary method of collecting data from the internet. This data can be used for analysis, research, etc.
2. **Real-time Application:** Web scraping is used for real-time applications like weather updates, price comparison, etc.
3. **Machine Learning:** Web scraping provides the data needed to train machine learning models.

Python provides several libraries for web scraping:

1. **BeautifulSoup:** BeautifulSoup is a Python library used for web scraping purposes to pull the data out of HTML and XML files. It creates a parse tree from page source code that can be used to extract data in a hierarchical and more readable manner.

```python
from bs4 import BeautifulSoup
import requests

URL = "http://www.example.com"
page = requests.get(URL)
soup = BeautifulSoup(page.content, "html.parser")
```

1. **Scrapy:** Scrapy is an open-source and collaborative web crawling framework for Python. It is used to extract the data from the website.

```python
import scrapy

class QuotesSpider(scrapy.Spider):    
	name = "quotes"    
	start_urls = ['http://quotes.toscrape.com/tag/humor/',]    
	def parse(self, response):        
			for quote in response.css('div.quote'):
					yield {'quote': quote.css('span.text::text').get()}
```

1. **Selenium:** Selenium is a tool used for controlling web browsers through programs and automating browser tasks.

```python
from selenium import webdriver

driver = webdriver.Firefox()
driver.get("http://www.example.com")
```

## Fetching and parsing HTML with Requests and Beautiful Soup

**Beautiful Soup** is a Python library for pulling data out of HTML and XML files, we will focus on HTML files. This is accomplished by representing the HTML as a set of objects with methods used to parse the HTML. We can navigate the HTML as a tree, and/or filter out what we are looking for.

To start web scraping, you need to fetch the HTML content of a webpage and parse it using Beautiful Soup. Here's a step-by-step example:

```python
import requests 
from bs4 import BeautifulSoup

#Specify the URL of the webpage you want to scrape
url = 'https://en.wikipedia.org/wiki/IBM'

# Send an HTTP GET request to the webpage
response = requests.get(url)

# Store the HTML content in a variable
html_content = response.text

# Create a BeautifulSoup object to parse the HTML
soup = BeautifulSoup(html_content, 'html.parser')

# Display a snippet of the HTML content
print(html_content[:500])
```

### Navigating the HTML structure

BeautifulSoup represents HTML content as a tree-like structure, allowing for easy navigation. You can use methods like `find_all` to filter and extract specific HTML elements. For example, to find all anchor tags () and print their text:

```python
# Find all <a> tags (anchor tags) in the HTML
links = soup.find_all('a') 

# Iterate through the list of links and print their text
for the link in links:
    print(link.text)
```

Consider the following HTML: 

```html
%%html
<!DOCTYPE html>
<html>
<head>
<title>Page Title</title>
</head>
<body>
<h3><b id='boldest'>Lebron James</b></h3>
<p> Salary: $ 92,000,000 </p>
<h3> Stephen Curry</h3>
<p> Salary: $85,000, 000 </p>
<h3> Kevin Durant </h3>
<p> Salary: $73,200, 000</p>
</body>
</html>
```

```python
from bs4 import BeautifulSoup # this module helps in web scrapping.
import requests  # this module helps us to download a web page

html="<!DOCTYPE html><html><head><title>Page Title</title></head><body><h3><b id='boldest'>Lebron James</b></h3><p> Salary: $ 92,000,000 </p><h3> Stephen Curry</h3><p> Salary: $85,000, 000 </p><h3> Kevin Durant </h3><p> Salary: $73,200, 000</p></body></html>"
soup = BeautifulSoup(html, 'html5lib')
```

- **Tags**
    
    Let's say we want the title of the page and the name of the top paid player. We can use the `Tag`. The `Tag` object corresponds to an HTML tag in the original document, for example, the tag title.
    
    ```python
    tag_object**=**soup.title
    print("tag object:",tag_object) #output: tag object: <title>Page Title</title>
    print("tag object type:",type(tag_object))#output: tag object type: <class 'bs4.element.Tag'>
    ```
    
    If there is more than one `Tag` with the same name, the first element with that `Tag` name is called. 
    
    ```python
    tag_object=soup.h3
    tag_object # output: <h3><b id="boldest">Lebron James</b></h3>
    ```
    
- **Children, parents and siblings**
    
    ```python
    tag_child=tag_object.b
    tag_child #output: <b id="boldest">Lebron James</b>
    
    tag_parent=parent_tag=tag_child.parent
    parent_tag #output: <h3><b id="boldest">Lebron James</b></h3>
    
    sibling_1=tag_object.next_sibling
    sibling_1 #output: <p> Salary: $ 92,000,000 </p>
    
    sibling_2=sibling_1.next_sibling
    sibling_2 #output: <h3> Stephen Curry</h3>
    ```
    
- **HTML attributes**
    
    If the tag has attributes, the tag `id="boldest"` has an attribute `id` whose value is `boldest`. 
    
    ```python
    # You can access a tag’s attributes by treating the tag like a dictionary:
    tag_child['id'] #output: 'boldest'
    
    # You can access that dictionary directly as attrs:
    tag_child.attrs #output: {'id': 'boldest'}
    
    # We can also obtain the content of the attribute of the tag using the Python get() method.
    tag_child.get('id') #output: 'boldest'
    ```
    
- **Navigable String**
    
    A string corresponds to a bit of text or content within a tag. Beautiful Soup uses the `NavigableString` class to contain this text. In our HTML we can obtain the name of the first player by extracting the string of the `Tag` object `tag_child` as follows:
    
    ```python
    tag_string=tag_child.string
    tag_string #output: 'Lebron James'
    
    type(tag_string) #output: bs4.element.NavigableString
    ```
    
    A NavigableString is similar to a Python string or Unicode string. To be more precise, the main difference is that it also supports some `BeautifulSoup` features. We can convert it to string object in Python:
    
    ```python
    unicode_string = str(tag_string)
    
    type(unicode_string) #output: str
    ```
    

### `find_all()` **method**

Consider the following HTML: 

```html
%%html
<table>
  <tr>
    <td id='flight' >Flight No</td>
    <td>Launch site</td> 
    <td>Payload mass</td>
   </tr>
  <tr> 
    <td>1</td>
    <td><a href='https://en.wikipedia.org/wiki/Florida'>Florida</a></td>
    <td>300 kg</td>
  </tr>
  <tr>
    <td>2</td>
    <td><a href='https://en.wikipedia.org/wiki/Texas'>Texas</a></td>
    <td>94 kg</td>
  </tr>
  <tr>
    <td>3</td>
    <td><a href='https://en.wikipedia.org/wiki/Florida'>Florida<a> </td>
    <td>80 kg</td>
  </tr>
</table>
```

```python
table="<table><tr><td id='flight'>Flight No</td><td>Launch site</td> <td>Payload mass</td></tr><tr> <td>1</td><td><a href='https://en.wikipedia.org/wiki/Florida'>Florida<a></td><td>300 kg</td></tr><tr><td>2</td><td><a href='https://en.wikipedia.org/wiki/Texas'>Texas</a></td><td>94 kg</td></tr><tr><td>3</td><td><a href='https://en.wikipedia.org/wiki/Florida'>Florida<a> </td><td>80 kg</td></tr></table>"
table_bs = BeautifulSoup(table, 'html5lib')
```

The `find_all()` method looks through a tag’s descendants and retrieves all descendants that match your filters.

**Sintaxis**: `find_all(name, attrs, recursive, string, limit, **kwargs)`

- **`name`**
    
    When we set the `name` parameter to a tag name, the method will extract all the tags with that name and its children:
    
    ```python
    table_rows=table_bs.find_all('tr')
    table_rows 
    ```
    
    ![Captura de pantalla 2024-12-20 a las 10.05.13.png](Captura_de_pantalla_2024-12-20_a_las_10.05.13.png)
    
    ```python
    first_row =table_rows[0]
    first_row #output: <tr><td id="flight">Flight No</td><td>Launch site</td> <td>Payload mass</td></tr>
    
    # The type is Tag
    print(type(first_row))#output: <class 'bs4.element.Tag'>
    
    # To obtain the child: 
    first_row.td #output: <td id="flight">Flight No</td>
    ```
    
    If we iterate through the list, each element corresponds to a row in the table:
    
    ```python
    for i,row in enumerate(table_rows):
        print("row",i,"is",row)
    ```
    
    ![Captura de pantalla 2024-12-20 a las 10.07.45.png](Captura_de_pantalla_2024-12-20_a_las_10.07.45.png)
    
    As `row` is a `cell` object, we can apply the method `find_all` to it and extract table cells in the object `cells` using the tag `td`, this is all the children with the name `td`. The result is a list, each element corresponds to a cell and is a `Tag` object, we can iterate through this list as well. We can extract the content using the `string` attribute.
    
    ```python
    for i,row in enumerate(table_rows):
        print("row",i)
        cells=row.find_all('td')
        for j,cell in enumerate(cells):
            print('colunm',j,"cell",cell)
    ```
    
    ![Captura de pantalla 2024-12-20 a las 10.08.41.png](Captura_de_pantalla_2024-12-20_a_las_10.08.41.png)
    
    If we use a list we can match against any item in that list.
    
    ```python
    list_input=table_bs .find_all(name=["tr", "td"])
    list_input
    ```
    
    ![Captura de pantalla 2024-12-20 a las 10.10.33.png](Captura_de_pantalla_2024-12-20_a_las_10.10.33.png)
    
- **`attrs`**
    
    If the argument is not recognized it will be turned into a filter on the tag’s attributes. For example with the `id` argument, Beautiful Soup will filter against each tag’s `id` attribute.
    
    ```python
    # Examples: 
    # Filtering based on the id value
    table_bs.find_all(id="flight") #output:[<td id="flight">Flight No</td>]
    
    # Find all the elements that have links to the Florida Wikipedia page:
    list_input=table_bs.find_all(href="https://en.wikipedia.org/wiki/Florida")
    list_input #output: 
    #[<a href="https://en.wikipedia.org/wiki/Florida">Florida</a>,
    # <a href="https://en.wikipedia.org/wiki/Florida">Florida</a>]
    
    # If we set the href attribute to True, 
    # regardless of what the value is, the code finds all tags with href value:
    table_bs.find_all(href=True) #output:
    #[<a href="https://en.wikipedia.org/wiki/Florida">Florida</a>,
    # <a href="https://en.wikipedia.org/wiki/Texas">Texas</a>,
    # <a href="https://en.wikipedia.org/wiki/Florida">Florida</a>]
    ```
    
- **`string`**
    
    With string you can search for strings instead of tags, where we find all the elments with Florida:
    
    ```python
    table_bs.find_all(string="Florida")
    ```
    

### `find()` **method**

It’s useful if you are looking for one element, as you can use the `find()` method to find the first element in the document.

```python
two_tables="<h3>Rocket Launch </h3><p><table class='rocket'><tr><td>Flight No</td><td>Launch site</td> <td>Payload mass</td></tr><tr><td>1</td><td>Florida</td><td>300 kg</td></tr><tr><td>2</td><td>Texas</td><td>94 kg</td></tr><tr><td>3</td><td>Florida </td><td>80 kg</td></tr></table></p><p><h3>Pizza Party  </h3><table class='pizza'><tr><td>Pizza Place</td><td>Orders</td> <td>Slices </td></tr><tr><td>Domino's Pizza</td><td>10</td><td>100</td></tr><tr><td>Little Caesars</td><td>12</td><td >144 </td></tr><tr><td>Papa John's </td><td>15 </td><td>165</td></tr>"
two_tables_bs= BeautifulSoup(two_tables, 'html.parser')

# We can find the first table using the tag name table
two_tables_bs.find("table")

# We can filter on the class attribute to find the second table, 
# but because class is a keyword in Python, we add an underscore to differentiate them.
two_tables_bs.find("table",class_='pizza')
```

## **Downloading And Scraping The Contents Of A Web**

### Example 1: Links, images

We download the contents of the web page. We use `get` to download the contents of the webpage in text format and store in a variable called `data`. We create a `BeautifulSoup` object using the `BeautifulSoup` constructor:

```python
url = "http://www.ibm.com"
data  **=** requests.get(url).text
soup **=** BeautifulSoup(data,"html5lib")  *# create a soup object using the variable 'data'*
```

**Scrape all links:**

```python
**for** link **in** soup.find_all('a',href**=True**):  *# in html anchor/link is represented by the tag <a>*
print(link.get('href'))
```

![Captura de pantalla 2024-12-20 a las 10.33.16.png](Captura_de_pantalla_2024-12-20_a_las_10.33.16.png)

**Scrape all images Tags:**

```python
**for** link **in** soup.find_all('img'):*# in html image is represented by the tag <img>*
print(link)
print(link.get('src'))
```

### Example 2: Tables

**Scrape data from HTML tables:**

```python
#The below url contains an html table with data about colors and color codes.

url = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DA0321EN-SkillsNetwork/labs/datasets/HTMLColorCodes.html"
data = requests.get(url).text
soup = BeautifulSoup(data,"html5lib")
```

> Before proceeding to scrape a web site, you need to examine the contents and the way data is organized on the website. Open the above url in your browser and check how many rows and columns there are in the color table.
> 

```python
#find a html table in the web page
table = soup.find('table') # in html table is represented by the tag <table>

#Get all rows from the table*
for row in table.find_all('tr'): # in html table row is represented by the tag <tr>

*# Get all columns in each row.
cols = row.find_all('td') # in html a column is represented by the tag <td>

color_name = cols[2].string # store the value in column 3 as color_name
color_code = cols[3].string # store the value in column 4 as color_code

print("{}--->{}".format(color_name,color_code))
```

![Captura de pantalla 2024-12-20 a las 10.37.03.png](Captura_de_pantalla_2024-12-20_a_las_10.37.03.png)