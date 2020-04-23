---
layout: collection
collection: portfolio
entries_layout: grid
classes: wide
title: "Music store(website)"
excerpt: "A store for selling disks of music. I was in charged of call the records(disk) from Database and dealt with data from Database in case that shopper purchases records."
header:
  image: /assets/Images/blog_main/musicstore/project_header.png
  teaser: /assets/Images/blog_main/musicstore/project_thumb.png
sidebar:
  - title: "Role"
    image: /assets/Images/blog_main/musicstore/project1.png
    image_alt: "Main homepage"
    text: "Designer, Front-End & Back-End Developer"
  - title: "Responsibilities"
    text: "Main homepage, favorite, and cart pages. Purchaing processing, Plot favorite genre after data in DB"
gallery:
  - image_path: /assets/Images/blog_main/musicstore/content1.png
    alt: "Main homepage"
  - image_path: /assets/Images/blog_main/musicstore/content2.png
    alt: "Cart page"
  - image_path: /assets/Images/blog_main/musicstore/content3.png
    alt: "Favorite page"
  - image_path: /assets/Images/blog_main/musicstore/content4.png
    alt: " Purchasing process page"
  - image_path: /assets/Images/blog_main/musicstore/content5.png
    alt: "Card payment"
  - image_path: /assets/Images/blog_main/musicstore/content6.png
    alt: "Admin cart page"
---

# 1. Abstract
The pupose of this project is making web site to sell music albums. The webpage has features like other common shopping website such as login, logout, displayment items, purchasing the items, etc. But, this website show recommend items through several processing data. You will find the recommend side in the website if you visit it.

<br>

# 2. Project Period

- From 2019. 11. to 2020. 04.

<br><br>

# 3. Project Member

- Kim MinSeon, Kim JunHee, Ryu SiMyeong, Yang MinGyu, Yun JeongYeon

<br><br>

# 4. Development environment

## 1) Front-End

- HTML5, CSS3, Javascript, jQuery, Bootstrap, (Ajax)

## 2) Back-End

- JAVA, MySQL, Spring, JSTL

## 3) Web Application Server

- Apache tomcat 8.0

## 4) Tools

- eclipse, lombok, github(For team project)

<br>



{% include gallery caption="show my parts in the project.<br> top-left) Main Homepage &nbsp;&nbsp;&nbsp;&nbsp; top-middle) Cart page &nbsp;&nbsp;&nbsp;&nbsp; top-right) Favorite page<br>bottom-left) Purchasing process page&nbsp;&nbsp;&nbsp;&nbsp; bottom-middle) Card payment &nbsp;&nbsp;&nbsp;&nbsp; bottom-right) Admin cart page" %}



# 5. What was charged in?

## 1) Main page

- Page design
- Effect of carousel by jQuery with data from Database
- Applying processed data by scheduler in spring framework
- Display albums by data from DB

## 2) Shopping pages

### #1 Cart page & Favorite page

- Page design
- Display albums by data from DB
- Applying changed data by button with jQuery & Javascript
- Data processing by Ajax


### #2 Purchase process page, Purchase success & fail pages

- Page design
- Applying address search API(Application Programming Interface), payment API for card and mobile (It is not real payment.)
- Savig the infomation about a buyer(or shopper) to Database.
- Applying validation of entry information
- Data processing by Ajax

## 3) Pie Plot at Favorite chart page

- Applying farovite genre plot of national, of aborad, and of all by processing data from Database
- Data processing by Ajax

## 4) Admin cart page

- For editing data, Call data by SQL from Database
- Featuring CRUD(Create, Read, Update, Delete)

If you want more specific and detailed information of the project, Click below the powerpoint file which is made in Korean.
<br>
Music store powerpoint >> [Download](/assets/download/blog/portfolio/musicstore/musicstore.pptx)
<br>
And I put the website link in [Here](http://itproject.ezenac.co.kr/musicstore/). You could visit the website if the website is not expired.
