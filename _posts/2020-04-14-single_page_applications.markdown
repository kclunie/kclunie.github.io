---
layout: post
title:      "Single Page Applications"
date:       2020-04-14 20:47:20 +0000
permalink:  single_page_applications
---


**What’s Single Page Application?**

A single page application is a single webpage where most of the information stays the same and only some of the data is updated. You will notice this if you look at Gmail, for example. Not much changes while navigating through your inbox. The only thing that changes is the current email you're looking at or folder. Single page applications only send the data you request and then your browser renders that information. On the flip side, a multi-page application involves the server re-rendering a full page with every click and sends it to your browser. This client-side method makes page load time must faster for users, the amount of information a server has to send much less and reduces costs.

**How Does a Single Page Application Work?**

A single page application is a web application or website that interacts with the user by dynamically rewriting the current page, rather than loading entire new pages from the server. This approach makes the application seem more like a desktop application and makes webpage transition much more smoother for the user. On most websites there is a lot of repetitive content such as navigation bars or headers/footers which makes a single page application very useful. These elements built together can be thought of similarly to a drawing or painting.  Some refer to this rendering of the webpage as painting the DOM. Multi-page websites paint the entire picture on the server and send it over to your browser. Single page applications guide the website to only paint the necessary data. This increases the speed of rendering the page when new content is requested when, for example, filtering your search results. In a multi-page traditional website a new render request would cause the server to repaint the entire picture and send it back. With Single Page Applications, the server sends specific updated instructions for a new page to be painted and where it needs to be painted. The speediness of this process stands out in the fact that by transferring the page rendering from the server to the client, the page can be dynamically rewritten, instead of going through an entire page reload.

**Single Page Applications Advantages**

There are many benefits to single page applications including improved application performance and consistency, and reduced development time and infrastructure costs. Below are some leading examples of advantages.

1. Single File Load

Single Page Applications download HTML in the beginning. After the initial page load, the server doesn’t send any additional HTML. The server sends you an outline page and your browser renders the user interface. As you navigate a webpage, the application sends requests for data to the server, the server sends back the data needed to the browser, and the browser renders an updated user interface. The data on the webpage is updated without the bulky full page refresh. This quick change of data is very usefull especially when it comes to navigation and repeat templates.

2. Server Vacation

Now that that the full page rendering is gone, the server doesn’t need to spend time and energy dealing with extra queries. Single page applications give the server a little break, which saves money because less servers are needed for the same amount of traffic.

3.  Fast and Free Front-end

Single page applications allow developers to build the front-end faster since the back-end and front-end are separated. Many data functionalities don’t change on the back-end, but how the front-end is designed may change or update from time to time. This is great since we don't want to risk messing with the data. Separating the back-end logic from how it’s presented allows developers to build, deploy, and experiment with the front-end completely independently of the underlying back-end technology. You can design the user experience, and then incorporate the data, and functionality from the back-end. APIs play a huge role here. APIs are a standard set of rules between applications on how they will structure, exchange, and reassemble data. The API setup lets developers build the front-end design quickely with no harm to the business critical back-end.

4. Enhanced User Experience

Since single page application frameworks can be updated independently, they are great to experiment with to create engaging and dynamic user experiences. As an added bonus, single page applications offer flexibility since many use JavaScript. Thanks to APIs, single page applications built in one language can work easily with back-end services developed in different languages. Furthermore, single page applications are great at making responsive designs for mobile, desktop and tablet.


