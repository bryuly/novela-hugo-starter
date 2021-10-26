---
title: When should I invest?
date: 2021-10-26T06:00:00+00:00
hero: "/images/favicon.svg"
excerpt: Is there a time that is best to invest?
timeToRead: 4
authors:
- Brad Yuly

---

## When should I invest?

Let me start with a statement, one should only engage in something they understand.

What do I mean by this? Simple, you probably don't go sky diving without first having an idea of what sky diving is, what its risks are, and how you mitigate those risks. After you have all the applicable information you can then make a judgement on if it is something you want to do or not do.

### Step 1

Learn what investing is, see my previous post **What is Investing?**

### Step 2

Learn what you are investing in, what the risks are and how you can mitigate those risks.

### Step 3

And finally, you get to this step. When should I invest? Investing as we are referring to in this article is long term investing (not day trading or even weekly). Long term investing is the easiest way to build wealth with a low amount of risk. 

...once the generated files are deployed, Gatsby lives in the browser. Gatsby cleverly generates a static website that turns into a web app after initial load, which extends the lifecycle to the browser.

What’s important to remember is that Gatsby’s lifecycle can be aggregated into 3 main sequences:

* Bootstrap
* Build
* Browser
* These three sequences makeup the Gatsby lifecycle.

Parts of the lifecycle are visible when running $ gatsby develop
A peak into the Gatsby lifecycle when running $ gatsby develop
A peak into the Gatsby lifecycle when running $ gatsby develop
If you’re familiar with React and the component lifecycle, Gatsby’s lifecycle is almost the same concept. Just like React’s lifecycle, Gatsby exposes hooks for developers to build on top of. Those lifecycle hooks are accessed through Gatsby specific files such as gatsby-node.js, gatsby-browser.js and gatsby-ssr.js.

What are the Gatsby specific files for?
gatsby-config.js
A place to put all your site configurations such as plugins, metadata, and polyfills. This file is the blueprint of your application and is where Gatsby really shines with its plugin system. When you run $ gatsby develop or $ gatsby build gatsby-config.js is the first file to be read and validated.

Most of your time spent in gatsby-config.js will likely revolve around source plugins, image plugins, offline support, styling options, and site metadata.

gatsby-node.js
Gatsby runs a Node process when you develop or build your website and uses Webpack under the hood to spin up a development server with hot reloading. During the Node process Gatsby will load plugins, check the cache, bootstrap the website, build the data schema, create pages, and deal with some configuration and data management.

Everything that occurs during the Bootstrap and Build sequences occurs in gatsby-node.js. This means it’s the perfect place to create pages dynamically based off data from a source plugin or modify Gatsby’s Webpack or Babel configs.

For example, if you want to move some files manually, such as a Netlify _redirects file, a good place to do it is in your gatsby-node.js file at the onPostBuild lifecycle hook.

From experience, most of my time has revolved around handling data and building pages in gatsby-node.js. This file quickly becomes the piping of your entire website.

## Examples of gatsby-node.js hooks:

* createPages
* onCreateBabelConfig
* onCreateWebpackConfig
* onPostBuild
* gatsby-ssr.js

When you think Server Side Rendering you think of a server that takes in requests and dynamically builds pages and sends it to the client. Gatsby doesn’t do that, but it does server side render — it generates all the pages during build time.

Naturally, gatsby-ssr.js allows developers to hook into that lifecycle. In my experience, most use cases revolve around injecting CSS, HTML, or Redux state information into the generated output. For example, if you need to insert third party scripts such as Analytics Tracking or a Pixel it can be done on the onRenderBody gatsby-ssr.js hook.

## Examples of gatsby-ssr.js hooks:

* onPreRenderHTML
* onRenderBody
* replaceRenderer
* gatsby-browser.js

Gatsby is a static site that loads a dynamic application after initial load, which means you get the benefits of a static site in a web application. gatsby-browser.js provides convenient hooks to deal with app loading, route updates, service worker updates, scroll positioning, and more.

Everything that occurs after your static site has loaded can be hooked in gatsby-browser.js. For apps that I’ve built, gatsby-browser.js was mostly used for keeping track of routes, scroll positioning, and sending analytics events.

## Examples of gatsby-browser.js hooks:

* onClientEntry
* onRouteUpdate
* onServiceWorkerInstalled
* registerServiceWorker
* shouldUpdateScroll

## Conclusion

Gatsby is built with React at its core and shares a common API pattern, the lifecycle. This lifecycle gives developers access to key moments in their website’s process through specific hooks. For example, adding analytics can be achieved through the Browser lifecycle hook onClientEntry. Gatsby reserves specific filenames as an entry point to access every lifecycle; these files are named gatsby-node.js, gatsby-ssr.js and gatsby-browser.js.

Without the Gatsby lifecycle, it would be impossible to customize and modify your project beyond the base configuration, leaving developers with a rigid and poor developer experience. This power and flexibility has helped us build amazing web projects for clients like Hopper!

Gatsby is a staple within our engineering process at Narative, helping us help our clients build the products they’ve always dreamed of, and the ones they’re yet to dream up.