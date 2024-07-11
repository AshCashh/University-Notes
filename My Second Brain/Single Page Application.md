---
aliases:
  - SPA
tags: [webdev]
Created: 2024-03-23T10:49:33+10:00
Modified: 2024-07-03T19:35:33+10:00
---
A single-page application (SPA) is a [[Web Development|Web Application]] or website that interacts with the user by dynamically rewriting the current web page with new data from the web server instead of re-routing to a new page. The goal is faster transitions that make the website feel more like a native app.
## Advantages
- Major benefit is speed. Most resources are loaded initially ([[HTML]], [[CSS]], [[JavaScript Programming|JavaScript]]). Once loaded, the application is very responsive to UI and navigation.
- Due to web resources being able to be cached the website can be run offline without any issues
- Due to the web-app consisting of only a single page there exists compatibility with native mobile applications
## Disadvantages
- Search engine optimisation (SEO) can be difficult to get right due to web crawlers generally only indexing the main page.
- If the user has disabled JS then the webpage won't work
- Memory loads can be more severe as the application can persist in the browser for a long time
- The initial load of the webpage can be slow as all resources need to be loaded at once