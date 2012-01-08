#######################
Quick Entries List Tag
#######################
::

  {exp:tagger:tagname}
      <!-- Template Code -->
  {/exp:tagger:tagname}

This tag generates a list of entry_id's (seperated by a pipe character), associated with the specified tag.

.. contents::
  :local:

***********************
Parameters
***********************

tag=""
==============
The tag you would want to decode

unitag=""
==============
If it's a unitag, use this parameter.

prefix=""
=============
This parameter allows you to change the default variable prefix used. This is especially useful when you are nesting tags to avoid variable collisions.

**Default:** prefix="tagger"

For example the variable `{tagger:entry_ids}`, if you use prefix="tg" the variable will now be {tg:entry_ids}

**********************
Variables
**********************

{tagger:entry_ids}
===================
A list of entry_id's associated with this tag

{tagger:tag_name}
=================
The tag name

****************************
Conditionals
****************************

{if tagger:no_entries}
=======================
This tag will conditionally display the code inside the tag if there are no entries

**********************
Example
**********************
::

	{exp:tagger:entries_quick tag="{segment_3}"}
	
		{exp:channel:entries entry_id="{tagger:entry_ids}"}
			<h4>{title}</h4>
		{/exp:channel:entries}
		
	{/exp:tagger:entries_quick} 

