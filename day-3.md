## Day 3: Creating Production, Rating, or 2AFC Test

### Agenda
- Review common errors
- Production test demo
- Rating test example demo
- 2AFC test example demo

### Review common errors
1. Spelling
2. Location - where things are saved; relative paths
3. Set every repeat
4. $ for variables
5. Attribute errors - size too small to see, gray text on gray background, position offscreen, sound volume to 0, units
6. Draw order
7. Cached experiment - delete the lastrun.py file


### Production test demo
- For our production test, let's first add the stimuli we want to present.  For this example, we will show an image and simply ask participants to produce the sentece that goes with that image.  
- There is a microphone component, but at this time I cannot strongly recommend using it.

### Rating test demo
- As with the production test, we will first add the stimuli we want to present.  For the rating test, participants will see an image and hear a corresponding sentence.  We will ask them to rate this sentences on a scale from 1-5.
- Psychopy has a RatingScale component that you can add to any routine.  Responses can be made with the keyboard or the mouse.  There are some basic options for how the scale is displayed which we will demonstrate now.  You can view descriptions of these options on the psychopy website: [http://www.psychopy.org/builder/components/ratingscale.html](http://www.psychopy.org/builder/components/ratingscale.html)


### 2AFC test demo
- Again, let's first add the stimuli we want to present.  For the 2AFC test, we want participants to see an image and hear two possible sentences.
- Then, we want them choose between two options.  We could do this with a keyboard component, or with a rating scale component.  
