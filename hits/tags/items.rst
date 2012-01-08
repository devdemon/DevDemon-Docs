############
Top Items Tag
############
::

  {exp:hits:items}
      <!-- Template Code -->
  {/exp:hits:items}

This template tag allows you to show a list of top items based on their hits

.. contents::
  :local:

***********************
Parameters
***********************

type=""
==============
REQUIRED: Hits can track different types of items.

=================== ====================================================================================
Type                Description
=================== ====================================================================================
**entry**           Channel Entries
**forum_thread**    Forum Threads
**category**        Channel Entries Categories
**channel_images**  Channel Images - The Images
**channel_files**   Channel Files - The Files
**channel_videos**  Channel Videos - The Videos
**br_product**      BrilliantRetail - The Products
=================== ====================================================================================

top=""
==============
REQUIRED: We need to specify what type top list we want

=================== ====================================================================================
Type                Description
=================== ====================================================================================
**today**           Today
**yesterday**       Yesterdays List
**week**            This Week
**month**           This Month
**year**            This Year
=================== ====================================================================================

channel=""
==============
Limit the results by channel. Additionally, you can use the pipe character to separate multiple channels.

channel_id=""
==============
Limit the results by channel_id. Additionally, you can use the pipe character to separate multiple channels.

static=""
==============
Setting this tag to "yes" will prevent the tag from looping. (See examples for usage)

limit=""
=========
This parameter limits the number of videos on any given page. The limit will default to 10 entries if a value is not specified. If you are using pagination then this will determine the number of entries shown per page.

**Default:** limit="10"

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
This parameter allows you to change the default variable prefix used. This is especially usefull when you are nesting tags to avoid variable collisions.

**Default:** prefix="hits"
For example the default variable for the file URL is: `{hits:count}` but if you use prefix="hi" the variable for the file URL will now be {hi:count}


**********************
Variables
**********************

{hits:item_id}
=================
The item ID (is always 0 for Channel Entries)

{hits:entry_id}
=================
The entry ID

{hits:hits}
===================
Total hits received

{hits:count}
=================
The "count" out of the current videos being displayed. If five videos are being displayed, then for the fourth video the {video:count} variable would have a value of "4".

{hits:total_items}
=================
The total number of items being displayed.

{hits:items}
=================
This variable will output a concatenated list of item_id's seperated by a pipe character
Only works in STATIC MODE.

{hits:entries}
=================
This variable will output a concatenated list of entry_id's seperated by a pipe character
Only works in STATIC MODE.


{hits:entries}
=================
The total number of videos being displayed.

****************************
Conditionals
****************************

{if hits:no_items}
=====================
This tag will conditionally display the code inside the tag if there are no items to display

**********************
Example
**********************

Normal Mode
==================================
::

	{exp:hits:items type="entry" top="week" limit="10"}
	    {exp:channel:entries entry_id="{hits:entry_id}" dynamic="off"}
	        <strong>{title}</strong>
	    {/exp:channel:entries}
	{/exp:hits:items}
	
Static Mode
==================================
::

	{exp:hits:items type="entries" top="week" limit="10" static="yes"}
	    {exp:channel:entries fixed_order="{hits:entries}" dynamic="off"}
	        <strong>{title}</strong>
	    {/exp:channel:entries}
	{/exp:hits:items} 