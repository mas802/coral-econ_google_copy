# Semi-automatic testing with coral.polyp.robot #

Automatically testing of a complete experiment is often challenging, as often it includes proper display of the interface as well as interactive components.
CORAL leverages here that the view provided to the participant is
a HTML document, that can be evaluated and responded to by
machines.
The key is a property called **coral.polyp.robot=robot.js**.
This property allows to specify a JavaScript file, that is run on
the view once it is fully loaded from the server.
This allow to very easily simulate participants for testing purposes.

A standard implentation of the **robot.js** script (provided in the example) will simply go through every input item on the page, then subject this to a list of checks if it can respond to the item
and respond accordingly.
It is quite myopic in the sense that it has no information about the previous or future stages of the experiment, only about what is presented in the current page.
A more elaborate setup could be thought of where more information about the experiment is provided as hidden elements which would allow this robot to be more sophisticated.
But this would go beyond the space or pure testing for functionality.


# Details #

Experiment stages with input fields for experimental participant choices can be automated within the robot.js script.  The robot script is activated in the **.properties** file by these lines

```
coral.polyp.number = 5
coral.polyp.robot = robot.js
```

where the coral.polyp.number is the number of agents to play the game, and coral.polyp.robot is the location of the robot script.

For example, if a participant is required to enter a unique numeric identifier, which would be given by the experimenter, and the input field has **name='number'**, then the robot while input a value, say a five digit number, into that field as follows.

```
if ( ref.name == "number" ) {
    ref.value = Math.round(Math.random()*89999)+10000;
}
```

It must be remembered that all agents are playing the game simultaneously and the robot is ignorant of the other players (and his past and future actions).  Also remember that the script will run at all stages of the game, so every validated input field in the game must be given an input by the robot for the game to proceed in an automated fashion.

If the input field has a particular correct input that allows the experiment to proceed, that exact input can be inserted as follows, where the name of the input field is quiz1, and the value which is validated as TRUE is 8.

```
if ( ref.name == "quiz1" ) {
    ref.value=8;
}
```

Radio buttons are a bit more difficult to handle than simple input fields. Several options exist:

```
if ( ref.name == "radiobuttonname" ) {
     ref.checked = 'checked';
}
```

This will just check every radio button with the name "radiobutton"to be checked, leading to the result that the last radio button will be the activated one in the end.

```
if ( ref.name == "radiobuttonname" ) {
     if ( ref.value == 1 ) {
       ref.checked = 'checked';
    }
}
```

This will get the button with value==1 checked.

```
if ( ref.name == "radiobuttonname" ) {
     if ( Math.random() > 0.5 ) {
       ref.checked = 'checked';
    }
}
```

This gives each button a 0.5 chance of being checked when encountered, this will have a bias towards the later buttons though (hence it is not good if you want to have a true random distribution – I haven't encountered the need for this yet).