## Beautiful Soup - Kinds of Objects


When we passed a html document or string to a beautifulsoup constructor, beautifulsoup basically converts a complex html page into different python objects.

### Some of the Important Objects:

* BeautifulSoup
* Tag
* NavigableString


##### BeautifulSoup

BeautifulSoup is the object created when we try to scrape a web resource. So, it is the complete document which we are trying to scrape. Most of the time, it is treated tag object.

        >>> from bs4 import BeautifulSoup
        >>> soup = BeautifulSoup("<h2 id='message'>Hello, Tutorialspoint!</h2>")
        >>> type(soup)

        <class 'bs4.BeautifulSoup'>

        >>> soup.name
        '[document]'

##### Tag Objects

A HTML tag is used to define various types of content. A tag object in BeautifulSoup corresponds to an HTML or XML tag in the actual page or document.

        >>> from bs4 import BeautifulSoup
        >>> soup = BeautifulSoup('<b class="boldest">TutorialsPoint</b>')
        >>> tag = soup.html
        >>> type(tag)  

        <class 'bs4.element.Tag'>


Tags contain lot of attributes and methods and two important features of a tag are its name and attributes.

Name (tag.name)
Every tag contains a name and can be accessed through â€˜.nameâ€™ as suffix. tag.name will return the type of tag it is.

        >>> tag.name

        'html'

However, if we change the tag name, same will be reflected in the HTML markup generated by the BeautifulSoup.

        >>> tag.name = "Strong"
        >>> tag
        <Strong><body><b class="boldest">TutorialsPoint</b></body></Strong>
        >>> tag.name

        'Strong'

Attributes (tag.attrs)
A tag object can have any number of attributes. Anything that is NOT tag, is basically an attribute and must contain a value.
    
    >>> soup = BeautifulSoup("<div class='example'></div>",'lxml')
    >>> tag = soup.div
    >>> tag['class']

    ['example']


NavigableString
The navigablestring object is used to represent the contents of a tag. To access the contents, use â€œ.stringâ€ with tag.

    >>> from bs4 import BeautifulSoup
    >>> soup = BeautifulSoup("<h2 id='message'>Hello, Tutorialspoint!</h2>")
    >>> soup.string

    'Hello, Tutorialspoint!'


You can replace the string with another string but you cant edit the existing string.

    >>> soup = BeautifulSoup("<h2 id='message'>Hello, Tutorialspoint!</h2>")
    >>> soup.string
    
    'Hello, Tutorialspoint!'

    >>> soup.string.replace_with("Online Learning!")
    >>> soup.string

    'Online Learning!'

    >>> soup

    <html><body><h2 id="message">Online Learning!</h2></body></html>


[`Next`](webscrape_beautifulsoup2.md)