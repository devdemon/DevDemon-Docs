###############
Map Tag
###############
::

  {exp:entry_mapper:map}
      <!-- Template Code -->
  {/exp:entry_mapper:map}

This template tag allows you to show your map and a basic list of entries

.. contents::
  :local:

***********************
Parameters
***********************

map_name=""
==============
The map short name

map_id=""
==============
The map id

prefix=""
=============
This parameter allows you to change the default variable prefix used. This is especially useful when you are nesting tags to avoid variable collisions.

**Default:** prefix="mapper"

For example the variable `{mapper:count}`, if you use prefix="hi" the variable will now be {hi:count}

**********************
Variables
**********************

{mapper:id}
=================
The map ID

{mapper:label}
=================
Map Label

{mapper:name}
===================
Map short name

{mapper:image_url}
====================
URL to the image

{mapper:image_width}
=====================
Image Width (in px)

{mapper:image_height}
======================
Image Height (in px)

****************************
Variable Pairs
****************************

{mapper:entries} {/mapper:entries}
==================================
Lists all entries

Here is a list of available variables WITHIN this variable pair

{mapper:entry_id}
------------------
The entry_id

{mapper:channel_id}
------------------------
The channel_id this entry belongs to

{mapper:entry_title}
-----------------------
The entries title

{mapper:css_top}
-----------------------
Top position (in px)

{mapper:css_left}
-----------------------
Left position (in px)


**********************
Example
**********************

::

    {exp:entry_mapper:map map_name="world_map"}
    <div id="world_map" style="position:relative;width:{mapper:image_width};height:{mapper:image_height};">
        <img src="{mapper:image_url}" width="{mapper:image_width}" height="{mapper:image_height}">

        {mapper:entries}
        <span class="entry" style="position:absolute;top:{mapper:css_top};left:{mapper:css_left};">
            {mapper:entry_title}
        </span>
        {/mapper:entries}

    </div>
    {/exp:entry_mapper:map}

