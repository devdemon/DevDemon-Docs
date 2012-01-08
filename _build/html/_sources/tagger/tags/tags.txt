#######################
View Tags
#######################
::

  {exp:tagger:tags}
      <!-- Template Code -->
  {/exp:tagger:tags}

This tag generates a list of tags that are associated with this entry.

.. contents::
  :local:

***********************
Parameters
***********************

entry_id=""
==============
REQUIRED: The entry ID of the entry

url_title=""
==============
Same as entry_id but now the url_title of the entry

orderby=""
==============
The "order" parameter sets the display order of the tags. Setting options for this parameter include:

-  orderby="order"
-  orderby="tag_name"
-  orderby="entry_date"
-  orderby="hits"
-  orderby="total_entries"

**Default:** orderby="order"

limit=""
==========
This parameter limits the number of tags displayed. The limit will default to 30 entries if a value is not specified.

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

For example the variable `{tagger:group_title}`, if you use prefix="tg" the variable will now be {tg:group_title}

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

{tagger:total_items}
=========================
Total entries linked to this tag

{tagger:total_hits}
=========================
Total hits that this tag has received

{tagger:count}
=========================
The "count" out of the current tag being displayed. If five items are being displayed, then for the fourth item the count variable would have a value of "4".

{tagger:total_tags}
=========================
The total number of tags being displayed

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

	{exp:tagger:tags entry_id="{entry_id}"}
		{if tagger:no_tags}<p>No tags where found.</p>{/if} 
		<a href="/tag/{tagger:urlsafe_tagname}">{tagger:tag_name}</a>
	{/exp:tagger:tags} 

