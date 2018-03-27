# Web-Crawler
Crawls a social networking website "Fakebook" in search of secret flags

High- level Approach:

This is a client-based program that crawls the fakebook page(server) by building up the socket connection. 
The client first recieves the home page of fakebook through HTTP GET.
The program uses HTML Parser to search the links in the page and then crawls to the login page.
The program then uses HTTP POST to send the login details and then the GET the CSRF token and the session id
After this, the crawler crawls to every fakebook page.
The program maintains two lists: one for already crawled links and one which consists of links that is waiting to be crawled.
While crawling these pages, the crawler looks for the flags that are abruptly present in selective pages of fakebook and prints it.
The program also takes care for the different HTTP status codes 200, 404, 500, 301 and 403

Code Implementation:

	This program imports the following modules:
		socket: To build a socket connection with the server
		AF_INET: To build a tuple of Address Family used to assign Hostname and Port Number
		SOCK_STREAM: For using TCP Connection
		sys: For taking command-line arguments
		HTML Parser: For Parsing the HTML page and looking for tags
		re: For using the regular expression for extracting the hexadecimal strings and links

Challenges Faced:
	Using HTTP POST to send login details
	Getting the CSRF token and Session id
	Using HTML Parser to continue parsing and crawl to the further pages
	Finding the flags from the pages
	Handling different HTML error codes 
	
Testing:

	Correct NU ID and password: "All flags received"
	Incorrect number of command line arguments: Error raised: Incorrect Arguments"
	Incorrect NU ID and correct password: "Error raised: Cannot retrieve token"
	Correct NU ID and incorrect password: "Error raised: Cannot retrieve token"
	Incorrect NU ID and Incorrect Password: "Error raised: Cannot retrieve token"

Steps taken:
	Research on HTTP GET and POST commands and its implementation to send login details to the server
	Solving the issue of connection by getting CSRF Token and Session Id
	Creating a way to handle crawling  of multiple pages using 'for' loop
	Creating two lists for crawled and uncrawled and managing it to avoid looping
	Handling the different HTTP message codes
	Research on HTML Parser and how to retrieve the links from it
	Research on 're' module and how to implement its findall and search methods
	Finding the way that the loop extracts the links automatically and redirects to the new link 
	Research on Flag extraction technique and building up a class for it
