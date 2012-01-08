#######################
Related Entries
#######################
::

  {exp:tagger:related}
      <!-- Template Code -->
  {/exp:tagger:related}

This tag works the same as :doc:`./entries` tag but only shows entries related (By Tags) to the main specified entry.

.. contents::
  :local:

***********************
Parameters
***********************
All parameters of :doc:`./entries` can be used here. And there are some specific parameters for this tag too.

entry_id=""
==============
The 'main' entry_id. All entries shown will be related in some way to this entry.

url_title=""
==============
Same as entry_id="" but now with an url_title.

**********************
Variables
**********************

All parameters of :doc:`./entries` can be used here

****************************
Conditionals
****************************

{if tagger:no_entries}
=======================
This tag will conditionally display the code inside the tag if there are no entries to display

**********************
Example
**********************
::

	<h2>Related Entries</h2>
	{exp:channel:entries channel="blog" url_title="{segment_3}"}
		
		<h1>{title}</h1>
		
		{body}
		
		<h3>Related Entries</h3>
		{exp:tagger:related entry_id="{entry_id}"}			
			<a href="/entry/{tagger:entry_url_title}">{tagger:entry_title}</a></p>
		{/exp:tagger:related}
		
	{/exp:channel:entries}