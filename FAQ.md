# FAQ #

**What is the res folder, and what should I do with it?**

The res folder(s) is where the client(s) keeps a copy of the files it displays, the most important is called `_exp.html` which contains the html code of the current page. This folder also would contain any image or other media files that are displayed to the participants. They can either be copied directly to all clients prior to the experiment, or uploaded by specifying a special condition "`*`" in the stages file.

If serveral clients are running simultaneous for testing each will get a seperate res folder with an identifying number. If multiple clients are started independently from the same location, make sure the coral.polyp.res property is set for a different folder for each of them.