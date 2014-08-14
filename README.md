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
git commit -m"your message";
rake generate
rake preview #now go to: http://localhost:4000/cssrefactoring and verify changes
rake deploy #will push _deploy dir to gh-pages branch
```
