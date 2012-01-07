#################
Display Poll Tag
#################
::

  {exp:channel_polls:poll}
      <!-- Template Code -->
  {/exp:channel_polls:poll}

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

prefix=""
=============
This parameter allows you to change the default variable prefix used. This is especially usefull when you are nesting tags to avoid variable collisions.

**Default:** prefix="poll"
For example the default variable for the file URL is: `{poll:total_votes}` but if you use prefix="cp" the variable for the file URL will now be {cp:total_votes}

**********************
Variables
**********************

{poll:total_votes}
====================
Total votes casts already

{poll:last_vote_date}
======================
Shows the date/time of the last vote cast in this poll
For date variable info see: http://expressionengine.com/user_guide/templates/date_variable_formatting.html

{poll:end_date}
====================
The end dat of this poll.
For date variable info see: http://expressionengine.com/user_guide/templates/date_variable_formatting.html

{poll:chart}
==============
Displays a Google Chart of the poll results.


****************************
Variable Pairs
****************************

{poll:answers} {/poll:answers}
==================================
Lists all answers for this poll

Here is a list of available variables WITHIN this variable pair

{poll:answer}
--------------
The answer

{poll:votes}
-------------
Total votes this answer already has

{poll:percent}
---------------
Percentage of the total votes

{poll:my_choice}
-----------------
This variable can be used to show the end user his own choice when he voted.
This variable will output 'yes' if the current answer is the one the user choose.

::

	{if poll:my_choice == 'yes'}
	YOUR ANSWER!
	{/if}
	
{poll:votes_log} {/poll:votes_log}
==================================
This variable pair will output a log of all votes cast in this poll.

Here is a list of available variables WITHIN this variable pair

{poll:log:answer_id}
---------------------
The answer id of the chose answer

{poll:log:answer}
------------------
The answer itself (text)

{poll:log:ip_address}
----------------------
The IP Address of the user

{poll:log:vote_date}
---------------------
The vote date
For date variable info see: http://expressionengine.com/user_guide/templates/date_variable_formatting.html

{poll:log:member_id}
---------------------
The member ID of the user
For guests, the member id is 0

{poll:log:screen_name}
-----------------------
The screen name of the user

{poll:log:username}
-------------------
And finally, the username of the user

{poll:countries} {/poll:countries}
==================================
This variable pair will output country stats based on the votes cast

Here is a list of available variables WITHIN this variable pair

{poll:country}
---------------
The country code

{poll:country_long}
--------------------
The country name

{poll:country_total}
---------------------
Total amount of votes from this country

{poll:country_percent}
-----------------------
Percentage of total votes from this country


****************************
Conditionals
****************************

{if poll:already_voted}
=========================
This tag will conditionally display the code inside the tag if the user has already voted in this poll.

{if poll:not_voted}
=========================
This tag will conditionally display the code inside the tag if the user has not yet voted in this poll.

{if poll:show_results}
=========================
This tag will conditionally display the code inside the tag if the user is allowed to view the votes.
Use this conditional to wrap your votes results around so you can decide when to show them.

{if poll:no_poll}
=========================
This tag will conditionally display the code inside the tag if no poll has been found

**********************
Example
**********************
::

	{exp:channel:entries channel="default"}
		{exp:channel_polls:poll entry_id="{entry_id}"}
			<h2>Poll Results</h2>
			
			{if poll:show_results}
				<ul>
				{poll:answers}
				    <li>{poll:answer} {poll:percent} {poll:votes} of {poll:total_votes} - {if poll:my_choice}<strong>MY CHOICE</strong>{/if}</li>
				{/poll:answers}
				</ul>
				
				{poll:chart}
				
				<h4>Votes Log</h4>
				<ul>
				{poll:votes_log}
				    <li>{poll:log:screen_name} - {poll:log:vote_date format="%F %d, %Y - %g:%i"} - {poll:log:answer}</li>
				{/poll:votes_log}
				</ul>
			
			
			{if:else}
				POLL RESULTS BLOCKED    
			{/if}
			
			{if poll:no_poll}<h4>NO POLL</h4>{/if}
			
		{/exp:channel_polls:poll}
	{/exp:channel:entries}  


Here is an example with IP2NATION enabled using the `{poll:countries}` `{/poll:countries}` variable pair

::

	{exp:channel_polls:poll entry_id="{entry_id}"}
	
		<h1>Countries that voted in poll</h1>
		{poll:countries}
		    <li><img src="/DevDemon2/images/world_flags/flag_{poll:country}.gif"/> ({poll:country_long}) {poll:country_total} Total ({poll:country_percent}%)</li>
		{/poll:countries}
		
		
		<hr>
		
		<h1>Countries Per Answer</h1>
		{poll:answers}
		<h4>{poll:answer}</h4>
		
		<ul>
		{poll:answers:countries}
		    <li><img src="/DevDemon2/images/world_flags/flag_{poll:country}.gif"/> ({poll:country_long}) {poll:country_total} Total ({poll:country_percent}%)</li>
		{/poll:answers:countries}
		</ul>
		
		{/poll:answers}
	
	{/exp:channel_polls:poll}  
