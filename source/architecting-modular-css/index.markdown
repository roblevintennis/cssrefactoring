---
layout: page
title: "architecting modular css"
date: 2014-08-13 06:47
comments: true
sharing: true
footer: true
---


# Achieving CSS Nirvana

If we're going to refactor crufty legacy code into maintainable works of art, we need to have an idea on what exactly is &ldquo;good CSS&rdquo;? Obviously, this is somewhat subjective, but there are some agreed upon general guidelines that are quite helpful here. Two resources we like are [OOCSS](http://oocss.org/) and [SMACSS](https://smacss.com/). If you haven't had a chance to read up on those we highly recommend that you do so.

This section will paraphrase some of the more useful ideas in these systems while adding our own spin on what makes CSS more reusable and maintainable. These concepts are abstract in nature so don't worry if you don't fully understand them here–we will delve deeper with examples in subsequent chapters.

## Modules

Essentially, a module is an abstract representation of a distinct component such as a button, icon, media box, etc. There's been a ton of writing in the community on this topic and you may hear of similar ideas like: Brad Frost's notion of [atoms and molecules](http://bradfrostweb.com/blog/post/atomic-web-design/), Stephen Hay's notion of [designing a system of components ](http://bradfrostweb.com/blog/mobile/bdconf-stephen-hay-presents-responsive-design-workflow/), or Nicole Sullivan's notion of [CSS Objects](https://github.com/stubbornella/oocss/wiki#whats-a-css-object). What are the common benefits of all of these ideas? Well, if you're coming from a programming background you'll be happy that you can leverage some of the ideas you learned there:

* **Reusability:** A module can be used anywhere on layouts and pages
* **Modules can be nested:** As alluded to in the last point, a module can nest other modules within it. These are often interchangibly referred to a sub-modules or sub-components
* **Modularity:** Major sub-components of your module can be extracted and used in other components. For example, you could imagine the dropdown portion of a menu module being extracted out for use on a search autocomplete module when results are shown
* **DRY:** We don't duplicate our CSS code
* **SRP:** SRP stands for Single Responsibility Principle and, essentially, states that a module should _do one thing well_ **NEEDS CITATION**. So, for example, we don't convoluate an autocomplete search module with header navbar structural CSS
* **Orthogonality:** Russ Weakley states beautifully that modules must be ["location agnostic"](http://www.slideshare.net/maxdesign/css-oocss-and-smacss) in that they are independent of the location of their use. This notion works in tandem with SRP
* **Encapsulation:** With SRP and orthogonality we also achieve encapsulation as well

### Module Namespace

Modules start with a _base class_ that acts as the module's *namespace*. So a Button module's base class might be represented with the CSS class `.button` or `.btn`. In fact, if you'd like a very visual representation of this idea, go to [our own Buttons library](http://alexwolfe.github.io/Buttons/) and click the Customize button. In the popup you'll notice the input labeled Namespace. What we've done there is allowed you to pick your own namespace for your button (this is useful if you, for example, need to use our Buttons with [Zurb Foundation](http://foundation.zurb.com/) which uses `.button`, or [Twitter Bootstrap](http://getbootstrap.com/2.3.2/) which opts for the class `.btn`; simply use a different class and you'll prevent any chance of a collision).

### Module Sub-Classes

Once you've defined a base class, you can extend the functionality of your module with the use of sub-classes. Again, referring to our [Buttons](http://alexwolfe.github.io/Buttons/), you will note that flat buttons use the sub-class `button-flat`, rounded buttons `button-rounded`, pills `button-pill` and so on. These are sub-classes. This brings us to an important programming concept at play that is generally credited to [Bertrand Meyer's open/closed principle](http://en.wikipedia.org/wiki/Open/closed_principle#Meyer.27s_open.2Fclosed_principle) that states that entities (modules in our case):

> should be open for extension, but closed for modification

So the idea, is that we put all of our shared behavior in the base class and then extend this base functionality with sub-classes that add further behaviors. We can continue to extend the core functionality with extensions thus complying with Open/Closed. _See Wikipedia's article on the [Open/Closed Principle](http://en.wikipedia.org/wiki/Open/closed_principle) for more information on this idea._

### Module Configurability
While most of the information provided here is derivitive, I haven't seen a CSS best practices guide that speaks to module configurability. **TODO: Show examples in the buttons _options.scss that speak to how you can configure only the button types you want with the Sass list there**

#### Further Reading on Modules

If you haven't already, you should definitely take a look at what Jonathan Snooks has to say about [Modules](https://smacss.com/book/type-module), and here's a very nice [example-driven article](http://thesassway.com/advanced/modular-css-an-example) on modular CSS. Also note that there's a definite overlap between the ideas of modules and OOCSS's notion of CSS Objects.

## States

TBD is-foo etc.

## Shallow Selectors

Another term that you'll see for this is [Depth of Applicability](https://smacss.com/book/applicability) and it, essentially states:

TBD

## TODO Selector performance...right to left browser reads etc.
