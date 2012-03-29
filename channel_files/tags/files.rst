############
Files Tag
############
::

  {exp:channel_files:files}
      <!-- Template Code -->
  {/exp:channel_files:files}

This template tag allows you to show all files within a single entry.

.. contents::
  :local:

***********************
Parameters
***********************

entry_id=""
==============
Entry ID of an Channel Entry. Use this parameter to limit the files list to a specific entry.

url_title=""
==============
Same as entry_id="" but now it with the entry's url_title.

channel=""
==============
Limit the files list to a specific Channel.

channel_id=""
==============
Same as channel="" but uses channel_id's instead.

field=""
==============
Limit the files list to a specific Entry Field.

category=""
==============
Limit the files list to a specific category as chosen in the Fieldtype.

file_id=""
==========
File ID of an file. Use this parameter to limit the files list to a specific file.

primary_only=""
===============
Limit the results to only the primary files.

- **Options:** yes | no
- **Default:** no

skip_primary=""
===============
Skip primary files

- **Options:** yes | no
- **Default:** no

orderby=""
=============
The "order" parameter sets the display order of the files. Setting options for this parameter include:

-  orderby="title"
-  orderby="upload_date"
-  orderby="filename"
-  orderby="filesize"
-  orderby="file_id"
-  orderby="random" 

**Default:** orderby="file_order"

sort=""
=============
The sort order can be ascending or descending. Setting options for this parameter include:
- sort="asc"
- sort="desc"

**Default:** sort="asc'

limit=""
========
This parameter limits the number of files on any given page. The limit will default to 30 entries if a value is not specified. If you are using pagination then this will determine the number of entries shown per page.

**Default:** limit="30"

offset=""
=============
This parameter offsets the display by X number of entries. For example, if you want to show all entries except the three latest ones, you would do this: offset="3"

backspace=""
=============
Backspacing removes characters (including spaces and line breaks) from the last iteration of the loop. For example, if you put a <br /> tag after each entry you'll have this:

::

	Item 1<br />      Item 2<br />      Item 3<br />
	
You might, however, not want the <br /> tag after the final item. Simply count the number of characters (including spaces and line breaks) you want to remove and add the backspace parameter to the tag. The <br /> tag has 6 characters plus a new line character, so you would do this:

backspace="7"

Would produce this:

::

	Item 1<br />      Item 2<br />      Item 3

prefix=""
=============
This parameter allows you to change the default variable prefix used. This is especially useful when you are nesting tags to avoid variable collisions.

**Default:** prefix="file"

For example the default variable for the file URL is: `{file:url}` but if you use prefix="cf" the variable for the file URL will now be {cf:url}

**********************
Variables
**********************

{file\:id}
==========
The internal File ID

{file\:url}
===========
The full URL to the original file

{file\:secure_url}
==================
Same as `{file:url}` but a HTTPS version

{file\:locked_url}
==================
Obfuscated time limited url to the file

{file\:title}
=============
The file title as specified in the field row

{file\:description}
===================
The file description as specified in the field row

{file\:category}
================
File category (if used/specified)

{file\:date}
============
Shows the date/time of the upload
For date variable info see: http://expressionengine.com/user_guide/templates/date_variable_formatting.html

.. deprecated:: 5.0.1
   Use `{file:upload_date}` instead.   

{file\:upload_date}
====================
Shows the date/time of the upload
For date variable info see: http://expressionengine.com/user_guide/templates/date_variable_formatting.html

{file\:filename}
================
The filename of the file

{file\:extension}
=================
The file extension of the file

{file\:filesize}
================
The file size. Outputs for example: 2.3 MB

{file\:filesize_bytes}
=======================
The file size, but now in bytes

{file\:mimetype}
=================
The official mime-type of the file
Example: image/jpeg

{file\:switch="one|two|three"}
==============================
This variable permits you to rotate through any number of values as the entries are displayed. The first file will use "option_one", the second will use "option_two", the third "option_three", the fourth "option_one", and so on.

The most straightforward use for this would be to alternate colors. It could be used like so:

::

	{exp:channel_files:files entry_id="{entry_id}"}
		<div class="{file:switch='one|two'}">
		        <h2>{file:title}</h2>
		        <a href="{file:url}">{file:filename} ({file:filesize})</a>
		</div>
	{/exp:channel_files:files}
	
The files would then alternate between <div class="one"> and <div class="two">.

Multiple instances of the `{file:switch=}` tag may be used and the system will intelligently keep track of each one.
	

{file\:count}
=============
The "count" out of the current files being displayed. If five files are being displayed, then for the fourth file the `{file:count}` variable would have a value of "4".

{file\:total}
=============
The total number of files being displayed.

{file\:field:1}
===============
The contents of custom field 1

{file\:field:2}
===============
The contents of custom field 2

{file\:field:3}
===============
The contents of custom field 3

{file\:field:4}
===============
The contents of custom field 4

{file\:field:5}
===============
The contents of custom field 5

****************************
Conditionals
****************************

{if file\:no_files}
===================
This tag will conditionally display the code inside the tag if there are no files


**********************
Example
**********************
::

	{exp:channel:entries channel="about"}   
		<h1>{title</h1>
		
		<h2>All Files</h2>
		{exp:channel_files:files entry_id="{entry_id}"}
	    	<a href="{file:locked_url}" title="{file:title}">{file:title}</a>
		{/exp:channel_files:files}
	{/exp:channel:entries}	


***********************
Pagination
***********************
The pagination feature allows you to display a limited number of files and then automatically link to the next set. That way you can, for example, show files 1-10 on the first page and automatically link to pages that display 11-20, 21-30, etc

You have two choices as to the style of the navigation element. The first method would look something like this:

::

	Page 27 of 344 pages  << First  <  11 12 13 14 15 >  Last >>
	
The second method is a more traditional "next page" / "previous page" output:

::
	
	Previous Page | Next Page


Parameters
=====================

paginate=""
-----------

::

	paginate="top" paginate="bottom"  paginate="both"

This parameter is for use with files pagination and determines where the pagination code will appear for your files:

=================== ====================================================================================
Value               Description
=================== ====================================================================================
**top**             The navigation text and links will appear above your list of entries.
**bottom**          The navigation text and links will appear below your list of entries.
**both**            The navigation text and links will appear both above and below your list of entries.
=================== ====================================================================================

If no parameter is specified, the navigation block will default to the "bottom" behavior.

paginate_base=""
----------------
This tells ExpressionEngine to override the normal pagination link locations and point instead to the explicitly stated template group and template.
For example: paginate_base="files/list"


Variables
=====================
These individual variables are for use inside the `{file:paginate}` tag pair.

{file\:current_page}
--------------------
Outputs the current page number (In the `{file:paginate}` tag pair)

{file\:total_pages}
--------------------
The total number of pages of you have (In the `{file:paginate}` tag pair)

{file\:pagination_links}
-------------------------
These show the current page you are on as well as "surrounding" pages in addition to links for nex/previous pages and first/last pages. (In the `{file:paginate}` tag pair)


Conditional Variables
=====================
These individual conditional variables are for use inside the `{file:paginate}` tag pair.

{if file\:next_page}
---------------------
This tag will conditionally display the code inside the tag if there is a "next" page. If there is no next page then the content simply will not be displayed. (In the `{file:paginate}` tag pair)

{if file\:previous_page}
-------------------------
This tag will conditionally display the code inside the tag if there is a "previous" page. If there is no previous page then the content simply will not be displayed. (In the `{file:paginate}` tag pair)


Example
=====================

::

	{exp:channel_files:files entry_id="{entry_id}" paginate="bottom"}
		<a href="{file:locked_url}" title="{file:title}">{file:title}</a>
		{file:paginate}
			<p>Page {file:current_page} of {file:total_pages} pages {file:pagination_links}</p>
		{/file:paginate}
	{/exp:channel_files:files}