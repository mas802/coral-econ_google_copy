Pre-defines the look of the tables, paragraphs, font size, colour, titles, sub-titles and the whole look of the page.

It uses a CSS style infomration which provides a way a common style is used throughout the experiment, giving a simplistic way of updating the experiment without touching the stages seperately.

_Example_ {specifies the body}
```
<!DOCTYPE html>
<html>
 <head> 
        <STYLE type="text/css">
         body { 
                font-family: Helvetica;
                font-size: 12 pt;
                text-align: center;
                        margin: auto;
               }
</STYLE>
</head>
<body>

<div> 

<form action="exp://host/">
```

The header and the footer are supposed to go into every .vm file, at the beginning and the end, respectively. Example of calling in the header, {before the footer}: #parsel("cred/footer.vm")