---
layout: post
nav: blog
title: Indianapolis
theme: public safety
comments: true
---

Working on ThemeRoller was a lot of fun and it taught me a lot about client-side styling and user interfaces in general.
It has also stood out in my mind as I continue to interact with more and more CSS frameworks, and I keep longing for more
tools like ThemeRoller.

Somewhere along the line with ThemeRoller, someone asked me, "Why is this tool specific to one framework?
Couldn't you create a tool that would work with any CSS file?". My immediate reaction was that this
person clearly didn't understand the complexity of the problem (turns out, it's not that complex at all).

But the thing is, even after wrapping up my involvement with jQuery Mobile, that person's question was still echoing in
the back of my mind. Would it be that hard to develop some framework-agnostic, WYSIWYG theme creation tool?

My immediate thought was to improve upon current developer tools. We all know Firebug and Chrome's developer tools work
just fine for debugging and quick styling, but I think the app I have in mind would do more for non-developers
beginning to dabble in some frameworks like jQuery Mobile or Twitter Bootstrap.

I could potentially put a little time and effort into forking/extending a tool like Firebug and adding some nice color
pickers and number spinners, but at the end of the day it wouldn't reach as many people or be all that usable.

So here's my thought. I want to create an extensible and configurable theming application that any developer can
grab, tweak, and apply for his specific framework. This way, each framework could potentially have it's own
customized version of the tool, but at the end of the day the basic ingredients are all the same.

What are those ingredients? Glad you asked:

1. Fast, light-weight parsing of any CSS file
2. UI elements specialized towards various CSS rules
3. Colorpicker
4. An inspector tool for point and click edits
5. Draggable colors with customizable behaviors
6. Undo/Redo Logs of every action the user makes
7. Downloadable/Shareable themes

As far as parsing goes, for now I'm thinking that the API will mostly handle the business logic of the actual skinning.
But the rules that a user has access to will need to be specified by the developer. This can be done with some esoteric CSS
comment for every rule that needs to be represented in the UI. Or, more likely, some specific JSON that the developer could write
out quickly that would list which rules are editable, and how they are grouped.

The potential for this app extends beyond just the big-name frameworks. The tool could also be used when designing a site
for a client. I'll give you a scenario. You whip up a site design, and your client is unhappy with your choice of typeface,
color, spacing, etc, but he likes the overall layout. Why bother iterating on color choices? Design a solid layout, and then let
the clients skin the page themselves. All you do is provide a base theme that can be easily tweaked. Sounds nice right?

Ok, so there's the overall outline. I'd love to get some feedback on the idea, as well as any questions/suggestions you
might have about implementing this thing. Give me a shout-out on
[Twitter](http://twitter.com/tybenz),
[email](mailto:tabenziger@gmail.com) me or submit a ticket on the [Github](https://github.com/themebot/themebot).

Note: This project is nothing more than a thought for now, so no, there's no source code to look at. Check back later for
updates. It will be soon.
