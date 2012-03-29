######################
Next/Prev Image Tag
######################
::

	{exp:channel_images:prev_image}
		<!-- Template Code -->
	{/exp:channel_images:prev_image}

	{exp:channel_images:next_image}
		<!-- Template Code -->
	{/exp:channel_images:next_image}

This tag makes displays the next image in the list.

.. contents::
  :local:

***********************
Parameters
***********************

image_id=""
=================
The Image ID of the current displayed image.

url_title=""
=================
The URL Title of the current displayed image.

.. important:: You MUST use one of the above parameters.


**********************
Variables
**********************
Available variables..

Most of the variables of :doc:`./images` can be used here.

****************************
Conditionals
****************************
These individual conditional variables are for use inside the {images} tag pair.

{if image:no_image}
=====================
This tag will conditionally display the code inside the tag if there are no Next/Previous

**********************
Example
**********************
::

	{exp:channel_images:images image_id="{segment_3}"}
		<img src="{image:url:medium}">
	{/exp:channel_images:images}

	<br><br clear="all">

	{exp:channel_images:prev_image image_id="{segment_3}"}
		<div style="float:left">
			<strong>Previous Image</strong><br>
			<a href="{path="/{segment_1}/{segment_2}/{image:id}"}"><img src="{image:url:small}"></a>
		</div>
	{/exp:channel_images:prev_image}



	{exp:channel_images:next_image image_id="{segment_3}"}
		<div style="float:right">
			<strong>Next Image</strong><br>
			<a href="{path="/{segment_1}/{segment_2}/{image:id}"}"><img src="{image:url:small}"></a>
		</div>
	{/exp:channel_images:next_image}

	<br clear="all">