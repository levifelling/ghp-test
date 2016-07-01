# ghp-test

# for reference see
# http://krishicks.com/post/subtree-gh-pages/
# http://gohugo.io/tutorials/github-pages-blog/

git clone https://github.com/levifelling/ghp-test.git
cd ghp-test

git checkout --orphan gh-pages
git reset .
rm -rf .
touch index.html
git add -A
git commit -a

git checkout master 
_

git subtree add --prefix=public https://github.com/levifelling/ghp-test.git gh-pages --squash
git subtree pull --prefix=public https://github.com/levifelling/ghp-test.git gh-pages

# make changes and commit on master
git push origin master
git subtree push --prefix=public https://github.com/levifelling/ghp-test.git gh-pages
