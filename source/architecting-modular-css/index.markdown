---
layout: page
title: "architecting modular css"
date: 2014-08-13 06:47
comments: true
sharing: true
footer: true
---


# Achieving CSS Nirvana

If we're going to refactor crufty legacy code into maintainable works of art, we need to have an idea on what exactly is &ldquo;good CSS&rdquo;? Two resources which help with this question are: [OOCSS](http://oocss.org/) and [SMACSS](https://smacss.com/). If you haven't had a chance to read up on those we highly recommend that you do so. In this section we will paraphrase some of the more useful ideas in these systems while adding our own spin on what makes CSS more reusable and maintainable.

*These concepts are abstract in nature so don't worry if you don't fully understand them here–we will delve deeper with examples in subsequent chapters.*

## CSS Systems

Provide an overview and discuss how the combination of modules, layouts, states, etc., etc., create a complete CSS System for a web site or application. **TBD**

## Modules

Essentially, a module is an abstract representation of a distinct component such as a button, icon, media box, etc. There's been a ton of writing in the community on the topic and you may have heard of similar ideas such as: Brad Frost's notion of [atoms and molecules](http://bradfrostweb.com/blog/post/atomic-web-design/), Stephen Hay's notion of [designing a system of components ](http://bradfrostweb.com/blog/mobile/bdconf-stephen-hay-presents-responsive-design-workflow/), or Nicole Sullivan's notion of [CSS Objects](https://github.com/stubbornella/oocss/wiki#whats-a-css-object). What are the common benefits of all of these ideas? Here are some:

* **Reusability:** A module can be used anywhere on layouts and pages
* **Modules can be nested:** As alluded to in the last point, a module can nest other modules within it. These are often interchangibly referred to a sub-modules or sub-components
* **Modularity:** Major sub-components of your module can be extracted and used in other components. For example, you could imagine the dropdown portion of a menu module being extracted out for use on a search autocomplete module when results are shown
* **DRY:** We don't duplicate our CSS code
* **SRP:** SRP stands for Single Responsibility Principle and, essentially, states that a module should _do one thing well_ **NEEDS CITATION**. So, for example, we don't convoluate an autocomplete search module with header navbar structural CSS
* **Orthogonality:** Russ Weakley states beautifully that modules must be ["location agnostic"](http://www.slideshare.net/maxdesign/css-oocss-and-smacss) in that they are independent of the location of their use. This notion works in tandem with SRP
* **Encapsulation:** With SRP and orthogonality we also achieve encapsulation as well

*If you're coming from a programming background you'll be happy to know that you can leverage some of the ideas you've already learned!*


## How are modules implemented?

### Module Namespace

Modules start with a _base class_ that acts as the module's *namespace*. So a Button module's base class might be represented by `.button` or `.btn`. In fact, if you'd like a very visual representation of this idea, go to our own [Buttons library](http://alexwolfe.github.io/Buttons/) and click the Customize button. This will open a popup. In this popup you'll notice the input labeled *Namespace*. By default it's just `.button`. Try entering your own base class name like `.my-button`. If you submit this, you will see that the code snippets on the page will update to reflect your new custom base class.

What we've done there is allowed you to pick your own namespace for your button (this is useful if you, for example, need to use Buttons with [Zurb Foundation](http://foundation.zurb.com/) which uses `.button`, or [Twitter Bootstrap](http://getbootstrap.com/2.3.2/) which opts for the class `.btn`; simply use a different class and you'll prevent any chance of a collision).

From within this base class you will define only the shared behaviors of our module. For example, for the Button module, you may wish to set things like the background and text colors, general *box-model* properties, font and perhaps border. Think of this base class as your default version of the module.

```css
.button {
  background-color: #eeeeee;
  display: inline-block;
  border: 1px solid #d4d4d4;
  height: 32px;
  line-height: 30px;
  padding: 0px 25.6px;
  font-weight: 300;
  font-size: 16px;
  font-family: "Helvetica Neue Light", "Helvetica Neue", Helvetica, Arial, "Lucida Grande", sans-serif;
  color: #666666;
  text-shadow: 0 1px 1px white;
  margin: 0;
  text-decoration: none;
  text-align: center;
}
/* ...hover, focus, active states omitted for brevity */
```

We've purposely omitted a couple of css3 properties to make the example easier to digest. We can see that this is the "boiler-plate" of our button and will act as a sensible default. Next we can extend this base with more interesting styles. Let's look at that next.

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

## JavaScript

If you're able to get team-wide consensus (not always an easy thing), there should be an agreement on what things get targeted by JavaScript. Generally, you should try to avoid having CSS classes–meant for styling, structure, or skin–from being targetted inappropriately by JavaScript code. The reason for this, is that it makes it much more difficult to later refactor such classes without inevitibaly borking a JavaScript spec, or, even worse, functionality in the core JavaScript code itself. Some teams even decide that classes meant to act as JavaScript hooks should be prefixed with `js-` to signify to future readers that this code should not be meant for styling, but to act as a logic hook. Conversely, IDs should really never be targetted from CSS, as they are even more ripe to act as JavaScript hooks (of course, there are other problems with having IDs in your CSS–namely that you'll never get any sort of reuse and you'll drive the selector specificity way up!)

Establishing a team-wide convention early on is great if you're dealing with a greenfield project. If not, you have to exercise your "search-fu" to find any potential JavaScript breakage. In project where there's intermingling of DOM and server-side code, such as a Ruby on Rails application that renders ERB pages, you'll have to search there as well. See  *TODO some other section that goes in to search/replace more deeply*

## Shallow Selectors

Another term that you'll see for this is [Depth of Applicability](https://smacss.com/book/applicability) and it, essentially states:

TBD

## TODO Selector performance...right to left browser reads etc.

