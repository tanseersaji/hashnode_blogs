## Scrape data from JS rendered sites

So I was working on this model that will classify whether a piece of given news is fake or not based on different parameters that I think will be useful. And the first phase in any machine learning project is to collect relevant dataset. I found this Github repo ( [https://github.com/KaiDMML/FakeNewsNet](https://github.com/KaiDMML/FakeNewsNet) ) with a pretty good dataset and with that I decided to get more data because I like scraping and indexing the internet. Naturally, for collecting “real” news I decided to get links from the RSS feed of Google and Yahoo news and then scrape those news sites.

Pretty easy task, or so I thought. I wrote a function in python that will get each link from RSS feed and do a GET request on then to get the page source code. I quickly realised that some of these news sites render its content on the client-side using JavaScript, so as long as the JS is not rendered the page will not load the information in it. For this reason, my function returned a lot of javascript code and no actual news.

To solve this problem, I used Selenium to render the javascript and then get the page source. I used PhantomJS because of two reasons: 1. I do not want to launch a browser GUI and 2. Firefox Headless was not working (and I'm too lazy to fix that). Here is a function that I wrote to do this task.


```
def render_page(url):
    driver = webdriver.PhantomJS()
    driver.get(url)

    # To get the redirected URL (if any)
    url = driver.current_url 
    
    body = driver.page_source
    driver.close()
    return body, url
``` 

Since I’m using Google News RSS feed which uses a redirect link instead of the actual link to the news website I had to get the redirected URL in line 4 of the code snippet.

That is for this short post.