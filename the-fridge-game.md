# The Fridge Game

```
fridge-game:
  [
    cls
    [
      'You are in a fridge. What do you want to do?'
      '1. Try to get out.'
      '2. Eat.'
      '3. Die.'
    ]
    [println] each
    {
      1 ['You try to get out. You fail. You die.']
      2 [
        'You eat. You eat some more.'
        'Damn, this food is tasty!'
        'You eat so much you die.'
      ]
      3 ['You die.']
    }
    prompt
    @
    dup null?
    [ drop [ 'Did not understand.' ] ]
    when
    '' <<
    'Play again? write y if you do.' <<
    [println] each
    prompt
    'y' =
      [ fridge-game ]
      [ 'Thanks for playing.' println clr ]
    branch
  ] def

fridge-game
```

Translated from the source at [Happy Learn Haskell Tutorial Vol 1](http://www.happylearnhaskelltutorial.com/1/fridge_the_game.html)