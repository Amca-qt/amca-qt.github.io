---
title: "Micro-CMS v1 WriteUp"
description: Walkthrough On Micro-CMS v1 challenge
date: 2024-12-03T19:47:03+08:00
image: cover.jpg
math: 
license: 
hidden: false
comments: true
draft: false
tags: 
    - Hacker 101
    - Write Up
    - Hacking
    - Easy
---

# Flag 1 : Cross Site Scripting ( XSS )

At first we've been redirect to a simple webpage ,try to explore the site, but found nothing only `testing page` ,`Markdown Test` and `Creating a new page`

![1](img/1.PNG)

so I try to edit the `Testing Page` by add the XSS Payload on the title then go back to homepage and you'll get the flag

![Flag 1](img/flag1.jpg)

# Flag 2 : Unauthorized Access

When I created the first page , I noticed it was assigned an id of 6

![3](img/2.PNG)

When I visit the two pages provided before, I noticed that the pages have an id of 1 and 2. which means there must be another pages with a different id. So I go around by changing the `id` from `1` to `10` but found nothing.

So I try explore everything on the web and found that the `edit page also have id `

![4](img/3.PNG)

Just like before , I changing the `id` from `1` to `10`, and found the 2nd flag 

![Flag 2](img/flag2.jpg)

# Flag 3 : SQL Injection 

Since all pages refer an `id` I try to test it with a `single quote (')` and somehow reveal the third flag

![Flag 3](img/flag3.jpg)

# Flag 4 : Stored XSS

![6](img/4.PNG)

See that `Markdown is supported, but scripts are not` means we have to find a way to bypass the markdown filter to execute xss to get the flag. Noticed the button code ? let's input XSS Payload in it

```XSS Payloads
<button onclick=alert(‘xss’)>click</button>
```

The payload execute nicely but nothing showed up, try to view the source code and you'll find the flag

![Flag 4](img/flag4.jpg)

# Conclusion

In conclusion this chall really teach about common Vulnerabilities that goes around and still relevant on this modern world
> Anjai speaking

![Gif](https://i.pinimg.com/originals/95/b1/d0/95b1d08de5b303cb5ab80af7b08dbdc4.gif)

# Happy Hacking









































