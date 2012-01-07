############
Zip Tag
############
::

	{exp:channel_files:zip}  

This template tag allows you to create a .zip file from all the files in the entry (Local storage only)

.. contents::
  :local:

***********************
Zip Tag Parameters
***********************

entry_id=""
==============
Entry ID of an Channel Entry. Use this parameter to limit the files list to a specific entry.

url_title=""
==============
Same as entry_id="" but now it with the entry's url_title.

filename=""
==============
Filename for the .zip (without the .zip)

*********
Example
*********
::

	{!-- ON A SINGLE TEMPLATE --}
	{exp:channel_files:zip entry_id="{segment_3}"}