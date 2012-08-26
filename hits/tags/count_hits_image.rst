########################
Count Hits (Image) Tag
########################
::

  {exp:hits:count_hits_image}

Allows you to track hits on cached templates. This tag outputs and img tag which points to a special URL on your site to track hits.
It will do it's best to ignore the most popular search engines. You will place this tag only on Single Entry Pages, sicne you only want to count the hits for a single entry at a time right?

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

		<h2>{title}</h2>
		{body}

		{exp:hits:count_hits_image entry_id="{entry_id}"}
		{!-- EXAMPLE OUTPUT: <img src="http://www.mysite.com/?ACT=123?t=2&i=66" alt="" /> --}
	{/exp:channel:entries}
