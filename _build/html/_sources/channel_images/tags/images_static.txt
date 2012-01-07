######################
Images Static Tag
######################
::

  {exp:channel_images:images_static}
      <!-- Template Code -->
  {/exp:channel_images:images_static}

Turn special Channel Images variables in posts body into images!
This tag does NOT loop!

.. contents::
  :local:

***********************
Parameters
***********************

entry_id=""
==============
Entry ID of an Channel Entry. Use this parameter to limit the images list to a specific entry.

url_title=""
==============
Same as entry_id="" but now it with the entry's url_title.

category=""
==============
Limit the images list to a specific category as chosen in the Fieldtype.

skip_cover=""
===============
Skip cover images

- **Options:** yes | no
- **Default:** no

offset=""
==========
This parameter offsets the display by X number of entries. For example, if you want to show all entries except the three latest ones, you would do this: offset="3"

img_prefix=""
==============
Add a prefix to the tag outputted by the `{image:1}` variable
You can also use {IMG_TITLE} and {IMG_DESC} in this parameter

img_suffix=""
==============
Add a suffix to the tag outputted by the `{image:1}` variable
You can also use {IMG_TITLE} and {IMG_DESC} in this parameter

prefix=""
==========
This parameter allows you to change the default variable prefix used. This is especially usefull when you are nesting tags to avoid variable collisions.

**Default:** prefix="image"
For example the default variable for the image URL is: `{image:url}` but if you use prefix="ci" the variable for the image URL will now be {cf:url}

**********************
Variables
**********************
In the following list ORDER refers to the Image Order in the publish form

{image:ORDER}
=============
This variable renders an image tag of the corresponding image.
For example: <img src="url_to_img" alt="img_title"/ >

{image:ORDER:title}
====================
The image title as specified in the field row

{image:ORDER:description}
==========================
The image description as specified in the field row

{image:ORDER:filename}
=======================
The filename of the image

{image:ORDER:url}
==================
The full URL to the image

{image:ORDER:secure_url}
=========================
The full URL to the image but now with HTTPS

{image:ORDER:SIZENAME}
=======================
This variable renders an image tag of the corresponding image SIZE.
For example: <img src="url_to_img_size" alt="img_title"/ >

{image:ORDER:url:SIZENAME}
===========================
THe full URL to the specific image size

{image:ORDER:secure_url:SIZENAME}
==================================
THe full URL to the specific image size but now with https

****************************
Conditionals
****************************

{if image:no_images}
=====================
This tag will conditionally display the code inside the tag if there are no images in current category

**********************
Example
**********************

Imagine this is the text in your post
::

	Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque in lacinia purus.
	
	{image:1}
	{image:1:description}
	
	Quisque molestie tempus mauris eu lobortis. Sed id nunc eu diam dapibus mollis non id ligula.
	
	{image:2}
	{image:2:description}
	
	Ut bibendum mauris in lectus suscipit dictum. Donec lacinia pulvinar nisi, ac dignissim mauris molestie id.
	Praesent pellentesque vestibulum ligula venenatis sollicitudin.

	
You can then use this in your template
::

	{exp:channel:entries channel="about" url_title="{segment_3}"}
	    <h2>{title}</h2>
	    {exp:channel_images:images_static entry_id="{entry_id}"}
	        {body}
	        {extended}
	    {/exp:channel_images:images_static}
	{/exp:channel:entries} 
	
Which will render like this
::

	Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque in lacinia purus.
	
	<img src="url_to_img" alt="some title">
	This is a very funny image
	
	Quisque molestie tempus mauris eu lobortis. Sed id nunc eu diam dapibus mollis non id ligula.
	
	<img src="url_to_img2" alt="another title">
	This one if even better!
	
	Ut bibendum mauris in lectus suscipit dictum. Donec lacinia pulvinar nisi, ac dignissim mauris molestie id.
	Praesent pellentesque vestibulum ligula venenatis sollicitudin.
