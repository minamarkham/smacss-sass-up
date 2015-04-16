## 2

Hi! I'm Elyse—I'm a front end architect/developer/designer in Austin. I'm a co-organizer of ATXSass, and also teach for Girl Develop It on occasion.

# 3

Why should I use Sass?

## 3/1

A lot of people recognize the power Sass can offer but mostly it seems like more work, more things to learn, more complicated language, etc etc. But there's a lot of reasons to switch that are more subtle than "ooh, mixins in CSS!" Even though you see tons of shiny, cool animation effects on CodePen using Sass, I would argue that is the least common use of Sass, and may exist only on CodePen.

A lot of people are very resistant to the idea of a CSS preprocessor; why learn another tool, if you already are comfortable with the one you know and it works for you?

## 3/2

Jina Bolton, in her Sass presentations, says "create systems, not pages." We used to do this—about page, home page, etc etc—but now as our apps and projects have gotten significantly more complex, that's a particularly bad plan.

How can you make a framework of code that is reusable and modular and separate from individual pages? Instead of "style the homepage", style the modules that are on the homepage.

Your code should be reusable in as many places as possible, which makes it more efficient to write and debug.

Sass helps you—or forces you—to do that. When you have the powerful tools of Sass available to you, instead of going to use the color picker to grab a shade of grey from your mockup, you know you can just write $grey. It allows you to write reusable code with very little effort.

## 3/5

Library and Utility CSS

Start with your variables, for colors, typefaces and sizes, helpers such as mixins for CSS3, reset CSS if required, any theming, and grid/mediaquery code or plugins such as Susy, Breakpoint, Compass, etc. any @import includes.

## 3/6 

Modules

## 3/7

Structure and Style

Or if you don't have a lot of reusable modules, you may only have individual pages, like on your personal site it might be homepage, about, and contact pages, but the blog posts styles are really the only reusable module. That's OK too—solve for the problem you are presented with.

## 3/8

Tom Genoni wrote a blog post about switching to Sass, in which he says that the best way to learn Sass without getting the insane output is to not use the crazy functionality in Sass.

"Sass is not a replacement for CSS, it’s more like having a CSS assistant who will help you write your code. So when you’re ready to really put it to work I recommend occasional sanity checks on the resulting CSS to see if this “assistant” has created too much repeated code or if the selectors are getting too complicated. Refactoring your Sass will help keep your code clean and you’ll start learning how you can make the best use of it."

I personally think using variables and mixins for obvious things you will reuse (like css3, clearfix, etc) is helpful, but if you are unsure about some of the extend or nesting or functions, don't use them--keep an eye on your code. This is an authoring tool and it's supposed to make your life BETTER, not harder.

# 4

I'm going to talk a little bit about the tools of using Sass—how to install it, what apps and options there are—and then we'll go back to the why and discuss some authoring tricks that help me, and hopefully can help you.

## 4/1

Yes, to install Sass you MAY have to install it via Rails in the command line. The really long and difficult command you have to write is as follows:

## 4/2

When to use terminal: small personal projects that don't require many other tasks done, if you want to learn and get comfortable in Terminal, to quickly compile one file and look at output. Knowing how to use this is a handy skill in your arsenal even if you don't use it as your primary compilation option.

## 4/4

CodeKit helpfully compiles your stylesheets for you into regular or minified CSS, expanded or collapsed, and has LiveReload. It also now does LiveReload in multiple browsers/devices, creates source maps, and easily allows you to add plugins like Foundation, Compass, via Bower. It also does other types of processing, like Haml or Coffeescript.

When to use CodeKit: if you prefer a GUI/apps, you want simple compilation AND livereload w/o using a tool like Grunt, you want to use/play with plugins without manual install.

## 4/5

If using Zurb Foundation, you can install and use the Sass version. This allows you to edit the settings and variables, rather than override their complex code. You can also pick and choose which parts of Foundation you want to import.

You install it with the Foundation command line interface, which uses npm and Bower.

Then you can choose one of two ways to create a project with Foundation: with Compass as the compiler (which is quite slow), and one with Grunt using the libsass compiler. Obviously the Compass one has Compass included, so you have their styles and mixins available to you automatically, but I prefer the Grunt and libsass version. I find it significantly faster. Neither of these came with livereload, though, or running a server, so you'd have to edit the own grunt file to include it. More on that and libsass later.

## 4/6

If you are prototyping, I love Foundation for this. I think it's valuable to use the Sass version, throw in your variables, colors, type, etc, and super-quickly have a sandbox where you can get a working wireframe up. I know a lot of companies that do this, whether its with Foundation, or like Happy Cog, using Compass and the Susy grid.

As Sophie at Happy Cog says, we prototype because "It moves."

## 4/7

"We can define how elements change at different screen sizes, and we can add in movement and interaction so that the site is tangible—something users and our clients can actually experience like a live website. We can test user flows and observe how people interact with the site. Since the prototype is a low-fidelity artifact, we can take what we learn from usability testing and iterate rapidly until we get it right."

## 4/8

Libsass is a compiler for Sass that does not rely on Ruby to generate the CSS. It’s blazingly fast. You have to compile it (in C), if you are using the original version. You can install and compile it yourself with the C compiler, but there are other ways to access libsass' speed.

## 4/9

This speed benchmark by Jo Liss http://www.solitr.com/blog/2014/01/css-preprocessor-benchmark/ tested Libsass as providing a massive (>10x) speed improvement over the original Sass compiled in Ruby, dropping processing time from 2.5 seconds to 0.2 seconds.

She says, "The speed of your CSS preprocessor is important for developer/designer ergonomics. The preprocessing time measured by this benchmark will typically incur as a delay every time you edit the stylesheet sources and hit reload in the browser. Delays below 0.2 to 0.5 seconds tend to be perceived by the human brain as near-instantaneous. The higher the delay, the higher the mental overhead."

I personally, on my last project, saw a drop from about 14seconds to about 2 seconds, which was crazy fast in comparison.

So—we want to be able to use libsass, that's awesome. But I don't feel like trying to deal with a C compiler. Luckily...

## 4/10

Node-sass is a library that provides binding for Node.js to libsass.

This is great if you are using Node, or other JS apps.. or Grunt. Or the Foundation libsass option. They all use the nodesass bind to libsass to compile.

## 4/11

And YES libsass now supports Sass 3.3, so it DOES support maps. This WAS probably the biggest complaint we hear about libsass. So if you use the Foundation libsass version, you can't use maps, or plugins like Susy that require Sass 3.3. OK, you still can't use Susy, but they're working on it!

On screen is a color-guide that Una Kravets made, and it's using the maps functionality to do so. And now it works in libsass!

## 4/12

Sooo... Grunt, Gulp, Broccoli, whatever it is nowadays! When I first started getting in to these, I'd ask what they did and people go, "Oh, they're task runners!" Which I think has become one of those non-answers. It's TRUE but I don't think particularly explanatory if you have never used them or don't know what a task being run might even mean.

Tasks are things like compiling sass, concat/minify js and css, run a local server, live reload, optimize images. Instead of using an app like CodeKit to do that, if we are writing a JS or Rails app, we can write JS to define these tasks, and run them in the Terminal.

If you are using Grunt or Gulp, and don't need Sass 3.3 features like maps, you can use the grunt-sass plugin—not to be confused with grunt-contrib-sass, the ruby version grunt plugin. grunt-sass compiles with libsass and should be very quick in comparison.

## 4/16

There are many Sass plugins, as well, like Compass, Bourbon, Susy, and North, among MANY others. They provide common mixins, vendor prefixes, grids, style guides and documentation, and other helpful authoring tools.


## 4/17

If you are just trying to test something, see if something works, or just want to play around, I recommend sassmeister.com, developed by Jed Foster (http://jedfoster.com/) and Dale Sande (http://www.dalesande.com/).

You can use SCSS or Sass syntax, different/new versions of the Sass compiler, plugins such as Compass, Bootstrap and Foundation, Bourbon, Breakpoint, Jacket, Singularity, Susy, and even True, the testing framework—and now Libsass compiler.



# 5

## 5/2

File and Folder Org
[read slides]

## 5/3

If you are starting a new project—or refactoring an old one—the way you organize your files can be one of the early things you do. I hear questions about this maybe more than anything else: how do you structure your projects?

Like anything, the main answer is: it depends. Every project is different. There are infinite ways to do it, so there is no blanket answer. but there are some best practices that I think most people aim to follow.

## 5/4

Here's how I do it on my blog.

In this case, I did style somewhat by "pages"—but on a small site like this, that's totally fine.
Here's an example of how I did it at my last job. This is a bit simplified, but we had a lot more modules, so grouping and commenting by type was more valuable.

## 5/5

Dale Sande gave a great talk called Clean out your Sass junk drawer, and he goes way in depth on some ways to do this.

"While part of a team developing an enterprise CMS, our process was to decompose a site's UI to it's lowest common elements. From those elements we could then build modules and then finally assemble the view templates. Each step building on the previous. Although my stylesheet management techniques weren't perfect, my concept of UI abstraction was solid. Working with a new team, sans a CMS, I went into the project with the same conceptual understanding, but the outcome was drastically different. The code became increasingly harder to reuse and making simple edits resulted in the reengineering of HTML as well as CSS. Post launch, I sat down and analyzed the code I wrote. I came to the realization that we were engineering our UI (CSS and HTML) from entirely the wrong perspective. We were approaching our development from the full page perspective. Engineering all our visual elements from the outside-in and scoped to a specific view. I started thinking back to the processes I pioneered with the CMS. Patterns established in the framework dictated we start from the elemental perspective; type, colors, forms, basic UI chrome (borders, shadows, icons, etc) all coded first. Once those element styles were completed, it was a matter of applying the skin to the CMS modules. The modules then in-turn were used to assemble the view. It worked quickly and seamlessly. Building the UIs from the inside-out was clearly the solution."

## 5/6

His mantra is "code the element, create the module and assemble the layout."

Elemental partials is where we get to work. Here we write Sass rules that will create your UI foundational layer. _buttons.scss, _forms.scss, _global_design.scss, _reset.scss and _typography.scss all contain Sass rules that will process into CSS. While they will import other partials, mixins and silent placeholder rules, it is important to remember that these files are engineered only to output CSS. Taking buttons as an example; between gradients, :hover and :active states, one could go a little mad over the complexities in styling. It is important to keep your Sass logic out of these files and focus purely on the rules that will produce CSS for your selector. Keeping functional Sass separate from presentational Sass is important in order to maintain readability, search-ability and scaleability of your code. Patterns like placing mixins in the same file as presentational Sass leads to overly complex files to scan and opportunities for accidental pollution of your processed CSS.

## 5/7

Mina Markham wrote a GREAT starter toolkit based on Scalable and Modular Architecture for CSS SMACSS for Sass (SCSS) projects. Styles are broken down into the following groups: Base, Layout, Modules, States, Themes

If you are starting a project and want some guidance on organization, I think this is an awesome, super simple place to start. Unlike a framework that provides all this code for you, Mina's starter is just placeholder docs.. the files are created, but empty, ready for YOUR code!

## 5/9

But won't my code be bloated and horrible!?

## 5/10

Nesting.

This is why you don't nest things in Sass unless they NEED to be. In this case, we really could eliminate the middle two classes—they aren't necessary. However I do want to nest at least the last 2 inside a parent, so that I can namespace and never worry about accidentally using that classname elsewhere and getting a conflict.

## 5/12

You get bloated output when you write bad CSS, when you nest when you don't need to, or when you over-use mixins or extends that aren't necessary. Read your output! YOU as an author are responsible for the output of your code, the exact same way as you are when you write plain CSS.

## 5/13 

Also, in terms of performance and reducing size to the browser, you'll do FAR more by reducing your JS and images than you will reducing your CSS selectors.

"As a general rule, your average stylesheet will increase by ~3k for every 100 lines of uncompressed code. The single ~700-line Sass-generated CSS file for this site — warts and all (i.e., repeated code blocks) — is ~22k uncompressed; minified and compressed: 4k. Even if I inadvertently added another 1300 lines of wasted code on top of this, bringing the file to 2000 lines, the minified and compressed version would still only be about 5k." 

## 5/14

Because Sass offers you the ability to nest your selectors, and you know that having your code encapsulated is the "good way to avoid collisions with other styles", you might find yourself mimicking the DOM in your Sass (bad idea).
So you might write this...

Using the above code, you can predict 100% of the time what's going to happen with your stylesheet. There is no cascading that can beat the specificity …

After compiling the Sass, we take a look at the output....

## 5/16 + gifs


## 5/20

Some other tips for eliminating extra output—other than not matching your HTML in your Sass—are things like the parent selector, placeholder extend, and using them to namespace modules. Not only can this help eliminate extra output, but it can also make AUTHORING a lot easier.


## 5/21

In Sass, the ampersand (&) symbol is used to reference the parent selector in a nested rule.

The & can also be placed after a selector to reverse the nesting order

## 5/24

I like SMACSS style state classes; you can use nesting and the ampersand to namespace them so you can use something like .is-active in a lot of different styles and locations.

## 5/26

Nesting CAN be used to namespace modules, and it can be VERY helpful in this regard. 

## 5/27

Here's a simple example; you want the header nav colors to be different than the footer nav colors, but nothing else—margin, padding, etc, should all be the same.

So here, you style the nav that will all be the same...

And then you can namespace inside the header and footer

And then your output is something like this


## 5/30

@extend is an easy way for one selector to share the styles of another selector, without duplicating the lines of CSS in your output

## 5/31

Where mixins use @include and literally include the lines of code everywhere you write @include, @extend's output comma-delineates the classes. Instead the same 4 lines of CSS duplicated 3x, we have 4 lines.

But note that we have defined .box as a class, so in our output, .box is there.

## 5/34

Sometimes you’ll write styles for a class that you only ever want to @extend, and never want to use directly in your HTML. For our box styles, if that's visual only and the class .box never appears in our HTML, why output it into our CSS if it will never get applied? If you use normal classes and use @extend for this, you end up creating a lot of extra CSS when the stylesheets are generated.

## 5/35

So here you can see it's just removed class .box from the output. Not a major decrease here but if you do this a lot, then you will see much less clutter in your CSS. This is especially helpful for visual helpers, like typography classes; I use it for named sizes and a "meta" style, which is ~20-40 lines of code in my CSS that I can eliminate with placeholders. Again, not a HUGE amount of file size.. but less junk. And when you are writing a BIG project, it adds up.

## 5/36

In the past I've used a mixin for the clearfix, but as we know, that includes that clearfix code everywhere you include it.

Instead, let's try using the placeholder––or silent class––selector. This will concatenate all the selectors that you use it on AND this way nothing gets compiled to CSS unless we actually use it. This might not be best for ENORMOUS apps, but it's definitely less output.

## 5/39

Sass makes it much easier to write MQs than CSS—you can include your MQ inside your selector, rather than the other way around.

## 5/41

You can even go one step furthur and make variables for your breakpoints, so you don't have to remember them.

## 5/42

Taking it one step furthur, as popularized by Chris Coyier, you can write a breakpoint mixin.

This is another good example of a Sass if statement; here we are defining a mixin with an argument of $point, and then saying, if my $point value that gets passed in my include is large, then print out this mediaquery, and the @content of it inside it.

This is a much nicer way to author mediaqueries; it makes it easy to see what styles are related to what MQ size, you never have to write the #s again, or go searching through 2 different files to debug styles.

## 5/44 + 45

Say you need a variable for text color in your project. You could call it $text-color, or should you call it $color-text? How do you decide? Choosing one at random can contribute to a lack of structure as the number of variables in your project increases. As experience shows, we often forget exactly how we named variables for particular projects.

## 5/46

A better way to name these variables would be to start with the generic word they all share in common: blue. Then we can get more specific from left to right:

This not only helps in recollection, but will allow a text editor (such as Sublime Text, Coda etc.) to easily suggest colors. This way you don't have to memorize exactly how you named your variables. Rather, you can start generically and get more specific as the text editor auto-suggests variable names. All you have to remember is you want a color of blue. So you begin typing $blue and you can get a list of all the different blues you've created!


## 5/47+48

Using a consistent naming convention, we can create a colors (or vars) .scss file and put in our colors, typography, etc.

## 5/49

Then we can create theme files; a default, a dark, a light, etc, using the color vars against more abstracted var names like primary, secondary, button-bg, etc.

## 5/50

Then we have the ability to change out the theme we are using pretty much on the fly, by picking which file we import.

## 5/51

Gutter color for vars!

## 5/52

In Sass, the JS style single-line comments with the two slashes are hidden from your output, which is great, because you can do a ton of commenting without anything showing up.

However, there are occasions where you may WANT your comments to show up in your compiled CSS—recently I was trying to do this so that I could see where imported files began and ended in my output. Helpfully, the CSS style slash-asterisk comments DO show up in output! Handy!

## 5/53

I also want to talk about commenting really quickly!

Comment each file to explain what is in it
Comment every large section of CSS
Comment individual items that need clarification
Be consistent
Imagine the next person who inherits your codebase. Your comments should be a guide for them through your CSS. Especially with potentially confusing Sass variables and mixins, it's not enough to have a comment that says "This is a mixin for a CSS3 gradient with eighteen arguments". Better to also add instructions on how to use. If you have a style guide or wiki docs, reference that page/section as well!


I use output comments to delineate sections in my output file, to make it easier to read through (when I need to, which is sometimes, and I do like to look at it). I use non-output comments to show how things work, how things should be used, etc.


## 5/54

But that's OK! If you try to document everything in your code at once you will most likely give up, because there's SO MANY THINGS, and weird bugs, and hacks...

But if you start one piece, one module at a time, you'll end up with a fully documented codebase eventually. So: Document as you go! If you make something new or refactor something, document it. Comment it and make a doc page, whether that's a UI Style Guide or a wiki page or whatever.

## 5/57-61

This is kind of a silly example, as there are many more sophisticated ways to do this, BUT this is honestly a thing I have used in the past. Sophistication is great when you NEED it, but my favorite thing about Sass is it provides simple ways like this to do something quickly that would be hard in CSS, but you also don't need a whole tool for.

I used something much like this at my last job; I was trying to figure out good layouts/grid systems, and Susy, a Sass plugin for grids, has this awesome background-gradient grid overlay. I needed to keep turning it on and off, so in my stylesheet I was working in, I just did that via a variable. Super quick. And NO it does NOT go into production!

## 5/62 + gif

COULD YOU, with something cooler and more time consuming? Sure. But remember, Sass should be an AUTHORING TOOL for you! If it's not working for YOU, then do what works instead. If that's crazy intense Grunt plugins.. FINE. If it's simple if statements in Sass? FINE. If it's only using the ampersand selector and importing files, FINE. Make Sass work for you. Don't feel like you have to do this hot new thing just because everyone is.. do what makes your workflow better, easier, and more functional. Every project is different.

# 6

Sass is an authoring tool. make it work for you!
