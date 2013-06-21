###############
Entries Tag
###############
::

  {exp:entry_mapper:entries}
      <!-- Template Code -->
  {/exp:entry_mapper:entries}

This template tag allows you to list all entries just like {exp:channel:entries}

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

**********************
Variables
**********************

{mapper:css_top}
=======================
Top position (in px)

{mapper:css_left}
=======================
Left position (in px)


**********************
Example
**********************

::


    <div id="world_map" style="position:relative;">
        {exp:entry_mapper:map map_name="world_map"}
        <img src="{mapper:image_url}" width="{mapper:image_width}" height="{mapper:image_height}">
        {/exp:entry_mapper:map}

        {/exp:entry_mapper:entries map_name="world_map"}
        <span class="entry" style="position:absolute;top:{mapper:css_top};left:{mapper:css_left};">
            {title}
            <!-- You can use all {exp:channel:entries} variables -->
        </span>
        {/exp:entry_mapper:entries}

    </div>

