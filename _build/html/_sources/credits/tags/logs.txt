############
Credits Log
############
::

  {exp:credits:log}
      <!-- Template Code -->
  {/exp:credits:log}

This template tag allows you to show display a log of all credits activity

.. contents::
  :local:

***********************
Parameters
***********************

receiver_id=""
==============
Limit the list to a specific Member ID of the one receiving points

.. note:: The SYSTEM is always 0

sender_id=""
==============
Limit the list to a specific Member ID of the one sending the points

.. note:: The SYSTEM is always 0

member_id=""
=================
The same as receiver_id=""

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

{credits:receiver}
====================
The Screen Name of the receiver

.. note:: The SYSTEM is always displayed as "SYSTEM"

{credits:receiver_id}
=====================
The Member ID of the receiver

.. note:: The SYSTEM is always 0

{credits:receiver_group_id}
============================
The Group ID of the receiver

.. note:: The SYSTEM is always 0

{credits:sender}
=====================
The Screen Name of the sender

.. note:: The SYSTEM is always displayed as "SYSTEM"

{credits:sender_id}
====================
The Member ID of the sender

.. note:: The SYSTEM is always 0

{credits:sender_group_id}
==========================
The Group ID of the sender

.. note:: The SYSTEM is always 0

{credits:date}
===============
The date of the transaction
For date variable info see: http://expressionengine.com/user_guide/templates/date_variable_formatting.html

{credits:action_name}
=======================
The action name (short name)

{credits:action_label}
========================
The action label (title)

{credits:credits}
========================
The amount of credits being exchanged/awarded/transfered

{credits:count}
=========================
The "count" out of the current item being displayed. If five items are being displayed, then for the fourth item the count variable would have a value of "4".

****************************
Conditionals
****************************

{if credits:no_logs}
=======================
This tag will conditionally display the code inside the tag if there are no logs to display.

**********************
Example
**********************
::

	<h4>Your Credits Activity (latest 25)</h4>
	<ul>
	    {exp:credits:logs received_id="CURRENT_USER" limit="25"}
	        {if credits:no_logs}<li>No activity recorded</li>{/if}
	        <li>{credits:credits} Credits - {credits:action_label} - {credits:date format=""}</li>
	    {/exp:credits:logs}
	</ul>