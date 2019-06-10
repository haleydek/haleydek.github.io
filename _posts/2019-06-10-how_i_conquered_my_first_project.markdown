---
layout: post
title:      "How I conquered my first project"
date:       2019-06-10 16:38:50 +0000
permalink:  how_i_conquered_my_first_project
---


As I sat down to start my first project, I felt a healthy combination of pride in how much I learned in only three weeks and uneasiness as I stared wide-eyed at my blank text editor. I was tasked with creating a CLI that scrapes data from an existing webpage and demonstrates all of the principles I learned about Object Oriented Programming. I thought to myself, “Whoa. Where do I even begin?”

After inspecting elements on numerous websites, I settled on the Twin Cities’ Animal Humane Society web page that lists all of the animals available for adoption at all of their shelters. I envisioned a CLI that would allow users to view pets by shelter or by species (i.e. dog or cat).

Before I even started coding, I thought about how I could best organize the data in my CLI. I decided that I would need a Species class, a Pets class, and a Shelter class. Next, I asked myself, “What relationship should these classes have with each other?” I knew that pets would belong to a species, and a species would have many pets. Pets and shelters would follow suit. What about species and shelters? Pets would be the join model, so a species would have many shelters through pets and vice versa.

Now that I knew the high-level framework of my project, I could start coding. I first wrote the code that scraped all of the data I needed from the website. Then, I started using the data to create the attributes of each class, with careful consideration to maintain the Single Source of Truth in my CLI. The last part that I built was the standard output and user input of my CLI.

Even though I initially felt overwhelmed at the thought of building a program on my own, I ended up cruising through the process with only a few small bumps in the road. I realized how important it is to have a clear understanding of the bones of my program before even writing a single line of code. Understanding the relationships between classes and ensuring that my scraper methods were pulling the data correctly gave me a strong foundation that made the rest of the process fairly seamless. You can’t start picking out paint colors before you have a strong foundation!
