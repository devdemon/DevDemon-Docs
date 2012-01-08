#######################
Entries Tag
#######################
::

  {exp:tagger:entries}
      <!-- Template Code -->
  {/exp:tagger:entries}

This tag shows a list of items that have been tagged with the specified tags.

.. contents::
  :local:

***********************
Parameters
***********************

tag=""
==============
This parameter allows you to specify a tag in which to pull entries that match. To specify multiple tags, separate tags with the pipe character.

unitag=""
==============
Same as tag="" but now with the unitag version of the tag

custom_fields=""
=================
Here you can specify which custom fields to grab from you channel entries. To specify multiple fields, separate fields with the pipe character.

status=""
===========
Limit entries by their status. To specify multiple status, separate status with the pipe character.

**Default:** status="open"

channel=""
===========
Limit the entries by channel. Multiple channels can be specified by using the pipe character

show_future_entries=""
========================
Do you want to display entries with a future date?

**Default:** show_future_entries="no"

limit=""
==========
This parameter limits the number of entries on any given page. The limit will default to 30 entries if a value is not specified.

**Default:** limit="30"

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

**Default:** prefix="tagger"

For example the variable `{tagger:count}`, if you use prefix="tg" the variable will now be {tg:count}

**********************
Variables
**********************

{tagger:entry_id}
====================
The entry ID

{tagger:entry_title}
====================
The entries title

{tagger:entry_date}
====================
The entry date
For date variable info see: http://expressionengine.com/user_guide/templates/date_variable_formatting.html

{tagger:channel_id}
====================
The channel ID of the entry

{tagger:channel_name}
======================
The channel short name of the entry

{tagger:channel_title}
=======================
The channel title (label) of the entry

{tagger:channel_url}
=====================
The channel URL of the entry, as specified in the channel preferences

{tagger:channel_search_result_url}
===================================
The channel search results URL of the entry, as specified in the channel preferences

{tagger:channel_comment_url}
=============================
The channel comment URL of the entry, as specified in the channel preferences

{tagger:CUSTOM_FIELD}
=============================
Replace CUSTOM_FIELD with the field you want. The ones you specified in the custom_fields="" parameter

{tagger:count}
=========================
The "count" out of the current entry being displayed. If five items are being displayed, then for the fourth item the count variable would have a value of "4".

{tagger:total_entries}
=======================
The total number of entries being displayed.

****************************
Conditionals
****************************

{if tagger:no_entries}
=======================
This tag will conditionally display the code inside the tag if there are no entries to display

**********************
Example
**********************
::

	{exp:tagger:entries tag="{segment_2}" custom_fields="body|extended"}
	
		{if tagger:no_entries}<p>No entries where found</p>{/if}
		
		<h2>{tagger:entry_title}</h2>
		
		<p>{tagger:body}</p>
		<p>{tagger:extended}</p>
		
		<p><a href="/entry/{tagger:entry_url_title}">Read More</a></p>
		
	{/exp:tagger:entries}