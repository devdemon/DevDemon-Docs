############
New Vote Tag
############
::

  {exp:channel_polls:new_vote}
      <!-- Template Code -->
  {/exp:channel_polls:new_vote}

This template tag renders the form to submit a new vote

.. contents::
  :local:

***********************
Parameters
***********************

entry_id=""
==============
Entry ID of an Channel Entry. Use this parameter to specify from which entry you want to pull the poll from

url_title=""
==============
Same as entry_id="" but now it with the entry's url_title.

return=""
=============
This parameter allows you to define where the user will be returned after submitting a vote. The parameter can be defined in two ways:

- Use the standard Template_Group/Template syntax to specify where to return the user. For instance, if you want the user to be returned to the "local" Template in the "news" Template Group, you would use: return="news/local"
- Use a full URL. For example: return="http://example.com/return.html"

If this parameter is not defined, they will be returned to the form page.

prefix=""
=============
This parameter allows you to change the default variable prefix used. This is especially useful when you are nesting tags to avoid variable collisions.

**Default:** prefix="poll"

For example the variable `{poll:end_date}`, if you use prefix="cp" the variable will now be {cp:end_date}

**********************
Variables
**********************

{poll:total_votes}
====================
Total votes casts already

{poll:end_date}
====================
The end dat of this poll.
For date variable info see: http://expressionengine.com/user_guide/templates/date_variable_formatting.html

****************************
Variable Pairs
****************************

{poll:answers} {/poll:answers}
==================================
Lists all answers for this poll

Here is a list of available variables WITHIN this variable pair

{poll:form_name}
-----------------
The form input name

{poll:form_value}
------------------
The form input value

{poll:answer}
--------------
The answer

{poll:votes}
-------------
Total votes this answer already has

****************************
Conditionals
****************************

{if poll:already_voted}
=========================
This tag will conditionally display the code inside the tag if the user has already voted in this poll.

{if poll:not_voted}
=========================
This tag will conditionally display the code inside the tag if the user has not yet voted in this poll.

{if poll:closed}
=========================
This tag will conditionally display the code inside the tag if the poll has closed.
The poll can be closed by reaching it's specified end date or by closing it manually in the poll options.

{if poll:no_access}
=========================
This tag will conditionally display the code inside the tag if the user has no access to view the poll.
This can happen if the user is part of a member group that cannot vote.

{if poll:no_poll}
=========================
This tag will conditionally display the code inside the tag if no poll has been found

**********************
Example
**********************
::

	{exp:channel:entries channel="default"}
		{exp:channel_polls:new_vote entry_id="{entry_id}"}
		
		<ul>
		{poll:answers}
		    <li><input type="radio" name="{poll:form_name}" value="{poll:form_value}"> &nbsp; {poll:answer}</li>
		{/poll:answers}
		</ul>
		
		{if poll:closed}<h4>POLL CLOSED</h4>{/if}
		{if poll:no_access}<h4>YOU HAVE NO ACCESS</h4>{/if}
		{if poll:already_voted}<h4>ALREADY VOTED</h4>{/if}
		{if poll:not_voted}<h4>NOT VOTED YET</h4>{/if}
		
		<input name="submit" value="VOTE" type="submit">
		
		{/exp:channel_polls:new_vote}
	{/exp:channel:entries} 

