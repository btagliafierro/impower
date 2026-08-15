Remove-Item -Recurse -Force site
mkdocs build --clean
mkdocs serve

git push origin --delete gh-pages
mkdocs gh-deploy --force

git add .
git commit -m "Update site content at project close"
git push