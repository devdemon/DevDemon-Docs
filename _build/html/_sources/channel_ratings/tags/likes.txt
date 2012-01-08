########################
LIKE: Like Stats
########################
::

  {exp:channel_ratings:likes}
      <!-- Template Code -->
  {/exp:channel_ratings:likes}

This tag allows you to display the amount of likes for an item

.. contents::
  :local:

***********************
Parameters
***********************

entry_id=""
==============
For Channel Entries

url_title=""
==============
For Channel Entries

comment_id=""
==============
For Individual Comments

member_id=""
==============
For Site Members

ci_id=""
==============
For Channel Images

cf_id=""
==============
For Channel Files

cv_id=""
==============
For Channel Videos

br_id=""
==============
For BrilliantRetail Products

.. important:: You MUST use one of the above parameters.

collection=""
==============
A specific ratign collection

**Default:** collection="default"

prefix=""
=============
This parameter allows you to change the default variable prefix used. This is especially useful when you are nesting tags to avoid variable collisions.

**Default:** prefix="rating"

For example the variable `{rating:count}`, if you use prefix="cr" the variable will now be {cr:count}

**********************
Variables
**********************

{rating:liked}
=======================
Total number of likes

{rating:liked_p}
=========================
Total like percentage

{rating:disliked}
=========================
Total number of dislikes

{rating:disliked_p}
=========================
Total dislike percentage

{rating:total}
=========================
Total number of submissions

{rating:latest_vote} 
=========================
The date/time of the latest like/dislike submission for this item
For date variable info see: http://expressionengine.com/user_guide/templates/date_variable_formatting.html

****************************
Conditionals
****************************

{if rating:no_votes}
======================
This tag will conditionally display the code inside the tag if there where no likes/dislikes recorded yet.

{if rating:voted}
======================
This tag will conditionally display the code inside the tag if the current user already has voted

{if rating:not_voted}
======================
This tag will conditionally display the code inside the tag if the current user didn't cast a vote yet

**********************
Example
**********************
::

	{exp:channel_ratings:likes entry_id="{entry_id}"}
	
		{rating:liked} people found this review useful
		
	{/exp:channel_ratings:likes}