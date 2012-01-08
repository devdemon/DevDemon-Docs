################
Credits Earned
################
::

  {exp:credits:earned}
      <!-- Template Code -->
  {/exp:credits:earned}

This template tag allows you to show display how many credits a user/group has earned.

.. contents::
  :local:

***********************
Parameters
***********************

member_id=""
==============
Member ID

.. note:: The use CURRENT_USER to indicate the current logged in user

username=""
==============
The Username

group_id=""
=============
The group ID. Use this parameter if you want to get the total earned for the entire group

action=""
===========
Limit to a specific action. To specify multiple items, separate each item with a pipe character.

**********************
Example
**********************
::

	<p>Total Credits Earned: {exp:credits:earned member_id="CURRENT_USER"}</p>