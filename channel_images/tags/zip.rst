############
Zip Tag
############
::

	{exp:channel_images:zip}

This template tag allows you to create a .zip file from all the images in the entry (Local storage only)

.. contents::
  :local:

***********************
Requirements
***********************

- PHP 5.2+
- php_zip extension enabled

***********************
Zip Tag Parameters
***********************

entry_id=""
==============
Entry ID of an Channel Entry. Use this parameter to limit the image list to a specific entry.

url_title=""
==============
Same as entry_id="" but now it with the entry's url_title.

filename=""
==============
Filename for the .zip (without the .zip)

size=""
==============
If you want to zip specific sizes you can specify them here.
Seperate multiple by a pipe |

Note: For the "original" size use: ORIGINAL. Example: size="ORIGINAL|small|medium"


*********
Example
*********
::

	{!-- ON A SINGLE TEMPLATE --}
	{exp:channel_images:zip entry_id="{segment_3}"}
