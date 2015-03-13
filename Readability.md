While maintaining proper readability is mainly the responsibility of the programmer, there are a number of ways a framework can support proper behaviour.

CORAL allows for the flexibile naming of variables, files and functions. It allows for simplification of the scope of the experiment. This is demonstrated (below) by the use of 'contribution.vm' instead of 'input.vm'. Which helps simplfy the validation process.

|template|validation|wait|
|:-------|:---------|:---|
|init.js|  |  |
|instructions.vm|  |  |
|wait.vm|  | all|
|contribution.vm|contribution |  |

The use of a variable is global, meaning that as the programmer you have tight control over the life cycle of that variable. The variable keeps it values set within a script until otherwise reset.
_i.e._ constraints which are set in _init.js_ are kept for the whole game.