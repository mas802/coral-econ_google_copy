# Introduction #

To simplify experiment implementation in the lab, packaging your CORAL experiment as an App will speed the experiment launching process.  The below instructions apply to Mac OSX.  Note that in this set-up write permission to the /Applications folder is required on both client and server machines.
# Details #

## SERVER ##
An AppleScript can launch the CORAL server. The following code launches the server and requests a choice of .properties files.  This is useful if multiple experiments are being run in same lab, or if you wish to keep a series of experiments packaged in a single application.

Using the AppleScript Editor add the following code.

```
display dialog "Please enter the name of the game you wish to serve" default answer ""

# This line defines the variable game_variable as whatever the user entered in the dialog box

set game_variable to (text returned of result)

set project_location to quoted form of POSIX path of "/Applications/CORALServer.app/Contents/Resources"

do shell script "cd " & project_location & "; java -Dlog4j.debug=true -Xmx512m -Xms128m -XstartOnFirstThread -cp lib/any.jar:lib/coral.jar:lib/hsqldb.jar:lib/velocity-1.6.2-dep.jar:lib/commons-logging.jar:lib/log4j-1.2.15.jar:lib/swt.jar coral.CoralHead " & game_variable & ".properties"
```

Save the script as an App (File-> Save As -> File Format -> Application).  Then select Bundle Contents and add all the files used in your experiment(s), making sure to include the lib, res and db folders.

Then save the App as CORALServer in the /Applications/ folder.

## CLIENT ##
As before, use the AppleScript Editor and paste the following code.  This script launches the client and request the IP address of the server on start-up.

```
display dialog "Enter IP address of server" default answer "192.168."

set ip_variable to (text returned of result)

display dialog ip_variable

set default_folder_Location to (path to documents folder)

set project_location to quoted form of POSIX path of "/Applications/CORALClient.app/Contents/Resources/"

# (choose folder with prompt "Folder :" default location default_folder_Location)

do shell script "cd " & project_location & " ; java -Dlog4j.debug=true -Xmx512m -Xms128m -XstartOnFirstThread -cp lib/any.jar:lib/coral.jar:lib/hsqldb.jar:lib/velocity-1.6.2-dep.jar:lib/commons-logging.jar:lib/log4j-1.2.15.jar:lib/swt.jar coral.CoralPolyp coral.host=" & ip_variable
```


Save the script as an App (File-> Save As -> File Format -> Application).  Then select Bundle Contents and add the /lib and /res folders used in your experiment(s).

Then save the App as CORALClient in the /Applications/ folder.

## Example ##
A series of multi-player experiments was packaged in this way by Cameron Murray.
The packaged CORAL experiment applications are available here
http://buddyexperiment.blogspot.com.au/p/data-repository.html