---
title: "Hugo"
date: 2019-11-15T14:24:54+08:00
tags: ["Hugo","Git"]
---
## Create and deploy your Hugo site on Github

### create repo in github
- hugo_blog
- <user_name>.github.io

```bash
hugo new site hugo_blog
cd hugo_blog && git init && git remote add origin https://github.com/<user_name>/hugo_blog
# add theme
git submodule add https://github.com/calintat/minimal.git themes/minimal
git submodule add -f https://github.com/<user_name>/<user_name>.github.io.git
cat > config.toml << EOF
baseURL = "https://<user_name>.github.io/" 
languageCode = "en-us"  
title = "Test Site"  
theme = "minimal"  
googleAnalytics = ""  
publishDir = "<user_name>.github.io"
EOF
hugo
cd <user_name>.github.io.git && git add . --all && git commit -m "hugo static" && git push
git add . --all && git commit -m "first hugo site" && git push -u origin master
```

Browser [https://<user_name>.github.io](https://<user_name>.github.io)
