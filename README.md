# ghp-test

User normal git workflow to commit changes on master. The `~/public` dir is linked to the gh-pages branch using `git subtree`. Details further down on how this was setup, but for normal development you don't need to worry about this.

## deploy to gh-pages
```
git subtree push --prefix=public https://github.com/levifelling/ghp-test.git gh-pages
```

## for reference see
- http://krishicks.com/post/subtree-gh-pages/
- http://gohugo.io/tutorials/github-pages-blog/


## initial setup for ~/public subtree
This only needs to be done once when setting up the repo. 
```
git clone https://github.com/levifelling/ghp-test.git
cd ghp-test

git checkout --orphan gh-pages
git reset .
rm -rf .
touch index.html
git add -A
git commit -a
git push -u origin gh-pages:gh-pages

git checkout master 

git subtree add --prefix=public https://github.com/levifelling/ghp-test.git gh-pages --squash
git subtree pull --prefix=public https://github.com/levifelling/ghp-test.git gh-pages
```
