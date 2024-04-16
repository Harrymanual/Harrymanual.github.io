---
layout: home
---

# Welcome to My Website

I am Harrison Glenn, a student at the University of Sydney (USYD). I am passionate about artificial intelligence, software development, and the art of testing software. On this website, you will find information about my projects, blog posts, and more.

## About Me

I am currently pursuing my studies at USYD, where I am deepening my knowledge in the fields of AI and software engineering. I enjoy exploring the latest advancements in these areas and applying them to real-world problems.

## Projects

Here are some of my recent projects:

- [Project 1](project1.html): A brief description of Project 1.
- [Project 2](project2.html): A brief description of Project 2.
- [Project 3](project3.html): A brief description of Project 3.

## Blog

Check out my latest blog posts:

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      - {{ post.date | date: "%B %-d, %Y" }}
    </li>
  {% endfor %}
</ul>

## Contact Me

You can reach me via email at [your-email@example.com](mailto:your-email@example.com) or connect with me on [LinkedIn](https://www.linkedin.com/in/your-linkedin-profile).