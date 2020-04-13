
In this series of articles, I'm going to go through the *what*, *why*, and *how* of the migration process of our React web application 💻 to a server-side rendering solution. You'll learn what SSR  is, how it differs from the "client-only" single-page applications and "regular" web apps, what are its pros and cons, and, finally, how to go about **migrating an existing React app to an SSR solution (Next.js).** (The concepts are the same for Vue apps (and Nuxt.js) or similar. 😉)

## What SSR even is? 🤔

To fully understand what SSR is, we'll first explore the differences between how "client-only" single-page applications (SPAs) and "regular" web apps are delivered to the browser and presented to the user.

  

### "Regular" web apps 🖥

Let's start with "regular" web apps. What I mean by this term is apps rendered on the server, usually using a language like PHP, Java ☕️, Ruby 💎, Node.js etc. and some templating language on top of HTML.

  

When you type in an address to this kind of an app or click a link pointing to it in your browser, the response of the app's server will contain all the HTML that you see in the browser.


![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/00q1pv5oueq6b7aofll1.png "Regular app diagram")

You can check it yourself --- go to [Wikipedia](https://en.wikipedia.org/wiki/Main_Page) 📖 (it's built using PHP), right-click anywhere on the page and choose "View source code" 👀. You'll see the HTML response that your browser received from the server and it contains *all* the content that you see on the page.

  

### "Client-only" SPAs ⚛️

On the opposite side of the spectrum 🌈, there are the "client-only" single-page apps. Those are for example applications bootstrapped with `create-react-app` or `@vue/cli`.

  

When you navigate to one of these pages, the response of the server (or CDN) will only contain one `div` element (+ maybe some `meta` tags or a loader). You might now be wondering -- does it mean that you will only be able to see one `div` on their screen? 😨 No, of course not. I didn't mention another important thing which gets fetched in the response. It is a `script` tag pointing to the JavaScript bundle. The moment the browser gets the response, the JavaScript engine kicks in 💥 and (using a library like React or Vue) builds the page for you (using a bunch of `document.createElement(...)` calls or similar).

![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/4cq7ribsfr5bdjgpjsak.png "Client-only SPA diagram")

  

An example of such an application is Netlify. When you visit [its web app](https://app.netlify.com/) and view the source code, you'll see just a small number of `div` elements, `script` tags etc. The actual content you see on your screen is built dynamically using JavaScript (React ⚛︎ in this case).

  
  

### Server-side rendered SPAs 🎶

Now that we have an understanding of what "regular" web apps and "client-only" SPAs are, we can proceed to server-side rendered SPAs. As you might have guessed, it is a mixture 🥣 of both approaches which tries to bring you the best of both of the worlds. Let's see how it works.

The TLDR that I like to use is as follows: It behaves as a "regular" web app on the first render and as a "client-only" SPA afterwards ⏩.

But what does it really mean? Well, if you visit such a website, your browser will receive a response which already contains all the HTML that is presented on that site. Just like with the "regular" web apps we talked about earlier. Then, the browser will execute the JavaScript code written in React, Vue or similar and start a process called hydration 💦. During this process, it will attach all your listeners  (`onClick` etc in React or `@click` etc in Vue) on the HTML elements which were delivered to the browser. After the hydration process is completed, the page behaves like a fully interactive SPA.

![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/irppqufr8g2hgevd3iv7.png "Server-side rendering diagram")

 An example of such a website is jobs.netflix.com (they use React with Next.js). When you go there, you don't see a spinner or a white screen but all the content appears instantly. Moreover, the whole page is fully interactive and the page transitions don't trigger a reload in the browser.

How can you make your application leverage server-side rendering? This topic will be covered in the subsequent blog post. (You can do it all in plain React/Vue and Node.js but it's *waaay* easier with libraries such as Next.js or Nuxt.js respectively)

  

### Statically exported sites 🍓

The list of different ways to architecture and deliver a web application could not be complete without at least mentioning statically exported sites. They are oftentimes written using so-called JAM Stack (JavaScript + API + Markdown) and bootstrapped using tools like Next.js, Gatsby.js, or Nuxt.js.

  ![Alt Text](https://dev-to-uploads.s3.amazonaws.com/i/6a1nfmg1cpj1iolcx3zz.png "Statically exported site diagram")

How do they differ from all the other approaches? Well, with these sites, all the HTML is delivered to the browser during the first render, just like with "regular" web apps or "server-rendered" SPAs. What's different is that there is no server running, creating these files on every request using a templating tool and sending them to the browser. Instead, you generate all the files at the build time 🛠, put them on the CDN and have them delivered right to your users' browsers. Basically, it's autogenerating HTML files. 😊

  

## Conclusion ✍️

I hope I managed to shed some light on *what SSR is* as well as describe some of the other approaches for delivering web apps to the browsers. There is *no finite* list of the "patterns" and there are always new ones emerging.

Of course, every application is different and there are pros and cons for each approach. You should always choose what suits 👔 *your* needs.

**In the next part of this mini-series, we're going to have a look at the pros and cons of using server-side rendering.**
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxMjc2MzE4MDZdfQ==
-->