############################
RATING: Top Channel Entries
############################
::

  {exp:channel_ratings:top_entries}
      <!-- Template Code -->
  {/exp:channel_ratings:top_entries}

This tag allows you to display a list of top Channel Entries

.. contents::
  :local:

***********************
Parameters
***********************

channel=""
==============
Limit the list by a specific channel

channel_id=""
==============
Limit the list by a specific Channel ID (faster)

custom_fields=""
=================
Here you can specify which custom fields to grab from you channel entries. To specify multiple fields, separate fields with the pipe character.

status=""
===========
Limit entries by their status. To specify multiple status, separate status with the pipe character.

**Default:** status="open"

include_review=""
==================
Include comment reviews in stats

**Default:** include_review="no"

collection=""
==============
Limit by rating collection.

**Default:** collection="default"

precision=""
==============
This parameter allows you to specify the number of decimals to round fractions on numerical rating fields for averages.
For example, a value of 1 would give you a result like this for a rating value: 4.5

**Default:** precision="2"

thousands=""
==============
This parameter allows you to specify which character to use to separate groups of thousands in numeric rating fields. For example, a value of , would parse 10000 as 10,000. Default is , (comma).

**Default:** thousands=","

fractions=""
==============
This parameter allows you to specify which character to indicate fractions in numeric ratings. (Decimals)

**Default:** fractions="."

scale=""
==============
By default, Channel Ratings assumes your rating scale is 5. As in, your numerical ratings are out of 5 (ex: 1 out of 5 stars, 2 out of 5 stars, etc). You can however, change the scale to be out of "10" by specifying the scale parameter. When you specify this, the stars variable pairs will switch from the default of 5 graphic images to 10 when placed around your numerical rating value.

**Default:** scale="5"

theme=""
==============
Since you can have your own custom themes, this parameter allows you to specify which theme to use.

**Default:** theme="stars"

limit=""
========
This parameter limits the number of items on any given page. The limit will default to 30 entries if a value is not specified.

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

**Default:** prefix="rating"

For example the variable `{rating:count}`, if you use prefix="cr" the variable will now be {cr:count}

**********************
Variables
**********************

{rating:entry_id}
====================
The entry ID

{rating:entry_title}
====================
The entries title

{rating:entry_date}
====================
The entry date
For date variable info see: http://expressionengine.com/user_guide/templates/date_variable_formatting.html

{rating:CUSTOM_FIELD}
=============================
Replace CUSTOM_FIELD with the field you want. The ones you specified in the custom_fields="" parameter

{rating:channel_id}
====================
The channel ID of the entry

{rating:channel_name}
======================
The channel short name of the entry

{rating:channel_title}
=======================
The channel title (label) of the entry

{rating:channel_url}
=====================
The channel URL of the entry, as specified in the channel preferences

{rating:channel_search_result_url}
===================================
The channel search results URL of the entry, as specified in the channel preferences

{rating:channel_comment_url}
=============================
The channel comment URL of the entry, as specified in the channel preferences

{rating:overall:avg}
=====================
This variable outputs the overall average rating value for all fields.

{rating:overall:total}
=======================
This variable outputs the total amount of ratings submitted

{rating:overall:sum}
=====================
This variable outputs the total cumulative value/score of all ratings submitted

{rating:overall:latest_date}
=============================
The date/time of the latest rating submission
For date variable info see: http://expressionengine.com/user_guide/templates/date_variable_formatting.html

{rating:overall:stars}
=======================
This variable outputs "star" images to construct a graphical representation of the overall average rating value

{rating:count}
=========================
The "count" out of the current item being displayed. If five items are being displayed, then for the fourth item the count variable would have a value of "4".

{rating:total_entries}
=======================
The total number of entries being displayed.

****************************
Conditionals
****************************

{if rating:no_entries}
======================
This tag will conditionally display the code inside the tag if there are no items to display.

**********************
Example
**********************
::

{exp:channel_ratings:top_entries custom_fields="body|extended"}
	
		<h2>{rating:entry_title}</h2>
		
		<p>{rating:body}</p>
		<p>{rating:extended}</p>
		
		Rating: OVERALL: {rating:overall:stars} ({rating:overall:avg} of 5)
				
{/exp:channel_ratings:top_entries}