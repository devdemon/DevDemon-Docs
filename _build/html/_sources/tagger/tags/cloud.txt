#######################
Tag Cloud
#######################
::

  {exp:tagger:cloud}
      <!-- Template Code -->
  {/exp:tagger:cloud}

This tag generates a tag cloud

.. contents::
  :local:

***********************
Parameters
***********************

rankby=""
==========
This parameter allows you to weigh your tags by **hits** or **entries**.

**Default:** rankby="entries"

min_size=""
=============
This parameter controls to min size of the `{tagger:size}` variable.

max_size=""
============
This parameter controls to max size of the `{tagger:size}` variable.

channel=""
=============
Limit the tags by channel. Multiple channels can be specified by using the pipe character

groups=""
=============
Limit the tags by groups. Multiple groups can be specified by using the pipe character

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

	Item 1<br />      Item 2<br />      Item 3<br />
	
You might, however, not want the <br /> tag after the final item. Simply count the number of characters (including spaces and line breaks) you want to remove and add the backspace parameter to the tag. The <br /> tag has 6 characters plus a new line character, so you would do this:

backspace="7"

Would produce this:

::

	Item 1<br />      Item 2<br />      Item 3
	
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

{tagger:unitag}
===================
An 100% Guaranteed URL Safe tag name, good for use in <a href=""> tags

{tagger:size}
=========================
This variable will return a numeric value of the relative rank of the tag within the sequence of tags in the list.

{tagger:total_items}
=========================
Total entries linked to this tag

{tagger:count}
=========================
The "count" out of the current tag being displayed. If five items are being displayed, then for the fourth item the count variable would have a value of "4".

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

	{exp:tagger:cloud limit="100" backspace="1" min_size="13" max_size="26"} 
		<a href="/tag/{tagger:urlsafe_tagname}/" title="{tagger:tag_name}" style="font-size:{tagger:size}px">{tagger:tag_name}</a>,
	{/exp:tagger:cloud}