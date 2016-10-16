+++
date = "2016-10-15T19:51:09-06:00"
draft = false
title = "Personal Site Design"
image = "/personalSiteImage.PNG"
description = "Personal sites seem to use the same design today."
+++

Most developers, and non-developers, have their own personal websites. Usually they contain blogs, portfolios, contact information etc. For most developers they are a great way to point a potential employer to when they ask for examples of work or to be a kind of central hub for their online presence. Much like everyone else I have a blog and portfolio site but the portfolio site was in a dire need of an update. They didn't really link to each other easily and the portfolio was needlessly complex. Now I am not the most gifted individual when it comes to UI/UX so like any good millennial I did some quick google searching and opened 20 or so tabs on personal website design/examples.

Usually I would tell anyone to pick a good template and use that. But, I have found myself tired of a few current web-design trends today. To be specific, the landing page. Now this was the one that came up everywhere. Almost every single business site uses it and for good reason. It works well on every screen size, doesn't require multiple urls, is quite simple to implement, and there are plenty of templates out there. I should mention that I did see a few other examples of personal sites that did not follow this trend but they usually were complex in the animation department and were geared more towards illustration and design then web development which is my background. So what to do?

I decided to try something new. Instead of using a template, which has been my usual solution, I popped open a pen (Codepen.io),  tossed in Skeleton, a very barebones CSS layout system (~200 lines), and started playing around. I wanted to go with a minimal theme. Keep it as simple as possible.

[Original CodePen Design](http://codepen.io/gerrells-david/pen/VKjkPG)

# Layout

As for layout, when it really came down to it I only needed 4 sections: an about me, blog (just a link to here), projects, and contact information (email, github, linkin, etc). I went with a 2 by 2 grid that collapsed to a 1 by 4 on smaller screens. I put an icon from Font Awesome with some text describing what the section was for in the center. I found that I would need two other pages for about and projects. I could go for a SPA (single page application) or landing page style but I wanted things to stay away from landing pages and SPA for now.

## Navigation

I didn't want a standard navbar or hamburger menu (again try something new) and just went with another Font Awesome icon at the top left that goes back to the home page. I know some may argue that it would be better to use a navbar or hamburger but I think for this case it made no difference. If a user wanted to go to the projects page from the about page it would take two actions with a hamburger menu and one with a standard navbar but only on desktop as most navbars collapse to menus on small screens. With this it still would take two actions. One to go back to the home page and another to go to the desired section. It may not be as quick perhaps but I don't think it made much of a difference.

## About Page

I put in a basic centered div with the about me text. Really didn't need anything more complicated. Oh, and also the Font Awesome icon to go back to the home page.

## Projects page

This was the most difficult part of the design. I wanted to stay with 2 columns per row that collapsed on small screens and just have a title and link to an example/demo. I like the idea discovery with UX/UI for users. Having just the title of a project displayed initially can entice the curiosity of a user to perform an action. What is "Locomotion" about? What happens when I hover/click on this? It also can help reduce clutter. Now I am by no means an expert on how to execute the idea correctly which is why I went with flip cards. (yes I simply couldn't help myself and pulled the idea from Google) They allowed for showing just a title on one side and then on the other the description and tools used as well which was something I was missing as employers look for that kind of info.

One thing that was difficult was sizing the cards and text within the cards. It could still use some adjustment as some mobile browsers change their viewport size when they hide/show the browser header and because. This is because it I use viewport sizing.

# Color

I absolutely love Google's Material Design and usually take everything I can from it (especially the colors) but for this I wanted to limit myself more. For color I wanted to keep things monochromatic and try to stay with a black and white feel. Maybe have some hover color transitions from black to white and visa-versa.

# Animation

As I was wrapping things up I wanted to add a little bit a flavor to things. It is easy to get carried away with animations. I try to think that the only time an animation should occur is to indicate or give feedback to a specific action. They also should always complete quickly. I hate it when I have to wait for animations to finish. I dropped in Animate.css and threw on some classes for transitioning to and from pages and some entrances to elements on page load. I also animated the flip cards on the projects page to flip on hover. I may change it to a click in the future but it looks fine for now.

All in all I don't think it distracts from the user experience.

# Results

I use github pages to host the site and am quite please with the results. This is the first time I have tried to break away a bit from trends and design norms. Nothing revolutionary but I think I am going to try and take more risks in future work. I would recommend others to do the same. Not only can it be quite fun but it can also help you standout from all of the landing pages out there. I would love to see your personal site or hear your design ideas. You can find the result below.

[Final Result](https://dgerrells.github.io/personal-site)
