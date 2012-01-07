############
Grouped Files Tag
############
::

  {exp:channel_files:grouped_files}
      <!-- Template Code -->
  {/exp:channel_files:grouped_files}

This tag makes displaying files by category easier. It will automatically sort the files by category.

.. contents::
  :local:

***********************
Parameters
***********************

All parameters of :doc:`./files` can be used here.

category_sort=""
==============
The sort order can be ascending or descending. Setting options for this parameter include:
- category_sort="asc"
- category_sort="desc"

**Default:** category_sort="asc'


**********************
Variables
**********************
{file:category}
==========
The category name

****************************
Variable Pairs
****************************

{files} {/files}
================
Lists all files in the category

All variables of :doc:`./files` can be used here. 

****************************
Conditionals
****************************
These individual conditional variables are for use inside the {files} tag pair.

{if file:no_files}
==================
This tag will conditionally display the code inside the tag if there are no files in current category

**********************
Example
**********************
::

	{exp:channel:entries channel="about" url_title="{segment_3}"}
		<h2>{title}</h2>
		
		{exp:channel_files:grouped_files entry_id="{entry_id}"}
			<strong>{file:category}</strong>
			{files}
				<a href="{file:locked_url}" title="{file:title}">{file:title}</a>
			{/files}
		{/exp:channel_files:grouped_files}
		
	{/exp:channel:entries}