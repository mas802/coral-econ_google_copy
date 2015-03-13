# Selecting one round for payoff #

If your experiment involves a number of rounds and you only want
to pay one of them you have to come up with a procedure to select this round.

The most straight forward way of doing this is to set the
payoff round at the start of the experiment and then use an
if statment later on to set a variable that contains the final
payoff.

So in a file like init.js that is run at the begin of the experiment
set:

```

// initialise the finalpayoff variable to -99 so it is obviouse
// when it was not set
var finalpayoff = -99;

// set the payoff round (this could be done throwing a dice)
var payoffround = 5;

```

Later at the end of the round when you have calculated the round's payoff (roundpayoff) you can set:

```

if ( round == payoffround ) {
    finalpayoff = roundpayoff;
}

```

# Selecting a RANDOM round for payoff #

If you want the program to select a random round for payoff, e.g. when the payoff round should be different for all subjects even in one session you can set the payoffround with the follwong code.

```
payoffround = Math.round( Math.random()*MAX_ROUNDS )
```