---
title: "Hugo"
date: 2019-11-15T14:24:54+08:00
summary: "How to create blog with Hugo and deploy to Github"
tags: ["Hugo","Git"]
categories: ["Readme"]
---
# Create and deploy your Hugo site on Github <!--more-->

### install hugo
```bash
brew install hugo
```

### create repo in github
- hugo_blog
- {user_name}.github.io

### create site by hugo and deply to github
```bash
hugo new site hugo_blog
cd hugo_blog && git init && git remote add origin https://github.com/{user_name}/hugo_blog
# add theme
git submodule add https://github.com/calintat/minimal.git themes/minimal
git submodule add -f https://github.com/{user_name}/{user_name}.github.io.git
cat > config.toml << EOF
baseURL = "https://{user_name}.github.io/" 
languageCode = "en-us"  
title = "Test Site"  
theme = "hamburg"
googleAnalytics = ""
publishDir = "{user_name}.github.io"

[menu]
  [[menu.main]]
    name = "Home"
    identifier = "home"
    url = "/"

  [[menu.main]]
    name = "Tags"
    identifier = "tags"
    url = "tags/"

  [[menu.main]]
    name = "Categories"
    identifier = "categories"
    url = "categories/"

[sitemap]
  changefreq = "monthly"
  priority = 0.5
  filename = "sitemap.xml"
EOF
hugo
cd {user_name}.github.io && git add . --all && git commit -m "hugo static" && git push
git add . --all && git commit -m "first hugo site" && git push -u origin master
```

### new post
```bash
hugo new posts/my-first-file.md
```

### example content
```
---
title: "Hugo"
date: 2019-11-15T14:24:54+08:00
summary: "How to create blog with Hugo and deploy to Github"
tags: ["Hugo","Git"]
categories: ["Readme"]
---
{your markdown context}
```

### push to github
```
hugo
cd {user_name}.github.io && git add . --all && git commit -m "hugo static" && git push
```
Browser Blog URL: [https://{user_name}.github.io](https://{user_name}.github.io)
