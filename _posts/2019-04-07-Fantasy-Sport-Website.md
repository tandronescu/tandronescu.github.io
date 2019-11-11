---
title: Fantasy Sports Website
date: 2019-04-07
tags: [website, PHP, SQL, DNS, WordPress, software]
header:
    image:
---

In the past, I often enjoyed holding annual competitions with my friend groups over choosing the correct score predictions for various sport events. Previously, I manually collected people's guesses and had to keep score of everything by hand. Instead of this tedious process, I automated this hobby and spawned a website to organize this information. This served as an excellent means of hosting these annual tournaments. The website can be found at this url (currently the DNS service is turned off until the next sporting playoff period begins): [https://fantasykernel.com/](https://fantasykernel.com/)

Along the journey of creating this website, I learned many valuable skills that can be applied in both web development and other applications outside this realm. 

To begin, I had to go through the process of acquiring a domain name through a DNS provider and performing the initial setup required to actually host a website. Another aspect of this preliminary setup was to secure the website using an SSL certificate. 

Next, I had to select a means of setting up the infrastructure for the website. After conducting a fair share of research into the options available, I chose to use a Digital Ocean droplet based on the WordPress content management system. WordPress provided a convenient way to organize the front-end aspects of the website while also providing a backbone for the SQL database structure. Here is a view of the homepage created using a WordPress plugin called Elementor: 
<br /><br />
![Fantasky Kernel Home](/images/fantasy-kernel-home.png)

The next step was begin organizing the basic page structure of the website using PHP to construct the backend content of the website. Building on top of WordPress' user login system, I implemented a custom plugin to change the flow of the user login and registration system to match the scope of the website. Instead of using the default WordPress pages and system, the custom plugin allowed for a new interface, fields of interest, security checks and anti-spam features. The image below shows the registration page used for new users:
<br /><br />
![Fantasky Kernel Register](/images/fantasy-kernel-register.png)

In order to add the desired fantasy sport functionality, user information would have to be stored in a database to save their scores and input. SQL was used to achieve this purpose, and the information in the SQL tables was used to filter website content displayed to user's based on their registration status or points accumulated. Some highlights of the website will be illustrated below including a user score input system and the leaderboard showing the top-scoring players. 
<br /><br />
![Fantasky Kernel Score Input](/images/fantasy-kernel-submit-scores.png)
<br /><br />
![Fantasky Kernel Leaderboard](/images/fantasy-kernel-leaderboards.png)

Overall, this was a fun project automating a game originally played among my friend group into a full-blown website. The first test run of the 2019 NBA Playoffs accumulated over 30 users and was a success. In the future, I certainly hope to grow the website, improve the functionality and expand to other sport events. 








