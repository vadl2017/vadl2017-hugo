# vadl2017-hugo
Source for the website

## Make your website work locally 
hugo server -t hugo-material-docs

## Updating your site
Once you are happy with the results, Ctrl+C (kill server) and rm -rf public (don’t worry, it can always be regenerated with hugo -t <yourtheme>)
```
git submodule add -b master git@github.com:vadl2017/vadl2017.github.io.git public
```

Almost done: execute deploy.sh script to help you (and make it executable: chmod +x deploy.sh):

```
#!/bin/bash

echo -e "\033[0;32mDeploying updates to GitHub...\033[0m"

# Build the project.
hugo # if using a theme, replace by `hugo -t <yourtheme>`

# Go To Public folder
cd public
# Add changes to git.
git add -A

# Commit changes.
msg="rebuilding site `date`"
if [ $# -eq 1 ]
  then msg="$1"
fi
git commit -m "$msg"

# Push source and build repos.
git push origin master

# Come Back
cd ..
```

