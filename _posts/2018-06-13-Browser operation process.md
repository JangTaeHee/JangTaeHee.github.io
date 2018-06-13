---
layout: post
title: "Browser operation process"
date: 2018-06-13 16:04:08
image: 'http://drive.google.com/uc?export=view&id=1SB6OU6EldIFymGXn4-m-AIgzTEs64fTS'
description: Understand how your browser works.
category: 'web'
tags:
- web
- browser
twitter_text: Understand how your browser works.
introduction: Understand how your browser works.
---

## Web Application operation process

1. URL entered : The user enters the site address in a web browser.
2. DNS Lookup : Use DNS to access the server ip corresponding to site address.
3. Socket Connection : TCP socket connection for client to server connection.
4. HTTP Request : The http header and data from the client are send to the server. 
5. Content Download : When the request reaches the server, the user sends the requested document to the web browser.
6. Browser Rendering : The web browser's rendering engine parses the document in the following order:
    - convert HTML to DOM(Document Object Model).
    - add css to DOM (CSSOM create).
    - Create a Render Tree with DOM.
    - Draw a Render Tree.
7. Display Content : Display the render tree in the browser and display it as a web page to the user.

## Browser role & type

- Requests a resource(URL) from the server and displays it on the screen.
- Major browser
    - Google Chrome - Webkit
    - Safari - Webkit
    - Mozilla Firefox(Escape) - Gecko
    - Microsoft Internet Exploer
    - Opera

## Browser Engine

- Webkit : An open source based engine co-developed by google and apple. the major mobile browser are all based on webkit.
![placeholder](http://drive.google.com/uc?export=view&id=1l6H03FmewO8ZIw42YeZjrMga78JqDsWR "webkit flow")
- Gecko : C++ based engine, maintained by Mozilla, not commercial open source, but also for general developers.
![placeholder](http://drive.google.com/uc?export=view&id=1ZyU8htKKDkzR5fTnyTdN-VkHfFqlyjoL "gecko flow")

## Browser basic structure
![placeholder](http://drive.google.com/uc?export=view&id=1RuB2kcbqYcbHYCbybX8ArdsKVD1Ig-j- "browser components")
- UI : User-operable area such as address window, favorites, etc.
- Browser engine : Control behavior of UI and Rendering engine.
- Rendering engine : Display requested resource on screen.
- networking : Network calls such as http requests.
- UI back-end : Use os user interface method to illustrate basic widgets (combo boxes, etc.).
- JavaScript interpreter : interpret and execute JavaScript.
- Data store : Ability to store using browser memory such as local storage, indexed db, cookies.

## Rendering Engine
- The role of displaying the request from the server to the browser.
- Operation process
    - HTML -> DOM parsing.
    - Render Tree build.
    - Render Tree placement.
    - Draw a rendering tree.
> Render Tree : HTML element + Tree with CSS styling information, DOM + CSSOM.

## Critical Rendering Path - Introducing the main rendering path
- A series of steps that a browser must take to convert a file, such as html, css, javascript, etc, and display it on the screen in pixels.
- The process of rendering optimization should always start with a measurement and proceed with optimization.