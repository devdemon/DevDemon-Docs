#######################
Ungrouped Tags
#######################
::

  {exp:tagger:ungrouped_tags}
      <!-- Template Code -->
  {/exp:tagger:ungrouped_tags}

This tag generates a list of tags that are not grouped

.. contents::
  :local:

***********************
Parameters
***********************

orderby=""
==============
The "order" parameter sets the display order of the tags. Setting options for this parameter include:

-  orderby="tag_name"
-  orderby="entry_date"
-  orderby="hits"
-  orderby="total_entries"
-  orderby="random"

**Default:** orderby="total_entries"

sort=""
==============
The sort order can be ascending or descending. Setting options for this parameter include:
- sort="asc"
- sort="desc"

**Default:** sort="asc'

limit=""
==========
This parameter limits the number of tags on any given page. The limit will default to 30 entries if a value is not specified.

**Default:** limit="30"

backspace=""
=============
Backspacing removes characters (including spaces and line breaks) from the last iteration of the loop. For example, if you put a <br /> tag after each entry you'll have this:

::

	Tag 1<br />      Tag 2<br />      Tag 3<br />
	
You might, however, not want the <br /> tag after the final item. Simply count the number of characters (including spaces and line breaks) you want to remove and add the backspace parameter to the tag. The <br /> tag has 6 characters plus a new line character, so you would do this:

backspace="7"

Would produce this:

::

	Tag 1<br />      Tag 2<br />      Tag 3
	
prefix=""
=============
This parameter allows you to change the default variable prefix used. This is especially useful when you are nesting tags to avoid variable collisions.

**Default:** prefix="tagger"

For example the variable `{tagger:tag_name}`, if you use prefix="tg" the variable will now be {tg:tag_name}

**********************
Variables
**********************

{tagger:tag_name}
===================
The pretty tag name

{tagger:urlsafe_tagname} 
=========================
An URL Safe tag name, good for use in <a href=""> tags

{tagger:total_hits}
=========================
Total hits this tag has received

{tagger:total_items}
=========================
Total entries linked to this tag

{tagger:count}
=========================
The "count" out of the current tag being displayed. If five files are being displayed, then for the fourth file the {tagger:count} variable would have a value of "4".

{tagger:total_tags}
=========================
The total number of tags being displayed.

****************************
Conditionals
****************************

{if tagger:no_tags}
=======================
This tag will conditionally display the code inside the tag if there are no tags to display

**********************
Example
**********************
::

	{exp:tagger:ungrouped_tags}
	
    	{if tagger:tags}<p>No tags where found.</p>{/if}
    	
    	<p><a href="/tag/{tagger:urlsafe_tagname}">{tagger:tag_name}</a></p>
    	
	{/exp:tagger:ungrouped_tags}