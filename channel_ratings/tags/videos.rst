############
Videos Tag
############
::

  {exp:channel_videos:videos}
      <!-- Template Code -->
  {/exp:channel_videos:videos}

This template tag allows you to show all videos within a single entry.

.. contents::
  :local:

***********************
Parameters
***********************

entry_id=""
==============
Entry ID of an Channel Entry. Use this parameter to limit the videos list to a specific entry.

url_title=""
==============
Same as entry_id="" but now it with the entry's url_title.

video_id=""
============
Video ID of an video. Use this parameter to limit the video list to a specific video.

orderby=""
=============
The "order" parameter sets the display order of the videos. Setting options for this parameter include:

-  orderby="duration"
-  orderby="views"
-  orderby="date"

**Default:** orderby="video_order"

sort=""
=============
The sort order can be ascending or descending. Setting options for this parameter include:
- sort="asc"
- sort="desc"

**Default:** sort="asc'

limit=""
=========
This parameter limits the number of videos on any given page. The limit will default to 30 entries if a value is not specified. If you are using pagination then this will determine the number of entries shown per page.

**Default:** limit="30"

offset=""
=============
This parameter offsets the display by X number of entries. For example, if you want to show all entries except the three latest ones, you would do this: offset="3"

embed_width=""
===============
The width of the embed. Default: 480

embed_height=""
================
The width of the embed. Default: 385

**Default:** prefix="video"

For example the default variable for the file URL is: `{video:title}` but if you use prefix="cv" the variable for the file URL will now be {cv:title}

**********************
Variables
**********************

{video:id}
=================
The internal Video ID

{video:service}
=================
Displays from video service this video is from.
Possible value: youtube or vimeo

{video:service_id}
===================
This variable displays the ID of the video (the video ID of youtube or vimeo)

{video:title}
=================
The video title

{video:description}
====================
The video description

{video:username}
=================
The username of the author (if available)

{video:author}
=================
The video author

{video:date} 
=======================
The date the video has been published
For date variable info see: http://expressionengine.com/user_guide/templates/date_variable_formatting.html

{video:views}
=================
The amount of views a video has received

{video:duration}
=================
The duration of the video.
Example output: 32 sec or 23min etc

{video:duration_secs}
========================
The duration of the video in seconds

{video:url}
=================
The URL to the SWF

{video:url_hd}
=================
The URL to the SWF in HD (Youtube only)

{video:img_url}
=================
The URL to an image of the video
Most of the time it's 120x90

{video:img_url_hd}
====================
A higher quality URL to an image of the video
Most of the time it's 480x360

{video:web_url}
=================
The full URL to the webpage of the video

{video:embed_code}
====================
This variable will output the embed code for the video.

{video:embed_code_hd}
=======================
This variable will output the embed code for the video.
But this time in HD (youtube only)

{video:count}
=================
The "count" out of the current videos being displayed. If five videos are being displayed, then for the fourth video the {video:count} variable would have a value of "4".

{video:total}
=================
The total number of videos being displayed.

****************************
Conditionals
****************************

{if video:no_videos}
=====================
This tag will conditionally display the code inside the tag if there are no videos


**********************
Example
**********************
::

	{exp:channel:entries channel="default_site"}
	    <h1>{title}</h1>   
	     
	    {exp:channel_videos:videos entry_id="{entry_id}"}
	        <h3>{video:title}</h3>
	        {video:embed_code}
	    {/exp:channel_videos:videos}
	    
	{/exp:channel:entries}