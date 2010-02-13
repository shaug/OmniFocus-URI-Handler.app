[send to OF]: javascript:window.location='x-omnifocus://newtask?name='+encodeURIComponent(document.title)+'&note='+encodeURIComponent(window.location+'\n\n')+encodeURIComponent(getSelection())+'&quickentry=0';
[send to OFQE]: javascript:window.location='x-omnifocus://newtask?name='+encodeURIComponent(document.title)+'&note='+encodeURIComponent(window.location+'\n\n')+encodeURIComponent(getSelection())+'&quickentry=1';
[parse]: javascript:window.location='x-omnifocus://parsetasks?text='+encodeURIComponent(getSelection())+'&single=0';

# OMNIFOCUS URI HANDLER

This applet enables you to create new tasks using an "x-omnifocus" URL. This is particularly designed to make it easy to add tasks from a web browser via a bookmarklet, without having to code a separate script for each browser. This also works in browsers that don't support AppleScript. (I'm looking at you, Firefox!!!)

It also supports more advanced URLs containing context and project assignments that you're likely to create from web page bookmarklets. This functionality can be utilized to make it easier to add OmniFocus tasks from other applications, shell scripts, etc., without having to hook into complicated AppleScript.

## ATTRIBUTION

This applet was originally created by [Nik](http://nik.me/omnifocus-uri-handler), with improvements and fixes from [kaijin](http://forums.omnigroup.com/showpost.php?p=66060&postcount=34).

## HOW TO CREATE PROPER URLS

All URLs must use the "x-omnifocus:" URI. You can have "whack whacks" after the URI, or just a colon, your choice. You must then follow the URI with the following methods:

> *x-omnifocus:newtask*

This creates a new task. You can pass variables, following the example below. The only required element is "name".

> _x-omnifocus://newtask?name=**task name**&project=**project name**&context=**context name**&note=**task note text**&quickentry=**1/0**_

**Project Name** and **Context Name** will "fuzzy match" an existing project or context, so you don't need a full or exact name.

A **Quickentry** value of "1" will cause the task to go into the Quick Entry window, which will be activated, rather than straight into the inbox. 

> *x-omnifocus:parsetasks*

This parses tasks either as a single task or as multiple tasks, per the usual parsing syntax. You can pass two variables, the text to parse and whether to parse it as a single task, as below. The only required element is the text to parse.

> _x-omnifocus://parsetasks?text=**Text to Parse**&single=**1/0**_

A *single* value of "1" will make the tasks parse as single tasks. Otherwise, tasks will be parsed line-by-line, potentially as multiple tasks. 

All strings should be URL encoded to eliminate any ambiguity in URLs and whatnot.

## BOOKMARKLETS TO GET YOU STARTED ##

Here's some sample bookmarklets you can put into your browser's toolbar to make this all go:

[Send Page to OmniFocus][send to OF]
:  Add the current page as a task with the page's URL and any selected text as the note

[Send Page to OmniFocus QuickEntry][send to OFQE]
:  Same as above, but route to the Quick Entry window instead of directly into the inbox

[Parse Selection][parse]
:  Parse tasks in the selection

    

## NOTES

The HTML entity decoding routine falls down on certain characters, particularly Unicode characters.

If you use the quick entry window with the "newtask" method, the project and context values will be ignored, as these are not scriptable in the quick entry window.

## VERSION HISTORY

 * 1.0 - 06/20/2008: Initial release. Supports parsetasks, newtask
 * 1.x - 09/03/2009: Modified iNik's script to support new AppleScript terminology used after OF 1.7 update. "activate" changed to "open" for QuickEntry. This version corrects an issue with the QuickEntry window failing to open when the bookmarklet is used in Firefox 3.5.2. Refer to http://forums.omnigroup.com/showthread.php?t=8251 for details.  - kaijin

