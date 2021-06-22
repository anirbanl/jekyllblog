---
title:  "Writing Mathematical blogs in LaTeX through Jekyll"
mathjax: true
layout: post
categories: media
---

![General Relativity](/assets/img/general-relativity.jpg)

# Table of Contents
* [<u>Installation</u>](#install)
* [<u>Creation of blog</u>](#jekyll)
* [<u>GitHub Integration</u>](#github)
* [<u>Deployment</u>](#netlify)
* [<u>Extra Stuff</u>](#extra)

<br /><br />
## 1. Install Ruby and Jekyll <a name="install"></a>

To be able to write blogs with complicated mathematics, you need some way for compatibility of blogs with MathJax or LaTeX. LaTeX is often preferred among math writers because of the whole diversity of mathematical writing features available as well as it is the de-facto standard for writing research papers, articles, journals, theses and books. 

#### So then why Jekyll? .....

Jekyll is a static site generator with lots of cool features needed for publishing blogs and websites. Compared to more common website publishing tools, Jekyll gives you more fine-grained control over the content albeit without any steep learning curve. Jekyll is fast and offers easy integration with github for version management (making changes and keeping track) and also with publishing tools like Netlify. An icing on the cake is Jekyll offers gazillions of cool themes and designs to choose from catering to multiple needs and formats. Jekyll themes are so popular because it is not necessary to deal with all the complicated HTML stuff as you can write directly in [Markdown](https://www.ionos.com/digitalguide/websites/web-development/markdown/) (as simple as writing in Microsoft Word). If  you want to, you can still embed HTML in between, so nothing lost.

> The most important feature of all is that many Jekyll themes allow MathJax/LaTeX integration, which along with the other features, makes it the go-to for writing math blogs!

<br/>
### Installation steps

Follow the steps for Jekyll installation on [macOS](https://jekyllrb.com/docs/installation/macos/), [Windows](https://jekyllrb.com/docs/installation/windows/), [Ubuntu](https://jekyllrb.com/docs/installation/ubuntu/) and [Other Linux distros](https://jekyllrb.com/docs/installation/other-linux/).

To get an idea of some installation issues please check [Issue 1](https://github.com/jekyll/jekyll/issues/8523) and [Issue 2](https://github.com/jekyll/jekyll/issues/4972).

To check successful installation try the following steps:
```
> jekyll new my-website
```
A new folder `my-website` (this is a placeholder, feel free to change to whatever name catches your fancy, for example, the name of your cat...) would have been created with all necessary jekyll and bundle packages (I am not getting into the details here as they would be taken care of by the steps a few lines back). Next try:
```
> cd my-website
> bundle exec jekyll serve
```
The `bundle exec jekyll serve` command above compiles the most minimalist jekyll webpage and enables it for viewing. This command is very useful as it allows on-the-fly editing and viewing your website changes locally before publishing. If everything works well, then you will be able to view your FIRST jekyll website by going to `localhost:4000` in your browser. **TADA!!!**

<br /><br />

## 2. Creating your blogging site with Jekyll and LaTeX<a name="jekyll"></a>

Well, to write a blog, the first thing to do is choose a Jekyll theme which caters to your style and of course, the tastes of your audience. For mathematical blogs, often, minimalist designs are preferred. Hence, I tried out only two out of many: [Minima](https://github.com/jekyll/minima) and [Contrast](https://jekyllthemes.io/theme/contrast). I found Contrast to be very interesting as it is MathJax-ready and also allows very nice integration with different kinds of media content. Moreover, Contrast is based on Minima and offers much more!

<br/>
### Working with Contrast theme
Within folder `my-website` (root directory of your blog) clone contrast theme codebase (which is going to be your default site codebase where you will be making changes):
```
> git clone https://github.com/niklasbuschmann/contrast
> cd contrast
> bundle add webrick
> bundle update

> pwd
.../my-website/contrast
```

To ensure LaTeX compatibility add the following line to the end of your `_layouts/default.html` file. The Contrast theme comes with KaTeX and MathJax compatibility by default, however, adding this will enable recognition of many TexLive features (including *amsmath* etc.):
> ``<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>``

<br/>
### Start writing....

Done with all blog configuration stuff... Now we can start writing!

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.md` with the necessary preamble (check this [source](https://raw.githubusercontent.com/niklasbuschmann/contrast/master/_posts/2017-01-01-advanced-examples.md) for an example). To write in Markdown, for excellent tips and tricks refer this [article](https://www.ionos.com/digitalguide/websites/web-development/markdown/) or this [example](https://raw.githubusercontent.com/niklasbuschmann/contrast/master/_posts/2017-02-01-markdown-examples.md) to get started quickly. For more advanced stuff, please refer the examples in the Contrast demo site ([Link1](https://niklasbuschmann.github.io/contrast/advanced-examples/) and [Link 2](https://niklasbuschmann.github.io/contrast/about/)).

<br/>
### Adding LaTeX stuff

This is super easy as we can just simple add `$$` delimiter in the beginning and end of our LaTeX snippet (instead of the usual `$` as dollar is so common in normal text domain). A simple example is as follows:
```
$$\nabla_\theta \mathbb{E}_{\tau \sim \pi_\theta}[R(\tau)] = \mathbb{E}_{\tau \sim \pi_\theta} \left[R(\tau) \cdot \nabla_\theta \left(\sum_{t=0}^{T-1}\log \pi_\theta(a_t|s_t)\right)\right]$$
```
will render this equation: $$\nabla_\theta \mathbb{E}_{\tau \sim \pi_\theta}[R(\tau)] = \mathbb{E}_{\tau \sim \pi_\theta} \left[R(\tau) \cdot \nabla_\theta \left(\sum_{t=0}^{T-1}\log \pi_\theta(a_t|s_t)\right)\right]$$

Also, do not forget to set `mathjax: true` in your blog markdown preamble. However, Jekyll and MathJax do not offer all of the functionality of LaTeX—there is no support for the LaTeX `usepackage` command, so only the core LaTeX functionality that has been ported to MathJax is available [[Source](http://www.iangoodfellow.com/blog/jekyll/markdown/tex/2016/11/07/latex-in-markdown.html)].

<br/>
### Testing your blog locally

Once your file is created with the preamble and some content in Markdown/LaTeX is added (lot of content is not needed for testing your site.. just the preamble and some basic content.. as basic as a few words...), try the following `bundle exec jekyll serve` command as seen before to compile your changes and test locally by entering `localhost:4000` your browser. 
```
> pwd
.../my-website/contrast
> bundle exec jekyll serve
```
>The best part is you can keep this command running and parallely make your changes... just refreshing your browser will show your latest changes.. this on-the-fly editing and viewing feature makes this so BEAUTIFUL!

Once this is done, all the publishable content gets populated in the `_site` directory. To add content like images, etc., create a directory like `img` under `assets`, so that you can add `/assets/img/file.png` as your image location in your blog markdown file.

We are now ready to push everything to github....


<br /><br />

## 3. Pushing your site on GitHub <a name="github"></a>

Now, create a new repository on GitHub under your username, lets say `https://github.com/username/jekyllblog`. To avoid errors, do not initialize the new repository with README, license, or gitignore files. You can add these files after your project has been pushed to GitHub. Once this is done, we need to clean up your `contrast` folder of the previous git configurations and then add your current compiled content to be pushed to your own newly-created repo:

```
> rm -rf .git
> git init
> git remote add origin https://github.com/username/jekyllblog
> git remote -v
origin	https://github.com/username/jekyllblog (fetch)
origin	https://github.com/username/jekyllblog (push)
```

After the above cleaning is done and git remote location is verfied, you can now push your locally tested changes:
```
> git add *
> git commit -m 'First commit'
> git push -u origin master
```

The GitHub integration now allows you to easily publish your blog publicly with Netlify.

<br /><br />

## 4. Deploying with Netlify <a name="netlify"></a>

Netlify can be tightly integrated with your GitHub repository so that continuous deployment can happen everytime changes are pushed to GitHub [[Source](https://www.netlify.com/blog/2020/04/02/a-step-by-step-guide-jekyll-4.0-on-netlify/)].

> Continuous deployment ensures that everytime you update, you just need to test locally and push to GitHub.... REST IS TAKEN CARE OF!!!

Netlify comes with 100GB free storage per month (which is sufficient for many, and of course there are paid upgrade options as well). First step is create an account on [<u>https://app.netlify.com/</u>](https://app.netlify.com/). 

<br/>
### Linking GitHub repository

Click "New site..." button to start the process. There will be a dialog asking to choose the Git provider for continuous deployment -- Choose "GitHub". Once Netlify linking to Git provider is done (you might need to Click "Authorize Application"), you will be asked to pick a repository -- Choose your repository `https://github.com/username/jekyllblog`.

<br/>
### Final Step: Deployment

Netlify offers some simple options to configure under "Deploy Settings", for ex, you can change the name of your site (to be in the format optionally `sitename.netlify.app`, or you can choose or add a custom domain name) and the GitHub repository to sync from and many other options.

Netlify, under the hood, will take this forward by building and deploying the site. AND every single time your changes are pushed to GitHub!

Once the site status shows as "Published", you can check your site's public address as chosen by you.


<br /><br />

## 5. Extra stuff <a name="extra"></a>

<br/>
### Set up Google Analytics for your web blog

First create a tracking ID using the published URL of your blog by following the instructions in [Google Analytics](https://support.google.com/analytics/answer/10269537). Next add  `google_analytics: UA-NNNNNNNN-N` line (replace using your tracking ID of this format) to the preamble of your blog markdown. Visit your published URL and see the data get populated in Google!

<br/>
### Example Markdown
If you want to check the Markdown source for this blog, you can find it [HERE](https://raw.githubusercontent.com/anirbanl/jekyllblog/master/_posts/2021-06-21-writing-latex-blog.md)!

