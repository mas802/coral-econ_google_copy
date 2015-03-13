# Automatic Screenshots #

There are currently two ways to create screenshots of your experiment, both with their advantages and disadvantages. The first one writes a continouse html file with all screens sent from the server, while the second one involves using a [robot](robot.md) but writes a seperate PNG file for each screen. If unsure go with the first approach.

## 1. Screenwriter approach (produces one html file) ##

The screenwriter approach is easiest to implement, you just add the following line to your coral.properties file:

```
coral.head.screenwriter = true
```

After the experiment has run you will find a .html file for each client connected in the server folder. Note that if your experiment involves repated stages with some JavaScript that affects the display, the results might not work out as expected.


## 2. Robot approach (produces single png files) ##

To create screenshots this way, we just have let the robot tell the client to take a screenshot and send it back to the server. First we have to get the information which page we are on into the template, the easiest way to do this is to include a unique identifyer in the header.vm file (just under the `<form action="exp://host/exp" >` tag).

```
<input type="hidden" name="_scrnid" value="exp_${agent}_${data.stageCounter()}" >
```

If you have loops/repeated stages, you have to include a round variable in there as well. This will evaluate to the file name of your screenshot for this stage.

Then you have to add these lines to the robot inside the "`if (form) {...}`" condition of the robot.js file. And run the experiment with the robot activated.

```
var scrnid = form['_scrnid'];
if ( scrnid != null) {
    window.location = "scrn:" + scrnid.value + ".png";
}
```

Note that you can have labels added to the input fields with this approach. And you can produce screenshots with filled in forms.