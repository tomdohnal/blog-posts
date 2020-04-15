# Migrating to SSR (Next.js) - part 2/3: IS IT EVEN WORTH IT? 💎
In this edition of the **migrating React app to server-side rendering (Next.js) mini-series** we'll explore the pros and cons of server-side rendering as opposed to "client-only" single-page apps (and statically generated sites). We'll go through the UX, business, and product development perspectives. **You'll learn when you should opt for server-side rendering, when statically generated sites are a better choice and under which circumstances you'll be better off with a "basic" SPA.**

## What are the pros of SSR? 👍🏽
### Improved UX/Speed 🏎
The first argument which favours using SSR is the improved page speed. 

If you navigate to a single-page application in your browser, the browser will first fire a request to download the HTML and JavaScript, and only after the JavaScript is downloaded and evaluated, it can fire additional request to fetch some data from your API. Meanwhile, the user is presented with a blank screen, spinners or skeletons. 

When you visit a website which uses SSR, the browser will fire a request, but, unlike with SPAs, the response contains all you need -- JavaScript files, HTML content *and* your data. **There are no spinners, skeletons -- no elements jumping around. The content is delivered faster, the time to the first paint improves.**

However, like with every other tool, it might be an overkill for your usecase. Think about if improving your page load by a couple of hundreds milliseconds is worth it. **It might be crucial in for e-commerce sites (which are in an extremely competitive** environment), **but might be an overkill for application which are only usable after loggin in**

> With the growing popularity of the [JAM Stack](https://jamstack.org/), you can get similar benefits (even better) in terms of speed for pages which don't require to be highly dynamic -- blogs, marketing sites or even some e-ccomerce sites.



### Better for SEO (controversial 🧐)
I've seen the SEO argument being used countless times, but frankly, I don't believe it is such a big deal. Let's first clarify why some people even make the claim that it's a big deal.

The way Google (and other) crawlers (which are scraping your website to display it in the search results) has *traditionally* worked is following: Visit a website, read the HTML delivered from the server/CDN, save it. Problems arised as libraries like React or Vue came into existence. As described in [the previous blog post](https://dev.to/tomdohnal/migrating-to-ssr-next-js-part-1-3-what-is-ssr-and-how-it-differs-from-other-approaches-50fa), almost no HTML is received in the first response from the server/CDN. It's only after the necessary part of JavaScript gets executed that you can see some meaningful content.

 **And that's the root of the SEO problem -- crawlers would only see the one div or a spinner and wouldn't wait for the actual content to show up. Therefore, your page wouldn't get properly indexed. However, this is no longer the case with the Google crawler as it waits for all the content to load up.** 

Where it might still be *necessary* is when you want to get a nice preview of your page when sharing to Facebook, Twiter etc. But if this would be your only concern, I think *prerendering* using a tool like [react-snap](https://github.com/stereobooster/react-snap) might be a better solution.
> You may *still* get some SEO improvements by using SSR even for crawlers which wait until all the content loads up. Indirectly -- **if the search ranking algorithm accounts for the page speed** (which should improve when using SSR), **your site should rank higher** in the search results.

## What are the cons of SSR? 👎🏻
### The need for a server
As opposed to the "traditional" SPAs where you don't even *need* a server to run your code, you need one in order to render the code on the server (it's called *server* side rendering after all...). What this means is that you have to pay for a server to execute your React.js code. If you already have a server, the resource consumption might go up. 

What can you do about it? Well, think about if SSR is the right solution for your usecase. You might be better of leveriging JAM Stack or a traditional SPA can be just enough for your usecase. Or, with the [new 9.3 Next.js release](https://nextjs.org/blog/next-9-3), you can easily combine SSR with static pages which prevents wasting server resources.

### It's harder for the development (sometimes)
If you were to roll your own SSR solution, you might be surprised that it's not as straightforward as creating a "traditional" SPA. If you think about it -- it makes sense. You have to take care to rendering the components to HTML, sending them to the browser, [hydration](https://reactjs.org/docs/react-dom.html#hydrate), making sure that you can fetch the data both on the server and the client...

Of course, if you use frameworks like Next.js or Nuxt.js, they abstract lot of these pain points so that you don't have to worry about them. However, for larger projects which want to start using SSR or which were using SSR before these frameworks existed, it can 

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3MTcyMjExMzksMzY5ODIwODU5LDEyND
QzNzk4NjAsLTExMDM4Mzc2NzUsLTEyMzM1MzQxMzksMTM1Nzk0
NjY0OV19
-->