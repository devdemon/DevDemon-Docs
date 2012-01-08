###################
RATING: Top Items
###################
::

  {exp:channel_ratings:top_items}
      <!-- Template Code -->
  {/exp:channel_ratings:top_items}

This tag allows you to display a list of top items

.. contents::
  :local:

***********************
Parameters
***********************

type=""
==============
REQUIRED: Channel Ratings can rate types of items.

=================== ====================================================================================
Type                Description
=================== ====================================================================================
**entry**           Channel Entries
**comment_review**  Comment Reviews (ratings attached to an comment)
**comment_entry**   Channel Comments (ratings on individual comments)
**member**          Site Members
**channel_images**  Channel Images (ratings on the individual images)
**channel_files**   Channel Files (ratings on the individual files)
**channel_videos**  Channel Videos (ratings on the individual videos)
**br_product**      BrilliantRetail (ratings on the individual products)
=================== ====================================================================================

channel=""
==============
Limit by channel (if applicable)

channel_id=""
==============
Limit by Channel ID (if applicable)

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

{rating:item_id}
====================
The Item ID

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

{rating:total_items}
=====================
The total amount of items being displayed.

****************************
Conditionals
****************************

{if rating:no_items}
======================
This tag will conditionally display the code inside the tag if there are no items to display.

**********************
Example
**********************
::

<h3>Top Channel Images</h3>
{exp:channel_ratings:top_items type="channel_images"}

	{exp:channel_images:images image_id="{rating:item_id}"}
		<img src="{image:url:small}">  {rating:overall:stars} <br /> 
	{/exp:channel_images:images}
	
{/exp:channel_ratings:top_items}