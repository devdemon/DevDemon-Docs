#######################
Grouped Tags
#######################
::

  {exp:tagger:groups}
      <!-- Template Code -->
  {/exp:tagger:groups}

This tag generates a list of tags by categorized by group

.. contents::
  :local:

***********************
Parameters
***********************

groups=""
==============
If you want to limit the list of group you can specify them here and separate them by a pipe character

**Default:** all groups

prefix=""
=============
This parameter allows you to change the default variable prefix used. This is especially useful when you are nesting tags to avoid variable collisions.

**Default:** prefix="tagger"

For example the variable `{tagger:group_title}`, if you use prefix="tg" the variable will now be {tg:group_title}

**********************
Variables
**********************

{tagger:group_title}
=====================
The group title

{tagger:group_name} 
=========================
The group short name (url_title)

{tagger:group_desc}
=========================
The group description

****************************
Conditionals
****************************

{if tagger:no_groups}
=======================
This tag will conditionally display the code inside the tag if there are no tag groups to display

****************************
Variable Pairs
****************************

{tagger:tags} {/tagger:tags}
==================================
Lists all tags within the groups
Here is a list of available variables WITHIN this variable pair

{tagger:tag_name}
-----------------
The Tag name

{tagger:tag_name}
-----------------
An URL Safe tag name, good for use in <a href=""> tags

{if tagger:no_tags}
--------------------
This tag will conditionally display the code inside the tag if there are no tags in this groups to display

**********************
Example
**********************
::

	{exp:tagger:groups}
		{if tagger:no_groups}<p>No groups where found.</p>{/if}
		<h2>{tagger:group_title}</h2>
		{tagger:tags}
			{if tagger:no_tags}<p>No Tags where found</p>{/if}
			<p><a href="/tag/{tagger:urlsafe_tagname}">{tagger:tag_name}</a></p>
		{/tagger:tags}
	{/exp:tagger:groups}