---
layout: post
nav: blog
title: Albuquerque
theme: economic development
comments: true
---

For my first post, I'd like to talk a little about patterns.

Most programmers are puzzle solvers. We sit and tinker all day trying to solve interesting
problems, or most often, solving problems we've created ourselves. The most rewarding part of this puzzle solving,
is when a pattern is identified, and an association is made. Simplifying these patterns into reusable pieces of code
is what makes programming fun. I know I'm most proud of code that I've written that is highly reusable.

What typically happens is that programmers will put off writing truly reusable code until absolutely necessary. I do,
and so does everyone else. I've outlined a little bit of what typical puzzle solving looks like (at least for me):


1. Button Mashing
  - I start prototyping a solution to a problem
  - I throw good coding practices out the window and just try to get results on the screen
2. Refactoring
  - I spend hours and hours tweaking code to be more readable/efficient/reusable
3. Epiphany
  - I realize some subset of my new code is similar to something I've written before
  - I create some small utility/API that is tailor-made for a certain coding pattern

Quickly, I'll say that the big time-suck in Step 2 can be reduced if better code is written from the start.
Understandably, outside factors can make this impractical (e.g. time constraints, rapid prototyping, etc).
I'd still recommend finding the balance between an accurate, fast prototype, and a clean implementation as much as possible.

Now, where does the pattern come in? What I'd really like to focus on is Step 3. This Epiphany is usually what spawns excellent
libaries/widgets/gems/APIs.

Let's walk through a more concrete example.

Recently, I was messing around with Ruby on Rails and I had started added some client-side/server-side communication
via AJAX. I'll take you through a smaller, similar app and see if you can spot the pattern.

Let's design a Grocery List application. The user can create Lists which contain multiple Items.
We'll have a unalterable, finite set of possible items the user might want on a list.
If we wanted to create a page where the list can be built out on the client-side and then pushed to the server to save the list,
we'd need a way of querying for items, as well as some button to submit the completed list.

Here's some code:
{% highlight html %}
<!-- Submit this form with the name of the item to get back data from server -->
<form id="get-items" action="/items" method="get" data-remote="true">
    <input type="text" name="items[name]" />

    <input type="submit" />
</form>
<table id="grocery-list">
    <tbody>
        <tr>
            <td>1.</td>
            <td>First Item</td>
        </tr>
        <!-- Add new row here with the new item -->
    </tbody>
</table>
{% endhighlight %}

And some more:

{% highlight javascript %}
// JS to grab data passed back from server and append row to the table
$( "#get-items" ).bind( "ajax:success", function( evt, data, status, xhr ) {
    var data = JSON.parse( xhr.responseText );

    listData.push( data ); //listData = global array of Items
    $( "#grocery-list tbody" ).append( "<tr><td>" + itemCount +
        ".</td><td>" + data.name + "</td></tr>" );
});
{% endhighlight %}

And some more:

{% highlight javascript %}
// User clicks the save-list button and gets back
// a confirmation message from the server
$( "button#save-list" ).click( function() {
    $.ajax({
        url: "/lists",
        type: "post",
        data: listData,
        dataType: 'json',
        success: function( response ) {
            var data = JSON.parse( response );

            $( "body" ).append( '<div class="confirmation-message">' +
                data.confirm + '</div>' );
        }
    })
});
{% endhighlight %}

Notice the pattern? It's actually something that is quite common in web apps. When submitting data/requests via AJAX,
there is always some sort of follow-up action performed on the client side, typically appending some new set of markup
somewhere to display response data.

So I decided to create a generic way to respond to these AJAX calls. By leveraging a templating tool like
[mustache.js](http://mustache.github.com/), or
[underscore](http://underscorejs.org/#template), it was easy to write a utility to listen
for AJAX responses, and append a template, populated with the response data.
I found this tool incredibly useful, and I'm still working on making it
more universal to the task. It's called AjaxAppend and you can read more
about it [here](/projects/ajaxappend).

You see that with a simple example like one above, pointing out these patterns in your mind can save you, and potentially others,
a lot of time in the long run (provided you take the time to do something about it).
Now when I need this type of AJAX/JSON/Markup workflow in an app, I write a few lines of JS, and I'm done.

So there it is.

Bad Code -> Pattern -> Simplify Problem -> Widget/Plugin/Function/API/etc

What I've outlined here, is a workflow for putting together reusable utilities. While it may seem slow and imperfect,
the truth is there aren't a lot of other options. Most programmers don't have the gift of foresight, so for now, this retroactive
simplification of repetitive code will have to do. Make sure you keep your eyes peeled for patterns that can be taken advantage of,
and tweet/message me some patterns you've identified and what you did about it.
