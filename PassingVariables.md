# Introduction #

In CORAL agents play the game sequence (as defined in the `.csv` file) individually.  For experiments where choices of one agent affect the variables of another agent, these choices must be passed between agents.

# Details #

Variable values for each agent are stored in a matrix-like representation.  The matrix is called `agents` with positions {0,1,2...N-1} .

However, one must specify the number format of the variable when accessing another agents variable values.  `agents[3].variable` will not produce a number format.

Thus if we want another agent to get the value of the variable called `variablename` from the first agent, that variable can be seen by other agents as

```
agents[0].getDouble("variablename")
```

Alternatively, if you require an integer value of the variable, you can use

```
agents[0].getLong("variablename")
```