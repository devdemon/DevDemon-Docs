#######################
RATING: Rating Status
#######################
::

  {exp:channel_ratings:rating_status}
      <!-- Template Code -->
  {/exp:channel_ratings:rating_status}

This tag allows you to know if the user has already rated this item.

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
For Channel Comemnts

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
The rating collection

**Default:** collection="default"

prefix=""
=============
This parameter allows you to change the default variable prefix used. This is especially useful when you are nesting tags to avoid variable collisions.

**Default:** prefix="rating"

For example the variable `{rating:count}`, if you use prefix="cr" the variable will now be {cr:count}

****************************
Conditionals
****************************

{if rating:not_rated}
======================
This tag will conditionally display the code inside the tag if the user has not rated this item.

{if rating:already_rated}
===========================
This tag will conditionally display the code inside the tag if the user has already rated this item.

**********************
Example
**********************
::

	{exp:channel_ratings:rating_status entry_id="{entry_id}" }
	
		{if rating:already_rated} You have already rated this entry {/if}
		
		{if rating:not_rated} Please scroll down to submit your rating!	{/if}
	
	{/exp:channel_ratings:rating_status} 