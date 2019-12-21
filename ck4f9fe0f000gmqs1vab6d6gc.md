## Tips to speed up your website

A 2007 Akamai study reveals that even a 100ms latency in a website can impact customer engagement and online revenue. Amazon found that 100ms delay in load time cost 1% of their sales. In 2018, Google shared an infographic that displayed how the bounce rate of your website increase for every second in load time delay.

This is a serious issue, but still, most newcomers in the field of web development do not care about how fast their website loads and instead care more about adding more images and more animation and particle.js to make UI look “pretty” and almost always (not all the time) ignore how users will feel while using that website. This blog is a list of things that I do while design/developing a website.

Just a note before starting, this list is indeed in order of importance according to me and the order may be different than what other web developers might do.

## 1. Use CDNs
I’ve seen people downloading JavaScript/CSS frameworks and linking that to their website. This is a massive mistake you as a web developer might be doing that suck up the load time of your website.

If you are using a famous framework (like JQuery or Bootstrap), there must be a CDN available for it. CDN is short for Content Delivery Network.


> A content delivery network or content distribution network (CDN) is a geographically distributed network of proxy servers and their data centers. The goal is to provide high availability and high performance by distributing the service spatially relative to end-users. CDNs serve a large portion of the Internet content today, including web objects (text, graphics and scripts), downloadable objects (media files, software, documents), applications (e-commerce, portals), live streaming media, on-demand streaming media, and social media sites.

Using CDN will decrease the number of files fetched from your server because a. that file may be already cached in the client’s browser and b. no HTTP(S) request is done to your server. Thus the server can spend more time serving actual content of the website and provide your users with information ASAP.

## 2. Cache Websites
If one or more pages in your website have static content then you should consider caching that page with all its content to the client’s browser. You can refer to this  [blog](https://www.iheavy.com/2011/11/01/5-tips-cache-websites-boost-speed/)  if you want to read more about it.

## 3. Never stop the content
You should never waste your precious load time for loading JavaScript files and CSS files (that does not correspond to the basic layout of the page) before rendering actual content of that page. To avoid this, you should always make two CSS files, one that specifies all the DOM layout styles like positioning and colour that will be hardcoded to the Head tag of the page and a different CSS that specifies all the animation, hover, focus styles of the element. This secondary CSS file can be appended to the Head tag using JS after rendering all the content.

Also, all JS files must be added at the end of your body tag.

## 4. Load text data before multimedia objects
Studies have shown that most of the time when a user is visiting a website, he/she is looking for some textual data rather than some image/video. Because if that was the case then that user would have searched Google Images or Youtube or something.

Therefore it’s better to load all the text data first and then load the images and videos that support the text. You can learn about your  [browser’s Page Load Order](https://johnresig.com/blog/browser-page-load-performance/)  or you can also use a JavaScript library called  [Lazy Load](https://appelsiini.net/projects/lazyload/) . You can also implement a  [Skeleton Screen](https://css-tricks.com/building-skeleton-screens-css-custom-properties/)  to improve the user experience.

## 5. Minimize layout recalculations
This simply means, don’t change the website layout after the website is loaded. Because when this happens, client computer’s CPU/GPU has to work again to rerender the webpage which will increase the battery/energy utilization of the user’s device. This may or may not affect the load time or user experience of your website but in the background, your website is using a lot of resources in client’s phone. (I think about customers)

## 6. Use popular fonts
This tip only applies to you, if you are one of those developers who add a lot of fancy fonts on your website and save that font locally in your server.

This is bad bro, don’t do that. You should rather use some Font provider like  [Google Fonts](https://fonts.google.com/)  and import/link that font on your website. Plus you should use a popular font that a lot of websites are already using because most probably that font must be already cached in client’s browser.

## 7. Minify all JS and CSS and HTML files
This is only applicable to production code, always keep a copy for later edits. You can use this  [website](http://minifycode.com/)  to do this task.

## 8. Google Page Speed
If you have an existing website and want to check it’s load time, you can use  [Google’s Page Speed](https://developers.google.com/speed/pagespeed/insights/)  service. This also provides a detailed list of things you can do in order to improve your website’s load time.

## 9. Google AMP
Google’s AMP (Accelerated Mobile Page) Project is an open-source initiative aiming to make the web better for all. The project enables the creation of websites and ads that are consistently fast, beautiful and high-performing across devices and distribution platforms. You can learn more about AMP on its  [official website](https://www.ampproject.org/) .

If you want to learn more about web development techniques or web development in general, you can refer to  [Google Web Fundamentals](https://developers.google.com/web/fundamentals/) 

That concludes this blog, you can try some of these tips and comment me if it worked or not. Also feel free to follow my blog, if you want to read more of my content.

