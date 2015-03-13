# Eclipse #
Eclipse is an Integrated Development Environment (IDE) suited to developing economic experiments with CORAL. It is compatible with Windows, Mac OSX and Linux.


## 1. Download and install Eclipse ##

Download eclipse from [eclipse.org](http://www.eclipse.org/downloads/) (Standard Edition is fine).

## 2. Download and install plugins (dropins) ##

To facilitate using CORAL with Eclipse there a few plugins that are useful:

#### AnyView (CORAL) ####

First [Any View](https://dl.dropboxusercontent.com/u/3997716/AnyClipse_0.9.0.jar) can be added into the
dropin folder of Eclipse - you can find this folder where you installed Eclipse (remember to restart).

#### Velocity Plugin ####

Another useful plugin is to enable syntax highlighting for velocity, there are a number of plugins out there, e.g. [Velocity-Edit](http://code.google.com/p/velocity-edit/). Some people prefer just to work with HTML syntax highlighting instead.

#### Javascript code highlighting ####

Eclipse is able to highlight Javascript code when appropriate software is installed. To improve your experience writing Javascript in Eclipse add the appropriate Web Developer and Javascript Developer tools as follows.

Help-> Install New Software-> Work with: Choose --All Available Sites-- -> Select from the populated list of options -Web, XML, Java EE, and OSGi Enterprise Development -> Click Next/Finish.

Restart Eclipse

## 3. Create or import a project ##

Either import an existing project (recommended) or create a new one.

#### Import existing project ####

File -> Import -> General -> Existing Projects into Workspace -> Next -> Browse (select folder) -> Finish

## 4. Using the Any View tool ##
This dropins comes with one View so far, in Eclipse choose Window-> Show View -> Other then selecting Any View from the AnyClipse option.
The tool allows for fast navigation to templates (or stages) in the experiment, between experiments (by adding multiple .properties files to the selector menu), and allows for fast launching and testing of any experiment based on a choice of .properties file.

![https://dl.dropboxusercontent.com/u/3997716/AnyClipse.png](https://dl.dropboxusercontent.com/u/3997716/AnyClipse.png)

For fast launching and testing by using the Any Views tool the set command line options (the small windows to the left of the yellow arrow) have to be adjusted depending on the operating system that is used. Just copy and paste the command for the respective operating system into it.

#### WINDOWS: ####
-Dlog4j.debug=true -Xmx512m -Xms128m -cp lib/any.jar;lib/coral.jar;lib/hsqldb.jar;lib/velocity-1.6.2-dep.jar;lib/commons-logging.jar;lib/log4j-1.2.15.jar;lib/swt-win32.jar coral.CoralHead
#### MAC: (default) ####
-XstartOnFirstThread -Dlog4j.debug=true -Xmx512m -Xms128m -cp lib/any.jar:lib/coral.jar:lib/hsqldb.jar:lib/velocity-1.6.2-dep.jar:lib/commons-logging.jar:lib/log4j-1.2.15.jar:lib/swt.jar coral.CoralHead



## 5. Starting an experiment project ##
An experiment in CORAL needs certain files and folders to run.  These are

**Folders**
/lib,
/db,
/res,

**Files**
YourExperimentName.properties,
YourExperimentName.csv,
coral.log

A new Eclipse project is created by selecting File-> New-> Project.  In the first New Project Wizard window select General-> Project.  In the next window you can name your project anything you choose.  However, if you wish for the project to automatically find the required CORAL folders you downloaded, first create a directory at the location of your new project with the same name as you intend to name the project and add the CORAL files into that directory.  Then when you create a new project in Eclipse, simply name the project with the same name as the folder you created containing all the CORAL files.

For example, I will create the following folder in my file system `/Users/Me/Documents/Eclipse/ExperimentName/` and within that folder will reside the /lib, /res, /db folders and the coral.log file.

I then choose the location for my project as `/Users/Me/Documents/Eclipse` and I name it `ExperimentName` and Eclipse will populate my project with these necessary files automatically.

The first order of business is to then write a `.properties` files and a csv file that will create the core structure of your experiment.

## What goes where ##

The /res folder is the repository for any image files that are presented in the experiment screens.

Other folders can be created within the project to manage your template screen files (.vm) and javascript files (.js), and the relative reference to this folder will be required in the .csv file that controls the experiment structure.

### More coming soon ###