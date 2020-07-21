---
layout: post
title: Example post of Freddie Venturas Blog
description: Ammended post from the template to understand it myself 
date: 2020-07-21 22:02:00
hero_image: https://www.csrhymes.com/img/example-docs-page.jpg
hero_height: is-large
hero_darken: true
image: https://www.csrhymes.com/img/example-docs-page.jpg
tags: post first standard template
canonical_url: https://www.csrhymes.com/2020/05/08/creating-a-docs-site-with-bulma-clean-theme.html
---

Malesuada molestie lorem. Nunc non mauris. Nam accumsan tortor gravida elit.
Cras porttitor.

Praesent vel enim sed eros luctus imperdiet. Mauris neque ante, placerat at,
mollis vitae, faucibus quis, leo. Ut feugiat. Vivamus urna quam, congue
vulputate, convallis non, cursus cursus, risus. Quisque aliquet. Donec
vulputate egestas elit. Morbi dictum, sem sit amet aliquam euismod, odio tortor
pellentesque odio, ac ultrices enim nibh sed quam. Integer tortor velit,
condimentum a, vestibulum eget, sagittis nec, neque. Aenean est urna, bibendum
et, imperdiet at, rhoncus in, arcu. In hac habitasse platea dictumst.
Vestibulum blandit dignissim dui. Maecenas vitae magna non felis ornare
consectetuer. Sed lorem. Nam leo. In eget pede. Donec porta.

Etiam facilisis. Nam suscipit. Ut consectetuer leo vehicula augue. Aliquam
cursus. Integer pharetra rhoncus massa. Cras et ligula vel quam tristique
commodo. Sed est lectus, mollis quis, lacinia id, sollicitudin nec, eros.
Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere
cubilia Curae; Morbi urna dui, fermentum quis, feugiat imperdiet, imperdiet id,
sapien. Phasellus auctor nunc. Vivamus eget augue quis neque vestibulum
placerat. Duis placerat. Maecenas accumsan rutrum lacus. Vestibulum lacinia
semper nibh. Aenean diam odio, scelerisque at, ullamcorper nec, tincidunt
dapibus, quam. Duis vel ante nec tortor porta mollis. Praesent orci. Cras
dignissim vulputate metus.

Phasellus eu quam. Quisque interdum cursus purus. In orci. Maecenas vehicula.
Sed et mauris. Praesent feugiat viverra lacus. Suspendisse pulvinar lacus ut
nunc. Quisque nisi. Suspendisse id risus nec nisi ultrices ornare. Donec eget
tellus. Nullam molestie placerat felis. Aenean facilisis. Nunc erat. Integer in
tellus. Mauris volutpat, neque vel ornare porttitor, dolor nisi sagittis dolor,
sit amet bibendum orci leo blandit lacus.

In id velit sodales arcu iaculis venenatis. Etiam at leo. Vivamus vitae sem.
Mauris volutpat congue risus. Curabitur leo. Aenean tempor tortor eget ligula.
Aenean vel augue. Vestibulum ac justo. In hac habitasse platea.

## GitHub Pages Configuration

GitHub pages allows you to create a website for your project with free hosting. Go to your repo on GitHub, then click Settings, then scroll down to the GitHub Pages section. You have the option to create a site from the root of your master branch of from the /docs directory in your master branch. For this example, we are going to use the /docs directory. 

Don't change this setting just yet as if you don't have a docs directory there will be nothing there to publish. 

## Creating the docs directory

Clone your git repo to a local directory, let's say `~/code/my-project` for this example. The below assumes you don't yet have a docs directory and you have [jekyll installed](https://jekyllrb.com/docs/installation/). If you do already have a docs directory you will have to rename it to something else. 

Create a new jekyll installation in the docs directory, ensuring you replace your username and project name in the below example.

```bash
git clone https://github.com/username/my-project.git ~/code/my-project
cd ~/code/my-project
jekyll new docs
```

You should now have a base install of Jekyll in your freshly created docs directory. 

## Configuring the theme

1. Replace everything in the Gemfile with the following
```
source 'https://rubygems.org'
gem "bulma-clean-theme",  '0.7.2'
gem 'github-pages', group: :jekyll_plugins
```

2. Open the `_config.yml` and comment out or delete the line `theme: minima` and replace it with `remote_theme: chrisrhymes/bulma-clean-theme`, then add `github-pages` to the list of plugins. Update the baseurl to your GitHub repo name, in this example we are using `my-project` as the repo name
```yaml
#theme: minima
remote_theme: chrisrhymes/bulma-clean-theme
baseurl: "/my-project"
plugins:
- github-pages
```

3. Open the `index.md` file and update the front matter so the layout is page and then add a title
```yaml
layout: page
title: Docs for My Project
```

4. Run `bundle install` and then `bundle exec jekyll serve`

5. Visit `http://localhost:4000/my-project/` to view your new docs page.

## Menu

To create a menu on the left on your docs page you need to create a new yaml file in _data directory, such as `menu.yaml` and then use the below format, where the label will be the menu title and the items are the menu items. Each menu item can have a list of sub menu items if needed.

```yaml
- label: Example Menu
  items:
    - name: Menu item
      link: /link/
      items:
        - name: Sub menu item 
          link: /sub-menu-item/
```

## Table of contents

If you would like auto generated table of contents for your docs page then add `toc: true` to the page's front matter. The table of contents works for markdown pages and loops through the heading 2s and heading 3s in the markdown and then auto generates the contents.

## GitHub Sponsors

If you want to link to your GitHub sponsors profile then add `gh_sponsor` with your username to the `_config.yml` file.

```
gh_sponsor: chrisrhymes
```

## Making the docs page live

Once you have finished creating your docs page you can commit your changes and push everything up to GitHub. Go back to the GitHub settings page and scroll back down to the GitHub Pages section. Now we can update the setting to use the Master branch /docs folder and then GitHub will build your new docs page. 

## Want to see an example?

I recently updated one of my own packages to use Bulma Clean Theme to power the docs page. Check out the docs for [Bulma Block List](https://www.csrhymes.com/bulma-block-list) as an example. 
