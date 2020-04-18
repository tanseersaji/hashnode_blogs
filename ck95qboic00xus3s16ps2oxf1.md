## How I changed Devblog's Footer (CSS pseudo-elements)?

In this blog, I'll show you how I changed Devblog's default Footer text using CSS pseudo elements.

## What are CSS pseudo elements?
CSS pseudo elements are special keywords that allow you to style specific part of a CSS selector. Like for example, if you want to style the Placeholder of an Input tag then you can do that something like this.

```
input::placeholder {
    background: #eeeeee;
}
``` 
General syntax for using a CSS Pseudo Element is like this

```
selector::pseudo-element {
  property: value;
}
``` 
You can do crazy stuff with CSS pseudo-elements, if you want to learn more then check out this Post [(CSS Pseudo Elements/Classes you have never heard of!)](https://dev.to/lampewebdev/css-pseudo-elements-classes-you-have-never-heard-of-30hl)  from [Michael "lampe" Lazarski](https://dev.to/lampewebdev).

For this post we will be using the pseudo-element **::after**, this one creates an element after the element selected by CSS, for example, in my case I'm creating a element after the footer tag and changing the visibility of the footer tag of the to hidden.

```
footer p{
visibility: hidden;
}

footer p:after{
content: '© 2020 - Tanseer Saji | Made with 💕 by Hashnode';
visibility: visible;
  display: block;
text-align: center;
}
``` 
In here, the content attribute defines the actual text you want to fill in the created pseudo-element.
Only problem with css pseudo-element is that we can't add links to it.

## Where did I include this code?
The developers of devblog were kind enough to provide us to add third party widgets, but if you add a style tag into this textarea then that will be executed in the browser. So what I did is just wrote the above piece of code into that space.

You can find this setting be clicking of the gear icon on top of your Devblog site, then click on Widgets tab in the side bar.

You can't add script tags in this space because of obvious reasons, that the only drawback otherwise feel free to run your imagination to customize your blog using css styles.

Thanks,
T

