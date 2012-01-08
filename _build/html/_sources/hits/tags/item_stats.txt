###############
Item Stats Tag
###############
::

  {exp:hits:item_stats}
      <!-- Template Code -->
  {/exp:hits:item_stats}

This template tag allows you to display hits stats for an item

.. contents::
  :local:

***********************
Parameters
***********************
You need to specify one of the following item id's

entry_id=""
==============
For Channel Entries

url_title=""
==============
For Channel Entries

category=""
==============
For Channel Categories (the url_title)

category_id=""
==============
For Channel Categories

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
For BrilliantRetail
	
prefix=""
=============
This parameter allows you to change the default variable prefix used. This is especially usefull when you are nesting tags to avoid variable collisions.

**Default:** prefix="hits"
For example the default variable for the file URL is: `{hits:count}` but if you use prefix="hi" the variable for the file URL will now be {hi:count}


**********************
Variables
**********************

{hits:today}
=================
Hits for Today

{hits:yesterday}
=================
Hits for Yesterday

{hits:week}
===================
Total hits this week

{hits:month}
=================
Total hits this month

{hits:year}
===================
Total hits this year

{hits:linechart:days}
======================
A Google Chart displaying hits per day

{hits:linechart:weeks}
=======================
A Google Chart displaying hits per week

{hits:linechart:months}
========================
A Google Chart displaying hits per month

****************************
Variable Pairs
****************************

{hits:days} {/hits:days}
==================================
Lists all days a hit has been recorded
Here is a list of available variables WITHIN this variable pair

{hits:hits}
-----------------
Total Hits Recorded

{hits:day_number}
--------------------
Current day number (0 to 365)

{hits:date}
-------------
The current day
For date variable info see: http://expressionengine.com/user_guide/templates/date_variable_formatting.html

{hits:weeks} {/hits:weeks}
==================================
Lists all weeks a hit has been recorded
Here is a list of available variables WITHIN this variable pair

{hits:hits}
-----------------
Total Hits Recorded

{hits:week_number}
--------------------
Current week number (0 to 53)

{hits:months} {/hits:months}
==================================
Lists all weeks a hit has been recorded
Here is a list of available variables WITHIN this variable pair

{hits:hits}
-----------------
Total Hits Recorded

{hits:month_number}
--------------------
Current month number (1 to 12)

{hits:date}
-------------
Starting day of the month
For date variable info see: http://expressionengine.com/user_guide/templates/date_variable_formatting.html

{hits:days} {/hits:days}
==================================
List all days
Here is a list of available variables WITHIN this variable pair

****************************
Conditionals
****************************

{if hits:no_stats}
=====================
This tag will conditionally display the code inside the tag if there are no stats to display

**********************
Example
**********************

::

	{exp:channel:entries entry_id="1"}
		<h4>{title}</h4>
		
		{exp:hits:item_stats entry_id="{entry_id}"}
		
			Today: {hits:today}
			Yesterday: {hits:yesterday}
			Week: {hits:week}
			Month: {hits:month}
			Year: {hits:year}
			
			{hits:linechart:days}<br />
			{hits:linechart:weeks} <br />
			{hits:linechart:months} <br />
			
			<h3>Days</h3>
			{hits:days}
				{hits:date format="%d-%m-%Y"} - {hits:hits} Hits <br />
			{/hits:days}
			
			<h3>Weeks</h3>
			{hits:weeks}
				Week {hits:week_number} - {hits:hits} Hits <br />
			{/hits:weeks}
			
			<h3>Months</h3>
			{hits:months}
				{hits:month_number} - {hits:date format="%F"} - {hits:hits} Hits <br />
			{/hits:months}
		
		{/exp:hits:item_stats}
	{/exp:channel:entries}