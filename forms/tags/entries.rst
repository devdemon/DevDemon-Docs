########################
Entries Tag
########################
::

  {exp:forms:entries}
      <!-- Template Code -->
  {/exp:forms:entries}

The Entries tag allows you to display Forms entries in your EE Templates.

.. contents::
  :local:

***********************
Parameters
***********************

entry_id=""
==============
Entry ID of an Channel Entry. Use this parameter to grab the form linked to a specific entry.

url_title=""
==============
Same as entry_id="" but now it with the entry's url_title.

form_name=""
==============
This parameter can be used to specify a specific form by using it's form name

member_id=""
==============
Limit to a specific member. Use CURRENT_USER to specify the current user.

prefix=""
=============
This parameter allows you to change the default variable prefix used. This is especially useful when you are nesting tags to avoid variable collisions.

**Default:** prefix="forms"

For example the variable `{forms:username}`, if you use prefix="fm" the variable will now be {fm:username}

**********************
Variables
**********************

{forms:member_id}
=================
The member id who submitted the entry

{forms:ip_address}
====================
The IP Address of the person

{forms:date}
====================
The date of the submission
For date variable info see: http://expressionengine.com/user_guide/templates/date_variable_formatting.html

{forms:country_cc}
====================
The country code if available

{forms:screen_name}
=====================
The screen name of the user

{forms:username}
====================
The username of the user

****************************
Variable Pairs
****************************

{forms:fields} {/forms:fields}
==================================
Lists all fields for this form

Here is a list of available variables WITHIN this variable pair

{forms:field}
--------------
Saved data for this field

{forms:field_type}
--------------------
The field type

{forms:field_label}
--------------------
The field label

{forms:field_name}
--------------------
The field short name


****************************
Conditionals
****************************

{if forms:no_form}
===================
This tag will conditionally display the code inside the tag if no form was found

{if forms:no_entries}
=======================
This tag will conditionally display the code inside the tag if there are no submissions for this form

**********************
Example
**********************

::

	{exp:forms:entries form_name="untitled"}

	Submitted on: {forms:date format=""}

	{if forms:no_form} NO FORM FOUND! {/if}

	{forms:fields}
		<strong>{forms:field_label} :</strong><br>
		<p>{forms:field}</p>
	{/forms:fields}

	{/exp:forms:entries}