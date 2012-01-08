############
Images Tag
############
::

  {exp:channel_images:images}
      <!-- Template Code -->
  {/exp:channel_images:images}

This template tag allows you to show all images within a single entry.

.. contents::
  :local:

***********************
Parameters
***********************

entry_id=""
==============
Entry ID of an Channel Entry. Use this parameter to limit the images list to a specific entry.

url_title=""
==============
Same as entry_id="" but now it with the entry's url_title.

channel=""
==============
Limit the images list to a specific Channel.

channel_id=""
==============
Same as channel="" but uses channel_id's instead.

field=""
==============
Limit the images list to a specific Entry Field.

category=""
==============
Limit the images list to a specific category as chosen in the Fieldtype.

image_id=""
============
Image ID of an image. Use this parameter to limit the images list to a specific image.

image_url_title=""
===================
Image URL Title of an image. Use this parameter to limit the images list to a specific image.

cover_only=""
===============
Limit the results to only the cover images.

- **Options:** yes | no
- **Default:** no

skip_cover=""
===============
Skip cover images

- **Options:** yes | no
- **Default:** no

orderby=""
=============
The "order" parameter sets the display order of the images. Setting options for this parameter include:

-  orderby="title"
-  orderby="random" 

**Default:** orderby="image_order"

sort=""
========
The sort order can be ascending or descending. Setting options for this parameter include:
- sort="asc"

**Default:** sort="asc'

limit=""
========
This parameter limits the number of images on any given page. The limit will default to 30 entries if a value is not specified. If you are using pagination then this will determine the number of entries shown per page.

**Default:** limit="30"

offset=""
==========
This parameter offsets the display by X number of entries. For example, if you want to show all entries except the three latest ones, you would do this: offset="3"

backspace=""
=============
Backspacing removes characters (including spaces and line breaks) from the last iteration of the loop. For example, if you put a <br /> tag after each entry you'll have this:

::

	Image 1<br />      Image 2<br />      Image 3<br />
	
You might, however, not want the <br /> tag after the final item. Simply count the number of characters (including spaces and line breaks) you want to remove and add the backspace parameter to the tag. The <br /> tag has 6 characters plus a new line character, so you would do this:

backspace="7"

Would produce this:

::

	Image 1<br />      Image 2<br />      Image 3

prefix=""
==========
This parameter allows you to change the default variable prefix used. This is especially useful when you are nesting tags to avoid variable collisions.

**Default:** prefix="image"

For example the default variable for the image URL is: `{image:url}` but if you use prefix="ci" the variable for the image URL will now be {cf:url}

**********************
Variables
**********************

{image:id}
==========
The internal Image ID

{image:url}
============
The full URL to the original image

{image:secure_url}
==================
Same as `{image:url}` but a HTTPS version

{image:locked_url}
==================
Obfuscated time limited url to the image

{image:title}
==============
The image title as specified in the field row

{image:url_title}
==================
The image title as specified in the field row OR is automatically generated if not specified

{image:description}
===================
The image description as specified in the field row

{image:category}
================
Image category (if used/specified)

{image:entry_id}
================
The entry_id this image belongs too. Handy for when you are listing images from different entries

{image:channel_id}
==================
The channel_id this image belongs too. Handy for when you are listing images from different entries

{image:width}
===============
The image width of the ORIGINAL image

{image:height}
===============
The image height of the ORIGINAL image

{image:filename}
=================
The filename of the image

{image:filesize}
=================
The file size. Outputs for example: 2.3 MB

{image:filesize_bytes}
=======================
The file size, but now in bytes

{image:mimetype}
=================
The official mime-type of the file
Example: image/jpeg

{image:switch="one|two|three"}
===============================
This variable permits you to rotate through any number of values as the entries are displayed. The first image will use "option_one", the second will use "option_two", the third "option_three", the fourth "option_one", and so on.

The most straightforward use for this would be to alternate colors. It could be used like so:

::

	{exp:channel_images:images entry_id="{entry_id}"}
		<div class="{switch='one|two'}">
		        <h2>{image:title}</h2>
		        <a href="{image:url}"><img src="{image:url:medium}" /></a>
		</div>
	{/exp:channel_images:images}
	
The images would then alternate between <div class="one"> and <div class="two">.

Multiple instances of the `{image:switch=}` tag may be used and the system will intelligently keep track of each one.
	

{image:count}
==============
The "count" out of the current images being displayed. If five images are being displayed, then for the fourth images the {image:count} variable would have a value of "4".

{image:total}
==============
The total number of images being displayed.

{image:field:1}
===============
The contents of custom field 1

{image:field:2}
===============
The contents of custom field 2

{image:field:3}
===============
The contents of custom field 3

{image:field:4}
===============
The contents of custom field 4

{image:field:5}
===============
The contents of custom field 5

**********************
Size Variables
**********************
These variables can be used for each Size you have created of an image

{image:url:SIZENAME}
=====================
The full URL to the sized image

{image:secure_url:SIZENAME}
============================
The same as `{image:secure_url:SIZENAME}` but now with HTTPS

{image:filename:SIZENAME}
============================
The filename of the sized image

{image:filesize:SIZENAME}
==========================
The file size of the sized image. Outputs for example: 2.3 MB

{image:filesize_bytes:SIZENAME}
================================
The file size of the sized image, but now in bytes.

{image:width:SIZENAME}
=======================
The image width of the SIZED image

{image:height:SIZENAME}
========================
The image height of the SIZED image


****************************
Conditionals
****************************

{if image:no_images}
=====================
This tag will conditionally display the code inside the tag if there are no images


**********************
Example
**********************
::

	{exp:channel:entries channel="about"}   
		<h1>{title</h1>
		
		<h2>All Images</h2>
		{exp:channel_images:images entry_id="{entry_id}"}
	    	<a href="{image:url}"><img src="{image:url:medium}" /></a>
		{/exp:channel_images:images}
	{/exp:channel:entries}	


***********************
Pagination
***********************
The pagination feature allows you to display a limited number of images and then automatically link to the next set. That way you can, for example, show images 1-10 on the first page and automatically link to pages that display 11-20, 21-30, etc

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

This parameter is for use with images pagination and determines where the pagination code will appear for your images:

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
For example: paginate_base="images/list"


Variables
=====================
These individual variables are for use inside the {image:paginate} tag pair.

{image:current_page}
---------------------
Outputs the current page number (In the {image:paginate} tag pair)

{image:total_pages}
-------------------
The total number of pages of you have (In the {image:paginate} tag pair)

{image:pagination_links}
-------------------------
These show the current page you are on as well as "surrounding" pages in addition to links for nex/previous pages and first/last pages. (In the {image:paginate} tag pair)


Conditional Variables
=====================
These individual conditional variables are for use inside the {image:paginate} tag pair.

{if image:next_page}
---------------------
This tag will conditionally display the code inside the tag if there is a "next" page. If there is no next page then the content simply will not be displayed. (In the {image:paginate} tag pair)

{if image:previous_page}
-------------------------
This tag will conditionally display the code inside the tag if there is a "previous" page. If there is no previous page then the content simply will not be displayed. (In the {image:paginate} tag pair)


{image:pagination_links}
-------------------------
These show the current page you are on as well as "surrounding" pages in addition to links for nex/previous pages and first/last pages.


Example
========

::

	{exp:channel_images:images entry_id="{entry_id}" paginate="bottom"}
		<img src="{image:locked_url}">
		{image:paginate}
			<p>Page {image:current_page} of {image:total_pages} pages {image:pagination_links}</p>
		{/image:paginate}
	{/exp:channel_images:images}