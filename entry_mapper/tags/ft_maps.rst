#################
Fieldtype: Maps
#################
The Entry Mapper: Maps fieldtype allows you to link any map to an entry.
In your templates you can then use the field tag to render the map and it's entries

.. contents::
  :local:

**********************
Examples
**********************

Variable Pair Mode
==================================
::

    {exp:channel:entries channel="maps"}
    <h1>{title}</h1>

    <hr>

      {entry_mapper_maps}
      <div id="world_map" style="position:relative;width:{mapper:image_width};height:{mapper:image_height};">
          <img src="{mapper:image_url}" width="{mapper:image_width}" height="{mapper:image_height}">

          {mapper:entries}
          <span class="entry" style="position:absolute;top:{mapper:css_top};left:{mapper:css_left};">
              {mapper:entry_title}
          </span>
          {/mapper:entries}

      </div>
      {/entry_mapper_maps}

    {/exp:channel:entries}


Single Var Mode
==================================
::

  {exp:channel:entries channel="maps"}
    <h1>{title}</h1>

    <hr>

    {exp:entry_mapper:map map_id="{entry_mapper_maps}"}
    <div id="world_map" style="position:relative;width:{mapper:image_width};height:{mapper:image_height};">
        <img src="{mapper:image_url}" width="{mapper:image_width}" height="{mapper:image_height}">

        {mapper:entries}
        <span class="entry" style="position:absolute;top:{mapper:css_top};left:{mapper:css_left};">
            {mapper:entry_title}
        </span>
        {/mapper:entries}

    </div>
    {/exp:entry_mapper:map}

  {/exp:channel:entries}
