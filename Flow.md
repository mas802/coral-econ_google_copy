# stages file, defaults to stages.csv #

The flow of the experiment is defined in the stages.csv file (see under Framework files how this name can be altered). This file outlines the order in which different screens will appear, when experimental logic files are called, which parts of the experiment are repeated and how often. It also defines what conditions have to be met for a certain stage to be displayed and what input elements must fulfil such that the particpant can move on to the next stage.


### General Process ###

  1. Create a .csv file that has the following columns

|template|loopstage|looprepeat|condition|validate|wait|
|:-------|:--------|:---------|:--------|:-------|:---|

  * Template: list the process that you want the program to take _i.e._ Introduction, input = 'game' etc.
  * Loopstage: put in a number at the end stage (located in the template column) of your loop. The number represents how many cels back that you want to start the loop at. _i.e._ The Loopstage tells it to loop from the introduction again.
| template| loopstage |
|:--------|:----------|
| Init.js |  |
| Intro.vm|  |
| Instructions.vm|  |
| Input.js| 2 |


_Init.js: defines the variables used, i.e. SHOWUPFEE = 1.6;. Therefore it is only ever called once._


  * Looprepeat: sepcifies how many times the loop should be repeated before it moves on to the next stage. _i.e._
|template| loopstage|looprepeat|
|:-------|:---------|:---------|
|Input.js| 2| 1|


  * Condition: defines which player type makes the decisions during that stage. _i.e._ Specify between payer and payee.
|template| loopstage|looprepeat|condition|
|:-------|:---------|:---------|:--------|
|Input.js| 2| 1|  |
|Contribution.vm|  |  | payer|

  * Validate: specifies that the stage has been fulfilled. If it has not been fulfilled it will go back to the screen until it is fulfilled.  In this column, it will also have to specify for example the range, _i.e._ price, price range {1:a}, **and/or** certain restrictions, _i.e._ Price A cannot be larger than price B. **and/or** if using a questionnaire, whether you want the participants to answer these questions (Do this in the stages file).

  * Wait: specifies if the players have to wait for another player to finish certain steps before moving on. Put _all_ if you want none of the players to get ahead of the others.


**_Note the names of files used under the template are examples, not the necessary file names._**