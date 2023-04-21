# garima-s_quotes_webscrapping
to automatically extract and parse data from quotes website. Then storing that data in data frames and creating datasets for research and learning purposes.
Website to scrape from: "http://quotes.toscrape.com/page/1/"


In the assignment, the number of pages to extract the data from was not mentioned, so I have created a function that will ask users for a valid number of pages they need.


Data to scrape from the website:
 1) Name
 
 2) Quotes 
 
 3) Tags


 Here we are going to use the following Python packages to complete our task:
 1) beautiful soup - used for taking data out from the website
 2) requests - to send our requests to the HTML server, it will take out data to store, 
 3) pandas - convert the information into a data frame and then export the data frame to CSV or Excel file 
 
 
On inspect of the website, we need to find the following things:
1) first, we need the html tag, which has only the necessary things to scrape. In each page body under the container, we have two 'div' HTML tags with the same class name, 'row.' but the first div contains the header and login of the page, which we don't need. It is the second div which contains the required information to scrape. Both div have the same class name and no other attribute; hence we will use the find_all method to get all the div and choose the second one. 
2) now we have the entire content with all the page's quotes, names, and tags. We need to loop through it to find sections of each quote. Each section is in tag div with the class name 'quote.' We will again use the find_all method to loop and get each div tag with the class name 'quote.' 
3) then, using for loop, we will iterate through each section and scrape the information needed: 
      i) Name: the name of the author. it is in the 'small' HTML tag. We retrieve the tag and then its value of it using the .text method. 
     ii) Quotes: the text of the quote. The quote data is in a 'span' HTML tag with the class name as 'text.' we retrieve the tag and then its value of it using the .text method. The quotes have double quotes in the beginning and ending, which doesn't store correctly in the CSV file. so to avoid that, we will remove the first character of the text.
     iii)Tags: the tag of the quote has multiple values. The tags are under the 'div' HTML tag with the class name 'tags.' Under this, multiple 'a' HTML tags have different names. So the tags have multiple values, so we use a tag_lst to store all the tags for the particular quote. we do so using the find_all method to get all the 'a' HTML tags and then going through each of them using for loop and retrieving the value using .text, and finally appending it in the tag_lst. I have use list to store all the tags as it can be easily stored in one place and retrived from one place.
After retrieving each quote's name, quote, and tags, it appends it to the content_lst, a 2d list that can be converted to a data frame using Pandas and stored into a .csv file.
 I have used a single for loop to scrape all three pieces of information from the website to reduce the code's memory space and time complexity.
