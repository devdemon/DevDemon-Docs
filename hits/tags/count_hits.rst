###############
Count Hits Tag
###############
::

  {exp:hits:count_hits}
      <!-- Template Code -->
  {/exp:hits:count_hits}

This tag counts the hits received. It will do it's best to ignore the most popular search engines.
You will place this tag only on Single Entry Pages, sicne you only want to count the hits for a single entry at a time right?

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

.. important:: You MUST use one of the above parameters.
	
**********************
Example
**********************

::

	{exp:channel:entries channel="blog"}
	
		{exp:hits:count_hits entry_id="{entry_id}"}
		
		<h2>{title}</h2>
		{body}
	{/exp:channel:entries}