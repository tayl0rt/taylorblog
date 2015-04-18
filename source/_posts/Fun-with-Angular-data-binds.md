title: "Fun with Angular data binds"
date: 2015-04-18 11:59:10
tags: 
---


## Alright! Let's take a look at some fun in AngularJS.

This is definitely going to be a little on the basic side, but that's intentional. I struggled to understand some of the core concepts in AngularJS and as usual sought examples, videos, etc.

I think for a lot of people, the AH HAH!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!... *ahem* moments happen when you sit down and finally take an hour or two to bang out some code.

Maybe you've had a few things start to click and you really have that smile on your face because you're starting to understand, and to me THAT is the time to write. Don't just read about it and forget to try it!

## So what's this all about?

Alright so when we take a look at a forms of user input. We're used to let's say filling out the quantity of an item we are purchasing and then hitting add to cart for example. That's what popped in my head with this particular example. I'm not trying to say the example pertains to that line of thinking, but the opposite actually. If the quantity is left blank maybe the form won't process, right? Stick with me here...

>"*it's really all about context*"

I'm big on actually trying things out like I said before and as a friend of mine encouraged me to think once, it's really all about context. This is tough when you're learning something new because things have no context, and the newer you are (myself included for sure), the harder it is to find context or reasons to code at all. 

The below example is the product of me simply wondering if (and being pretty damn sure that) you could allow the user to control the data, in a way that would trigger events on the page itself. It's one thing to bind an element and an input box, so when you type Hello John, it fills the element with the text 'Hello John', and it's another thing... to say I want a function to trigger, but conditional only if *this* is equal to *this* and only if *that* actually has happened, AND I want the user to have control over it.
 
But when I say it's one thing, then it's another thing.... that might sound a little embellishing towards the latter thing. It's not, this doesn't have to be your magnum opus, and it shouldn't necessarily take you 2 days to finish it. In fact it's the opposite, if you can't find a good tutorial on making directives in AngularJS... Open up a file and try to make a directive, lol.

It may amount to nothing more than you seeing how things could interact in AngularJS; my hope is you will take away at the very least the way the following works (hopefully by you messing with it):
    
    ng-model="" ng-click="" ng-show="
     
### So let's take a look at this:

    <h2 id="text-to-show" ng-show="userInputCheck()">You are able to see me! Everything checks out!</h2>
      	<input id="checkbox" type="checkbox" ng-model="checked"/>
      	<input id="user-input" type="text" ng-model="userInput"/>
      	
So absolutely this is trivial if you *did not* have the user input text field. You'd just have a piece of hidden text that's triggered to show if the checkbox is checked.

You could also have a two part way of messing with it - Checkbox is checked and the hidden text shows AND a user input field to determine what that hidden text actually is.

What I went for was hidden text being shown not only on one condition, but two. What this does is simply require a *tad* more thinking, and a wee bit more code involved. It's a step above trivial without making you slam your head against the wall.

### Walking lasts until you realize you're running.

You don't run after you walk in coding. You simply reach the AH HAH moment and realize you're mid-run. These things can have a snowball effect, so the point of this article really is to demonstrate when you're frustrated with tutorials that don't make sense... or can't find the best examples online, don't give up. Just keep going and keep coding and google until you're eyes bleed. One day you'll wake up and have a brilliant idea that however trivial in the grand scheme of things, will boost your confidence tremendously as you overcome the challenge you've set for *yourself*.

### This is it!

Alrighty head over to https://github.com/tayl0rt/angularDataBindExample and take a look at what I'm talking about code wise. If you don't want to then at least take away the overall point - *don't forget to actually write code*. Thank you!