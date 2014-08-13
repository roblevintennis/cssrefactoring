---
layout: post
title: "Ideas for Book"
date: 2014-08-10 08:58:45 -0700
comments: true
categories:
---
# CSS Refactoring Ideas

Just some ideas that could become chapters or sections


## Convincing Management of the Benefits

## Content Audit

Alex has a strategy for this which might be interesting to put in here.

## Our spin on OOCSS and SMACSS and general best practices

We can do our own take on these and more .. intent is to ramp up reader on best practices. This section needs to be short.

## Global Search and Regular Expressions

I saw this example at: http://wildbit.com/blog/2012/04/16/refactoring-14000-lines-of-css-into-sass/

Removing Ghost Selectors with Regular Expressions

Well, it happens — you redesign some element and forget to clean up old CSS afterwards, which makes the code bloated, increases file size and decreases performance. I spent a day checking if most of our CSS selectors existed in design mockups or development code. Consistent code formatting and simple regexps come in handy here. I used these ones the most:

[" ]classname — is this class name ever used?
h3.*classname — is this class name ever used with h3 element?
With these checks and refactoring I got rid of about 10% of our stylesheets, which is much more than I expected.

## Tools

#### CSS Dig http://atomeye.com/css-dig.html
#### autoprefixer
#### CSSCSS
#### CSS Comb
#### stylestats

Applying these tools to legacy styles

## Case Study: Buttons

## Case Study: TBD–some open source refactor???

## Safely Refactoring

Discuss a step by step strategy for safely extracting out modules, restructuring, etc.

#### Module Based Refactorings

For example, like the palette function I created for Mavenelink or table tease apart Trever and I did. We might want to borrow from the Refactoring idiomatic refactorings e.g. "Extract Method" could become "Extract Module". Mention Open/Closed principle and how base module should comply.

#### Patterns

Might be interesting to emulate some of the standard Refactoring literature out there e.g. Martin Fowler's  "Pull Up" etc. Not all of them just the ones that make sense

http://refactoring.com/catalog/ (and Rob has the book)

#### Removing overqualified selectors

#### Remove duplication DRY or Single Responsibility Principle

Perhaps using tools like CSSCSS


## Future Proofing Your Refactoring

### Styleguide
### Pattern Library

# Promoting the Book

TBD




