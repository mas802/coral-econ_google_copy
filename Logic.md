## defaults to javascript ##
The logic of the experiment concerns all calculations from participant input to the transfer of information between participants. Default implementation uses JavaScript files for this purpose. _Note: do not confuse this with the option to use JavaScript in the html files._
In JavaScript variables can be accessed with their names (therefore, no preceding dollar sign) and new variables can be created.

#### Calculations ####
_Example_

wait.vm  ?

#### TRANSFER INFORMATION BETWEEN PARTICIPANTS ####
To transfer information between participants, the relevant 'others' have to be identified for each participant. A key instrument can be a matching table, but other methods (true random allocation) can also be used. The **agents** and **agent** assist with this task. The array **agents** allows for access to the data of the other participants (numbered from 0 to N-1), while the **agent** variable simply indicates the participants one position within the **agents** array.

_Example_