cssrefactoring
==============

A book on refactoring large CSS codebases

## Setup

You need Ruby, bundle, and all the Octopress/Jekyl ecosystem stuff.

```shell
bundle install
rake install
git remote add origin git@github.com:roblevintennis/cssrefactoring.git
```

## Authoring

*Do not push directly to `gh-pages` branch as it will bork the Octopress deploy task*

```shell
git commit -m"your message";#commits your work on [master] branch
rake generate
rake preview #now go to: http://localhost:4000/cssrefactoring and verify changes
rake deploy #will push _deploy dir to gh-pages branch
# Now that you've deployed to gh-pages, you still need to commit to the [master] branch:
git push origin master
```

## Where's the book?

We haven't quite added links to the book pages yet. We will soon. For now, go to:

http://localhost:4000/cssrefactoring/convincing-management/

http://localhost:4000/cssrefactoring/extract-module/

http://localhost:4000/cssrefactoring/architecting-modular-css/

## Hacking Notes

### Custom Theme

Essentially, just copied the classic theme to a cssrefactoring theme:
...

```shell
cp -R .themes/classic/ .themes/cssrefactoring/
rake install['cssrefactoring'] # essentially copies this theme over into /source
```
#### Making changes to theme:

First go ahead and make a simple change in the:
`.themes/cssrefactoring/sass/base/_layout.scss` file (or any other file in that theme that'll show up)
I made a simple `outline: 10px solid hotpink;` right on the `body` for example.

Now use the install task to copy over your updated theme and generate and preview:

```shell
$rake install['cssrefactoring'] && rake generate && rake preview
A theme is already installed, proceeding will overwrite existing files. Are you sure? [y/n] y
```

Now you should be able to go to the localhost:4000/cssrefactoring and see your theme changes


