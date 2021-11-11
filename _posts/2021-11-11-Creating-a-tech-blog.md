---
published: false
---
## Creating a tech blog 

This post will detail how this blog came to be and how I work on the posts and what is the current work flow I'm using to manage new posts.

The base template is forked from one of many public Github repositories mentioning blogs and it's a Jekyll based template hosted for free using [GitHub Pages](https://pages.github.com/). With GitHub Pages, my entire blog ranging from all its static assets, CSS, configuration files and the actual posts are hosted on GitHub directly. I can edit, save, push my changes and a few minutes later, it'll all be live and ready to view. It's that easy! 

### Caveats

There are some small caveats in the process of forking an existing repo and making it your own to be aware of though. This is related to how Jekyll itself works and is configured in most of the cases and this is what I ran into:

- images need to be referenced within each individual post from a fixed directory at the root of the repo called `_images` in order for the template engine to pick them up and render them;

- in the existing `config` folder, the URL where the blog will be hosted will need to be edited in case it is required to match a "sub page" within the original GitHub pages domain. The reason for this is that most templates assume that the blog content is the only content that is being hosted using GitHub Pages, but, if you have different repositories with Pages enabled, that will need to be reflected in this configuration file;

### Writing process/development 

In order to actually write a post in such a way that I can edit it, preview it, make changes to the content and structure while I'm drafting it, I need a way to preview it locally and see how it looks. 

Since Jekyll generates these blog posts by essentially transpiling Markdown into a corresponding web view of the content coupled with CSS for styling and layout as well as any static assets, the best way to preview it is to either use a complete Markdown editor while writing it (for example, the Markdown editor in IntelliJ is really good) or to use a scheme where we can link the repository hosting our blog with a web service tailored for editing Markdown.

I've decided to follow such an approach for these posts and I'm using [Prose](prose.io) in order to do online editing and previewing and so far the experience has been great! 

### Conclusion 

It's easier than ever to start a blog nowadays and have it published in minutes and this has been my approach to this! Stay tuned for the next posts!! 