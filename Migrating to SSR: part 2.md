# Migrating to SSR (Next.js) - part 2/3: WHAT ARE PROS AND CONS OF SSR?
In this edition of the **migrating React app to server-side rendering (Next.js) mini-series** we'll explore the pros and cons of server-side rendering as opposed to "client-only" single-page apps (and statically generated sites). We'll go through the UX, business, and product development perspectives. **You'll learn when you should opt for server-side rendering, when statically generated sites are a better choice and under which circumstances you'll be better off with a "basic" SPA.**

## What are the pros of SSR? 👍🏽
### Improved UX/Speed 🏎
The first argument which favours using SSR is the improved page speed. 
you save a roundtrip if you recall the image from the previous blog post (link)
there is no spinner / white screen
many platforms can benefit from SSG rather
only where it matters (if the content is behind a login gate, not so much)
e-commerce sites in an extremely competitve environments are the ones which benefit the most

### Better for SEO (controversial 🧐)
I've seen the SEO argument being used countless times, but frankly, I don't believe it is such a big deal. Let's first clarify why some people even make the claim that it's a big deal.

The way Google (and other) crawlers (which are scraping your website to display it in the search results) has *traditionally* worked is following: Visit a website, read the HTML delivered from the server/CDN, save it. Problems arised as libraries like React or Vue came into existence. As described in [the previous blog post](https://dev.to/tomdohnal/migrating-to-ssr-next-js-part-1-3-what-is-ssr-and-how-it-differs-from-other-approaches-50fa), almost no HTML is received in the first response from the server/CDN. It's only after the necessary part of JavaScript gets executed that you can see some meaningful content. And that's the root of the SEO problem -- crawlers would only see the one div or a spinner and wouldn't wait for the actual content to show up. Therefore, your page wouldn't get properly indexed.

However, this is no longer the case, at least with the Google crawler as it waits for all the content to load up. Where it might still be *necessary* is when you want to get a nice preview of your page when sharing to Facebook, Twiter etc. But if this would be your only concern, I think *prerendering* using a tool like [react-snap](https://github.com/stereobooster/react-snap) might be a better solution.
> You may *still* get some SEO improvements by using SSR even for crawlers which wait until all the content loads up. Indirectly -- **if the search ranking algorithm accounts for the page speed** (which should improve when using SSR), **your site should rank higher** in the search results.

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MTYyNDk3ODUsLTEyMzM1MzQxMzksMT
M1Nzk0NjY0OV19
-->