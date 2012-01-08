######################
Template
######################

Mega Upload is a fieldtype and doesn't require any special tag.

To insert Mega Upload within your template you just use the channel field directly.
The actual field will provide you the actual URL of the file just like ExpressionEngine's own file fieldtype.

****************************
Variable Pair Mode
****************************
If the fieldtype is used in pair mode, you can use these variables within

{filename}
==================================
The filename

{extension}
==================================
The file extension

{path}
==================================
The path to the file


**********************
Example
**********************

Normal Mode
==================================
::

	{exp:channel:entries channel="about"}
	    <h2>{title}</h2>
	    <p><a href="{mega_upload_field}">Download File</a></p>
	{/exp:channel:entries} 
	
Variable Pair Mode
==================================
::

	{exp:channel:entries channel="about"}
	    <h2>{title}</h2>
	    <p>Filename: {mega_upload_field} {filename}.{extension} {/mega_upload_field}</p>
	{/exp:channel:entries}  