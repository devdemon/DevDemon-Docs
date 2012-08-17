###########################
Common Errors
###########################

For Updater to work, at least two criteria must be satisfied:

(1) file ownership: all of your ExpressionEngine files must be owned by the user under which your web server executes. In other words, the owner of your ExpressionEngine files must match the user under which your web server executes. The web server user (named "apache", "web", "www", "nobody", or some such) is not necessarily the owner of your ExpressionEngine files. Typically, ExpressionEngine files are owned by the ftp user which uploaded the original files. If there is no match between the owner of your ExpressionEngine files and the user under which your web server executes, you will receive an error message and the update process will stop and you will find that no matter what you do, you won't be able to update automatically.

(2) file permissions: all of your ExpressionEngine files must be either owner writable by, or group writable by, the user under which your Apache server executes.

On shared hosts, ExpressionEngine files should specifically NOT be owned by the web server. If more then one user owns different files in the install (because of edits made by deleting and re-uploading of files via different accounts, for example), the file permissions need to be group writable (for example, 775 and 664 rather then the default 755 and 644). File permissions (in general) should be adjusted as appropriate for the server environment (the shared host RackSpace CloudSites for example recommends 700 and 600 for a single ftp user, or 770 and 660 for multiple ftp users). 


Here is a list of common errors

DB Backup fails with error: You have exceeded the allowed page load frequency.
================================================================================
You have Throttling enabled, disable it. This will prevent execution of our AJAX calls.