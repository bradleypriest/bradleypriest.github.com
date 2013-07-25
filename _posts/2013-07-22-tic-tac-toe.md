---
layout: post
title: "Ember Tic Tac Toe"
guid: "ember-tic-tac-toe"
category:
tags: [emberjs, useless-code]
---
{% include JB/setup %}

Every now and then it's nice to build something completely and utterly useless just for the hell of it.

On Sunday, I sat down and spent a couple of hours building Tic-Tac-Toe in EmberJS.
Although Ember is almost definitely the wrong hammer for the nail, it gave me a chance to refresh the basics.

To check out the final product and code visit [http://bl.ocks.org/bradleypriest/6051289](http://bl.ocks.org/bradleypriest/6051289).

There are plenty of Ember getting started tutorials out there, but they all seem a little too useful for my tastes, so let's walk through building Tic-Tac-Toe in Ember.

## Getting Started

I started out with the [JSBin template](http://jsbin.com/ucanam/239/edit) from the official Ember contributing guide.

Firstly, we're going to need nine objects to represent the tic-tac-toe squares, so we'll set up the IndexRoute's model
function to return an array of empty objects.

Then we'll make sure to set the `App.IndexController` to be an `Ember.ArrayController`, so we get all the `ArrayProxy` goodness.

And we'll also add some CSS to wrap them into a 3x3 grid.

{% highlight js %}
App.IndexRoute = Ember.Route.extend({
  model: function(){
    return [{},{},{},{},{},{},{},{},{}]
  }
});
App.IndexController = Ember.ArrayController.extend();
{% endhighlight %}

Next up let's set up the basic template and CSS:

{% highlight html %}
<section class="box-wrapper">
  {{ "{{" }}#each controller}}
      <div class="box">
      </div>
  {{ "{{" }}/each}}
</section>
{% endhighlight %}

{% highlight css %}
.box {
   border: 1px solid;
   border-radius: 3px;
   height: 100px;
   width: 100px !important;
   display: inline-block;
   font-size: 100px;
   line-height: 100px;
   text-align: center;
   font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
 }
 .box-wrapper {
   width: 316px;
 }
{% endhighlight %}

<a class="jsbin-embed" href="http://jsbin.com/ucanam/433/embed?live">JS Bin</a>

So far, so good. As long as you're happy drawing on your monitor with a whiteboard marker, we've got a perfectly functional board... not so much? Ok, let's keep going instead.

## X Marks the spot

A little bit of interactivity perhaps. Ok, well let's say if you click on a box, we mark it with an X.
So how do we go about that, let's set a `userSelected` flag on the object once you've clicked.

{% highlight html %}
<section class="box-wrapper">
  {{ "{{" }}#each controller}}
    <div class="box" {{ "{{" }}action selectBox this}}>
      {{ "{{" }}#if userSelected}}
        X
      {{ "{{" }}/if}}
    </div>
  {{ "{{" }}/each}}
</section>
{% endhighlight %}
{% highlight js %}
App.IndexController = Ember.ArrayController.extend({
  selectBox: function(box) {
    Ember.set(box, 'userSelected', true);
  }
});
{% endhighlight %}

<a class="jsbin-embed" href="http://jsbin.com/ucanam/431/embed?live">JS Bin</a>
Great, so now when we select a square, we get a nice pretty X in it.
However, it's pretty easy to win a game when you don't have an opponent.

## Player 2

To make sure we don't get shown up too badly, we'll start with a pretty dumb AI opponent, it'll
just pick at random from all of the available moves.

While we're at it we'll make things a little easier on ourselves by defining an `App.Box` so we can use Ember's magical computed properties.

{% highlight js %}
 App.Box = Ember.Object.extend({
   selected: Ember.computed.or('userSelected', 'computerSelected')
 });

 App.IndexRoute = Ember.Route.extend({
   model: function(){
     return [{},{},{},{},{},{},{},{},{}].map(function(){
       return App.Box.create();
    });
   }
 });
{% endhighlight %}

Now let's add an `unselectedContent` property to our controller, and then every time the player
takes a turn the computer will take theirs.

{% highlight js %}
App.IndexController = Ember.ArrayController.extend({
  selectBox: function(box) {
    if (box.get('selected')) { return; }
    Ember.set(box, 'userSelected', true);
    this.performMove();
  },

  unselectedContent : function() {
    return this.get('content').rejectProperty('selected')
  }.property('@each.selected'),

  performMove: function() {
    var available = this.get('unselectedContent');
    var selected = this.selectMove();
    available[selected].set('computerSelected', true);
  },

  selectMove: function() {
    var available = this.get('unselectedContent');
    return Math.floor((available.get('length') * Math.random()));
  }
});
{% endhighlight %}

{% highlight html %}
<section class="box-wrapper">
  {{ "{{" }}#each controller}}
    <div class="box" {{ "{{" }}action selectBox this}}>
      {{ "{{" }}#if selected}}
        {{ "{{" }}#if userSelected}}
          X
        {{ "{{" }}/if}}
        {{ "{{" }}#if computerSelected}}
          O
        {{ "{{" }}/if}}
      {{ "{{" }}else}}
        &nbsp;
      {{ "{{" }}/if}}
    </div>
  {{ "{{" }}/each}}
</section>
{% endhighlight %}
As you can see, we make a quick check to be sure the player has chosen an empty square, and then your opponent randomly chooses one..

<a class="jsbin-embed" href="http://jsbin.com/ucanam/434/embed?live">JS Bin</a>

## Winning is Everything
Ok, now we have a two player tic-tac-toe game. I trust you all to play fair and square, but let's let the computer decide when the game has been won to be safe.

We'll start by hardcoding all the possible winning combinations (I'm sure there's a smarter way of doing this but YOLO)

{% highlight js %}
App.IndexController = Ember.ArrayController.extend({
  lines: [[0, 1, 2], [3, 4, 5], [6, 7, 8], [0, 3, 6], [1, 4, 7], [2, 5, 8], [0, 4, 8], [2, 4, 6]],
  //...
})
{% endhighlight %}

And we'll write some code to compare the player's square's indices against all of the possible winning layouts.
We have a function `userWins` which calculates all the player's indices and intersects them with all the possible winning rows.
Basically, if the intersection returns 3 values then the game has been won.

{% highlight js %}
App.IndexController = Ember.ArrayController.extend({
  //...
  userIndices: function() {
    return this._indicesForProperty('userSelected');
  }.property('unselectedContent'),

  computerIndices: function() {
    return this._indicesForProperty('computerSelected');
  }.property('unselectedContent'),

  _indicesForProperty: function(prop) {
    return this.get('content').map(function(item, index){
      if(item.get(prop)){ return index; }
    }).compact();
  },

  userWins: function() {
    return this._hasWinningMove(this.get('userIndices'));
  },

  computerWins: function() {
    return this._hasWinningMove(this.get('computerIndices'));
  },

  _hasWinningMove: function(indices) {
    return this.get('lines').some(function(match) {
      return Ember.EnumerableUtils.intersection(match, indices).length === 3;
    });
  }
  //...
});
{% endhighlight %}

Now let's call `userWins` and `computerWins` every time a move is taken.

{% highlight js %}
App.IndexController = Ember.ArrayController.extend({
  //...
  selectBox: function(box) {
    if (box.get('selected')) { return; }
    box.set('userSelected', true);
    if (this.userWins()) {
      this._notify("Congratulations. You beat a random number generator");
    } else if(!this.get('unselectedContent').length) {
      this._notify("A draw? Is that the best you can do");
    } else {
      this.performMove();
    }
  },
  performMove: function() {
    var available = this.get('unselectedContent');
    var selected = this.selectMove();
    available[selected].set('computerSelected', true);
    if (this.computerWins()) {
      this._notify("Ouch. You lost to a random number generator");
    }
  },
  _notify: function(msg) {
     Ember.run.next(function(){
       alert(msg);
     });
   }
  //...
})
{% endhighlight %}

<a class="jsbin-embed" href="http://jsbin.com/ixomir/2/embed?live">Ember-Tic</a>

## Wrap-up

Now wasn't that easy, if you read the final codebase, you'll see I made a couple more tweaks.
- Adding a reset board button
- Changing the wrapper div's to anchor tags so it works on mobile

Check out the final code and give it a go at [http://bl.ocks.org/bradleypriest/6051289](http://bl.ocks.org/bradleypriest/6051289)

The next step would be to make the UI a little smarter, I would probably check for any intersections that return two
matches and see if the missing index is still empty, but I'll leave that as an exercise for the reader.

Have a great day, now go building something utterly useless and let me know [@bradleypriest](https://twitter.com/bradleypriest)

<script src="http://static.jsbin.com/js/embed.js">

</script>