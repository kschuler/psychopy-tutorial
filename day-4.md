## Day 4: Adding code snippets for more complex handling

### Demo

Imagine that we want to play a simple matching game in which the child hears the noun and is asked to select the correct image. Using what we already have learned, you could use a rating component or a keypress component that stores the correct answer. But what if you want the subject to click on the picture with the mouse?  This requires adding a mouse component and using some simple code.  You'll want to add this code every *frame* because you want the mouse to listen for clicks as frequently as possible.

```python
for stimulus in [noun_1, noun_2]:
  if mouse.isPressedIn(stimulus):
    if stimulus.image == corrAns:
      thisExp.addData('correct', 'True')
    else: 
      thisExp.addData('correct', 'False')
    continueRoutine = False
    break
```

Great! That works. But what if you want the stimulus to DO something whenever iti s clicked?  For example, maybe you want the stimulus to turn a little transparent to indicate it was the option selected?  These are called "conditionals" and they always require the use of code.

You'll also need to make changes to component *attributes* via code.  All psychopy attributes are available via the API: [http://www.psychopy.org/api/api.html](http://www.psychopy.org/api/api.html).  Most attributes can be changed in one of two ways:

##### 1. By setting the attribute equal to a new value

```python
someComponent.someAttribute = newValue

# for example
image.opacity = 1.0
```

##### 2. By using the function for changing the attribute

```python
someComponent.changeAttributeFunction(newValue)

# for example
image.setOpacity(newValue)
```

So to make one of the images change to transparent we could do the following.

```python
for stimulus in [noun_1, noun_2]:
  if mouse.isPressedIn(stimulus):
    if stimulus.image == corrAns:
      thisExp.addData('correct', 'True')
      stimulus.setOpacity(0.5)
      stimulus.draw()
      win.flip()
      core.wait(0.5)
    else:
      thisExp.addData('correct', 'False')
    stimulus.setOpacity(1.0)
    continueRoutine = False
    break
```

Note that we had to *draw* the stimulus to the screen again, *flip* the window again, and *wait* a little bit so that we are able to observe the change.

### Activity

1. Add an additional two stimuli to the matching game (norg and spad)
2. Attempt to make a square appear around the stimulus when it is clicked.  The square should appear red if an incorrect answer is clicked and green if the correct answer is clicked.

*Hint:* Think about what *attributes* a polygon (also called a ShapeStim) has.  For example, color.  You may need to use the 
