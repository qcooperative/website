# QCooperative website

QCooperative website. The site is built using [hugo](https://gohugo.io/) with the [Meghna]<https://themes.gohugo.io/meghna-hugo/>) theme.

## Clone the repository

This repository uses submodules, use the recursive option to clone:

```
mkdir public
cd public
git clone --recursive git@github.com:qcooperative/website.git
```

## Install hugo 4.8+

Install hugo following the instructions in <https://gohugo.io/getting-started/installing/>.

Notice that the minimum version required for the Meghna theme is Hugo 0.48, while debian repositories only have 0.4\. Alternatively, for linux, you can [install using snap package](https://gohugo.io/getting-started/installing/#snap-package).

## Prepare deployment folder

Create ```public``` folder inside the cloned ```website``` and fetch the gh-page branch in it running the following command from the cloned ```website``` folder:

```
git worktree add -B gh-pages public origin/gh-pages
```

## Build

After you do some change to the content of the site, you can check how it looks by doing:

```hugo serve``` (beaware. do not run ```hugo server``` that is a default and autocompleted command)

or, to show draft posts:

```
hugo -D serve
```

To build for deployment, that is build to the public folder, just do:

```
hugo
```


Commit the changes to the sources first

```
git add -u  # and add new assets if any
git commit -m "Update sources"
git push origin master
```

Then, change to the public folder (which is checked at gh-pages), commit and push the changes:

```
cd public
git commit -am "Update site"
git push origin gh-pages
```
