# How to get the stats of my character right

This is a how-to that explains how to edit a character so that its computed stats do matchs those found in-game.
While this was very useful before we had the 'Import from local client' feature, it is almost useless now.
The import process shall build a character configuration that closely matches the one in-game.
Some mismatches or misses can still occur, and the edition capability shall allow to fix this.

## Create you character
Obviously, you should create a character with the right class and race. Both do contribute to base stats.

## Create a character configuration
Here the most important thing is to set the right level. It does contribute a lot to base stats.

## Gear
Obviously, your character must have the right gear at each slot. For each piece of gear, you should check:
- stats (really?)
If stats are not right, then probably:
- you did not choose the right item. Some items exist with the same name at different levels or with different stat flavours.
- if the item is right, then maybe the item level is not right. Change the item level. It shall update the stats accordingly.
- if item and item level are right, you may have to edit stats using one of the provided custom stats modes (set, add, merge).

## Buffs
In the buffs section, you will have to setup a collection of things that may changes the stats:
- traits from your current trait tree (no trait tree edition yet, but all traits are there)
- racial traits
- buffs from consumables (for instance, hope tokens)
- hope buffs that come from being at the right place (in Bree, or near a free-people star like Aragorn, Elrond...). Hope give additional morale.
- buffs from being near a Captain (In Defence of Middle Earth...)

## Stat tomes
Stat tomes may give some points in the major stats (Might, Agility, Vitality, Will, Fate).

## Virtues
If stats are still a bit wrong, then let's have a look at the virtues.
Since both active and passive virtues do contribute to stats, you shall set the right tier for each and every virtue. And of course, select the right ones as active ones.

## What's next
At this point, most stats shall be ok. May be you'll get a few points difference between the simulated character and the in-game character. That's probably due to roundings here and there.
If a stat is really wrong, then:
- you missed something in the list of things presented here,
- it might be a bug!

## How to submit a stats bug
First step is to export the current character configuration. This will produce an XML file where you told it to.
Please send to lotrocompanion@gmail.com:
- the character data XML file
- screenshots of your ingame values (the more I get, the higher the chance to find and fix the bug):
  - character form
  - tooltip of the wrong derivated stats (percentage) if needed,
  - trait tree
  - racial traits page
  - virtues page
  - tooltips of the active buffs
  - I probably miss things
 
 ## Tools to track what's wrong
 You can use tools to find out what's wrong:
 - the detailed stats window,
 - the contributions window.
