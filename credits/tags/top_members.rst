############
Top Members
############
::

  {exp:credits:top_members}
      <!-- Template Code -->
  {/exp:credits:top_members}

This template tag allows you to show display a list of the top members

.. contents::
  :local:

***********************
Parameters
***********************

action=""
===========
Limit the list to a specific action. To specify multiple items, separate each item with a pipe character.

limit=""
=========
This parameter limits the number of videos on any given page. The limit will default to 10 entries if a value is not specified. If you are using pagination then this will determine the number of entries shown per page.

**Default:** limit="15"

prefix=""
=============
This parameter allows you to change the default variable prefix used. This is especially useful when you are nesting tags to avoid variable collisions.

**Default:** prefix="credits"

For example the variable `{credits:count}`, if you use prefix="cr" the variable will now be {cr:count}

**********************
Variables
**********************

{credits:screen_name}
=======================
The Screen Name of the user

{credits:username}
=====================
The Username of the user

{credits:member_id}
=====================
The Member ID of the user

{credits:group_id}
=====================
The Group ID of the user

{credits:credits}
====================
Total amount of credits for this user

{credits:count}
=========================
The "count" out of the current item being displayed. If five items are being displayed, then for the fourth item the count variable would have a value of "4".

{credits:total_members}
=========================
The total amount of members currently being displayed

****************************
Conditionals
****************************

{if credits:no_credits}
=======================
This tag will conditionally display the code inside the tag if there are no stats to display

**********************
Example
**********************
::

	<h4>Top 10 Members</h4>
	
	{exp:credits:top_members}
		<a href="/members/{credits:member_id}/">{credits:screen_name}</a> ({credits:credits} total credits)<br /> 
	{/exp:credits:top_members}