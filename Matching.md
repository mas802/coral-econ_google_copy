# How to match agents in the game. #

Different experimental protocol asked for interactions between participants. How to match participants is often a vital part of the experiment. CORAL is agnostic to those protocols, offering a simple list based access to access data across participants.

It is recommended to use list based matchings for most cases.

```
matchings[4] = [ [2,3,0,1], // 1st round
                 [3,2,1,0] // 2nd round
               ];
```

If you want to vary the matching each round , you have to include the sequence in a file that gets open every time in the loop.