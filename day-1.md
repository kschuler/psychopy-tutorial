## Day 1: Overview & Creating an Exposure Phase

### Before we begin
- Make sure PsychoPy is installed
- Download the files you will need for the tutorial

### Agenda
- [Overview](#Overview) (10 mins)
  - Introduce PsychoPy and its builder method
- [Demo](#Demo) (30 mins)
  - Planning and storyboarding an experiment
  - Creating the exposure phase of the experiment
- [Activity](#Activity) (50 mins)
  - Find a partner or 2 (coding buddy)
  - Plan and storyboard the "try me" experiment
  - Create the exposure phase of the "try me" experiment

### Overview
- PsychoPy is an experiment building software, similiar to E-prime or MATLAB.  It is my preferred metod of creating experiments in the lab because it is (1) free, (2) has great documentation and help, and (3) is actively mantained.
  - Documentation: [http://psychopy.org/builder/builder.html]()
  - Q&A Help site (new questions asked here): [https://discourse.psychopy.org/]()
  - Old Q&A Help site (no longer active): [https://groups.google.com/forum/#!forum/psychopy-users]()
- PsychoPy can be used as a python package for programming experiments, or via a GUI experiment builder that requires little to no programming at all.  Today, we are going to learn how to use the builder method.

- The builder has three main panels: routines, flow, and components.  You build your experiment by adding components to routines (typically trials) and inserting them into a flow (the order you want them to occur in your experiment).  You can use loops around routines or groups of routines for even more flexibility.  I will demonstrate all of these things in a moment.  After the demonstration, you'll create your own experiment with a partner and I'll walk around to answer questions and help.


### Demo

> We want to create an artificial language learning experiment, which consists of an exposure phase, a production test, and a rating test.  In the exposure phase, we want to expose participants to sentences while they see a corresponding picture.  In the production test, we want participants to hear a singular sentence paired with the corresponding picture and then be asked to provide the plural sentences when viewing the plural image. In the rating test, we want participants see a picture and hear a test sentence, and then rate on a scale from 1 to 5 whether they think that sentence matches the picture.  We want to make sure we collect some information from the participant, like their participant id number, gender, and what language condition they will participate in.
> 
> Plan and storyboard this experiment, then create dialog box and the exposure phase.  (Production and rating tests will be completed later in the week.)

-	Experiment creation always begins with planning and storyboarding.  You should make sure you know exactly what you want to do in your experiment before you begin.  What stimuli you’ll use, what your conditions will be, exactly what subjects should see and hear – even down to exactly where on the screen you want things to appear.

-	After that, you can begin adding routines to your experiment.  Inside each routine, you’ll include the components you need to create your experiment.  We will demonstrate how to do this now.

-	Sometimes you want to do things that seem more complex than creating simple routines and components with the builder.  For example: progress bars or having different subjects in different conditions.  We will demonstrate a few ways of accomplishing these more complex things in the builder.

- Progress bar 3 ways.  There are a number of ways you could make a progress bar.  If you only need the bar to update to reflect each phase of the experiment, (1) the easiest thing to do might be to create an images of a progress bar at different states (e.g. the way you want it to look for all 4 phases of the experiment).  You could then display each different image at each different phase, which would give the impression of a progress bar.   (2) Similarly, you could accomplish this same thing with two polygons, one that stays static (the empty part of the progress bar) and one that gets bigger as the phases go on.  (3) If you need the progress bar to update by trial, you’ll have to insert a dynamic code snippet to retrieve the total number of trials in the condition and the number of trials that have been completed so far.  Each loop contains this information in:
    - Total number of trials: `loopName.nTotal`
    - Current trial number: `loopName.thisN`
- You can use these values to change the size of the inner polygon as the trial numbers increase.  The simplest way to do this is in the size value of the polygon itself.  If the outer polygon is something like 500 pixels wide by 50 pixels wide, you could do:
    - Set every repeat, because you want this to dynamically update
    - `[(loopName.thisN/loopName.nTotal) *500, 40]`
- Two conditions 3 ways. There are also a number of ways you could run different conditions, or versions, of your experiment.  (1) The simplest possible way to do this is to simply create a completely separate .pxyexp file.  You could name one “run-language-b.psyexp” and the other “run-condition-b.psyexp”.  You’d want to make sure you note the experiment condition somewhere (probably in the dialog box), so that the data file updates accordingly.  (2) Another simple approach is to have the name of the condition file be the name of you input into the dialog box. (3) If you want to allow a selection in the dialog box to enable you to create a second condition, another thing you could do is insert a code snippet at the beginning of the experiment that sets the condition files for the experiment.  For example, if you have to language conditions, A and B, we might have the experimenter enter A or B into the dialog box for language.  This information would then be stored in expInfo:
    - `expInfo[‘language’]`
    - You can use this value to set the condition file:
  ```python
  If expInfo[‘language’] == “A”:
      exposureFile = “conditions/language-a-exposure.xlsx”
  elseif expInfo[‘language’] == “B”:
      exposureFile = “conditions/language-b-exposure.xlsx”
 ```

### Activity

Select a partner/coding buddy. You will work on this together.  You should both create the experiment on your computers, but your experiments should be identical. 

> Now you want to create another artificial language experiment.  This experiment also has an exposure phase, production test, and rating test.  However, this time, your stimuli are videos instead of images.  Create the following parts of the experiment in the following ways:

1.	Collect the subject’s ID number, gender, handedness, and age.
2.	This experiment has two language conditions (below).  Ensure that you are able to run both conditions of your experiment.
  - Language A includes all 5 sentence and video pairs repeated twice during exposure.
  - Language B includes all 5 sentence and video pairs repeated once during exposure.
3.	Add a progress bar that updates on every trial.  Add text next to the progress bar that shows what phase of the experiment you are in (e.g. “exposure phase”).
4.	Display the video in the top left corner of the screen during exposure.
5.	Allow the video to display for 1.0 seconds before the sound component plays during exposure.
6.	Add a routine that includes instructions for the exposure phase (e.g. text that describes what the subject will do during the exposure).
