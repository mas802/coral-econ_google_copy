# Getting started with CORAL #

Please see http://ideas.repec.org/p/qut/qubewp/wp016.html for more background on this project.

## A useful guide for new users of CORAL ##

The following step-by-step example will be based around a simple public good game experiment. You can use this as a starting point for your own experiment as it easier to expand than to start from scratch (see Schaffner, 2013).


---


### STEP 1: Make sure you have Java installed ###

You need a working version of [Java](http://www.java.com) on your computer.
To test this on Windows start the command line tool (Start->cmd) and type "java -version". On OSX and Linux you can just type this into a Terminal.

```
C:\>java.exe -version
java version "1.7.0_45"
Java(TM) SE Runtime Environment (build 1.7.0_45-b18)
Java HotSpot(TM) Client VM (build 24.45-b08, mixed mode, sharing)

C:\>
```

Please follow the instruction for your operating system on the Java page to install if needed. Sometimes you will need to add the full path to the java.exe. binary (e.g. "C:\Program Files (x86)\Java\jre6\bin\java.exe").


---


### STEP 2: Download the example project and extract ###

Download the example project ([examplePG.zip](https://dl.dropboxusercontent.com/u/12198759/examplePG.zip)) and extract it into a folder of your choice.


---


### STEP 3: Run the example ###

To get a feeling for how the program operates, start the example project. Depending on your operating system you will have to either doubleclick coral-dep.jat (Windows, Linux), or startPG.command (OSX, note that you might need to change the permission first).

If you get an error "'java.exe' is not recognized as an internal or external command" you might need to check you java installation.

The example will open with a server screen and a testing client screen separated into 4 equal areas, each representing a different participant screen.

|<img src='https://dl.dropboxusercontent.com/u/12198759/coral_doc/screen_clients.png' width='400px' />|<img src='https://dl.dropboxusercontent.com/u/12198759/coral_doc/screen_server.png' width='400px' />|
|:----------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------|

To get the program running just click BEGIN on each of the 4 clients. Then the instruction screen will show up for each of them.
You can now progress through the experiment to get an understanding what it looks like.

![https://dl.dropboxusercontent.com/u/12198759/coral_doc/screen_clients2.png](https://dl.dropboxusercontent.com/u/12198759/coral_doc/screen_clients2.png)


---


### STEP 4: Explore the .properties file ###

The properties (settings) of a single experiment are listed in the so called .properties file.
The format of the file is a simple text file (open it with your favourite text editor) which is quite common in the Java environment and follows a very straight forward syntax.

```
# lines beginning with a hash sign (#) are comments
# and will be ignored by the program.

# values can be assigned to identifiers with an equal 
# sign where the value is any text between the equal 
# sign and the end of the line.
identifier = value

# usually identifiers use a dot notation to clarify 
# what part of the application they target. 
coral.head.ip = 192.168.1.1
coral.polyp.fullscreen = true
```

All properties are set to default values if not set. The coral.properties file of the example project contains extended comments for the important ones.
A full list of settings can be found in the [properties](properties.md) list on this wiki.


---


### STEP 5: Explore the stages.csv file ###

One of the most important properties for the server (coral.CoralHead)
is the stages file, which instructs the server on how to progress through the experiment.

```
exp.stagesfile = PGstages.csv
```

The file is kept in a comma separate values format (CSV) and can be edited with commercial table editors such as Excel but also with a
text editor.
The name of the file can be chosen to suit the experiment and treatment.

The first column of the stages file makes reference to two different kind of files, scripts and templates.
Usually the first are intended to deal with the experimental logic, while the second presents information to the participant and elicit responses.


#### Script files ####

In the default configuration the language for scripts is [JavaScript](https://en.wikipedia.org/wiki/JavaScript), mainly because it is almost ubiquitously used on the Internet these days and so huge support for it is available.
Its basic syntax is very close to the C-family of programming
languages.


#### Template files ####

The default templating language is velocity which is an intentionally restricted language that offers all elements to construct appealing user interfaces in [HTML](https://en.wikipedia.org/wiki/HTML) and with [CSS](https://en.wikipedia.org/wiki/CSS).
Have a look at the examples provided and for further reference consult the [user guide of velocity](http://velocity.apache.org/).


#### The public good example ####

The example provided is a very simple set up for a public good game with four players and a total of 10 rounds. The stages file outlines the following stages which are followed sequentially:

|stages/init.js|sets up the parameters for the experiment|
|:-------------|:----------------------------------------|
|stages/info.vm| displays an introduction to the experiment and elicits the participation number|
|stages/wait.vm| displays a wait screen and pauses until all participants have caught up|
|stages/beforeEachRound.js| script to run at the start of each round of the experiment. Resets variables and takes care of matching. This is the start of the main loop of the experiment.|
|stages/contribution.vm| elicits the contribution from the participant|
|stages/wait.vm| reuse of the wait screen to wait for everybody to catch up|
|stages/redistribution| where the payoffs are calculated before the program loops back to the next round. The experiment will loop back to the start of the loop until the repeat counter is 0 (so the value of 9 in the repeat column will result in a total of 10 rounds). |
|stages/showPayoff.vm| display the final payoff and end of the experiment|


---


### STEP 6: Start to customize the experiment ###

You now know all the basics to start customising the experiment to your needs.

<a href='Hidden comment: 
The final central part of the framework is the server and data storage.
The server is implemented in Java 6, allowing it to run on a large number of
platforms and the same code has been tested to run on Windows, Mac OSX, Linux
and even iOS.
The functionality is provided by a number of java .jar files.
These are standard library files that provide common functionality in an easy
to access and update format.
Database access for instance is provided by a standard Java Database Connectivity
([http://www.oracle.com/technetwork/java/javase/jdbc/index.html JDBC])
interface.
Hence any number of JDBC implementations can be used to provide the data storage
capabilities.
As a default CORAL uses a small custom transport library called any.
As server display component using velocity to display content in a SWT container
is also provided to monitor progress of the experiment.
It is recommended to keep the most up to date jar files in a lib folder. Then the <lib> part of the above command would need to be updated as follows (up to date at time of writing).

```
lib/coral.jar;lib/any.jar;lib/commons-logging.jar;lib/hsqldb.jar;swt.jar;velocity-1.6.2-dep.jar
```
'></a>