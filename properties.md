# Currently implemented properties #

(incomplete)

The following is a list of properties which can be separated out in properties for the server (coral.head), properties for the experiment (coral.exp) and properties for the client (coral.polyp). Properties that do not follow the proper naming convention might be updated in the future.

## General and coral.head ##

| coral.debug | **true**/false | set the program into debug mode on startup |
|:------------|:---------------|:-------------------------------------------|


## Experiment ##

| exp.basepath| "."/path | set the directory where the files for the experiment can be found. |
|:------------|:---------|:-------------------------------------------------------------------|
| exp.stagesfile | stages.csv | the name of the stages file to be used |
| [coral.exp.variant](CoralExpVarianProperty.md) | **empty**/char | Allows small variations within the same stages file by specifying alternative file endings [details](details.md). |

## coral.polyp ##

| coral.polyp.ontop | **true**/false | force the polyp window to always be in front |
|:------------------|:---------------|:---------------------------------------------|
| coral.polyp.fullscreen | **true**/false | force the client window to be full screen |
| coral.polyp.number | **1**/integer | number of simultaneous polyps running in the same window, most useful for testing |
| [coral.polyp.robot](robot.md)  | **empty**/filename | Specifies a JavaScript file that is run after the page is fully loaded on the client, needs to be reachable for the client, most useful for testing. |

## coral.db ##

| coral.db.mode | **file**/mem | determine whether the database is writen to a file oder just kept in memory |
|:--------------|:-------------|:----------------------------------------------------------------------------|

## coral.web ##

| coral.web.server | **false**/true | state whether to start the web server |
|:-----------------|:---------------|:--------------------------------------|
| coral.web.hostname | **localhost**/string | public host name |
| coral.web.port | **8080**/int | web port number |