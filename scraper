from urllib.request import urlopen as uReq
from bs4 import BeautifulSoup as soup
import time

# creating the csv file
filename = "indeedjobs.csv"
f = open(filename, "w")
headers = "Company; Job; City\n"
f.write(headers)

# Iterating through all indeed url's
for i in range(5):
	time.sleep(1)
	url = 'https://www.indeed.nl/vacatures?q=developer&start=' + format(i) + str(0)
	uClient = uReq(url)
	page_html = uClient.read()
	uClient.close()

	page_soup = soup(page_html, "html.parser")
	containers = page_soup.findAll("div",{"class":"row"})
	
# Iterating through jobtitle, city, and company name
	for container in containers:
	    jobtitle = container.a["title"]
	    city_container = container.findAll("span",{"class":"location"})
	    City_name = city_container[0].text
	    company_container = container.findAll("span",{"class":"company"})
	    company_name = company_container[0].text.strip()

	    print("Company: " + company_name)
	    print("Job: " + jobtitle)
	    print("City: " + City_name)

	    f.write(company_name + ";" + jobtitle + ";" + City_name + "\n")
f.close()








