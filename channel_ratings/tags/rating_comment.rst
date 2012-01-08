########################
RATING: Comment Rating
########################
::

  {exp:channel_ratings:rating_comment}
      <!-- Template Code -->
  {/exp:channel_ratings:rating_comment}

This tag will display the rating ratings of an individual comment

.. contents::
  :local:

***********************
Parameters
***********************

comment_id=""
==============
REQUIRED: The ID of comment

collection=""
==============
Limit by rating collection.

**Default:** collection="default"

precision=""
==============
This parameter allows you to specify the number of decimals to round fractions on numerical rating fields for averages.
For example, a value of 1 would give you a result like this for a rating value: 4.5

**Default:** precision="2"

thousands=""
==============
This parameter allows you to specify which character to use to separate groups of thousands in numeric rating fields. For example, a value of , would parse 10000 as 10,000. Default is , (comma).

**Default:** thousands=","

fractions=""
==============
This parameter allows you to specify which character to indicate fractions in numeric ratings. (Decimals)

**Default:** fractions="."

scale=""
==============
By default, Channel Ratings assumes your rating scale is 5. As in, your numerical ratings are out of 5 (ex: 1 out of 5 stars, 2 out of 5 stars, etc). You can however, change the scale to be out of "10" by specifying the scale parameter. When you specify this, the stars variable pairs will switch from the default of 5 graphic images to 10 when placed around your numerical rating value.

**Default:** scale="5"

theme=""
==============
Since you can have your own custom themes, this parameter allows you to specify which theme to use.

**Default:** theme="stars"

prefix=""
=============
This parameter allows you to change the default variable prefix used. This is especially useful when you are nesting tags to avoid variable collisions.

**Default:** prefix="rating"

For example the variable `{rating:count}`, if you use prefix="cr" the variable will now be {cr:count}

**********************
Variables
**********************

{rating:FIELDNAME:rating}
=========================
This variable outputs the rating value for the specified field

{rating:FIELDNAME:stars}
=========================
This variable outputs "star" images to construct a graphical representation of the rating value for the specified field

{rating:overall:rating}
========================
This variable outputs the overall average rating value for all fields.

{rating:overall:stars}
=======================
This variable outputs "star" images to construct a graphical representation of the overall average rating value for all fields.

****************************
Conditionals
****************************

{if rating:no_rating}
======================
This tag will conditionally display the code inside the tag if there are no stats to display

**********************
Example
**********************
::

	{exp:comment:entries sort="asc" limit="20"}
	        {comment}
	        
	        <p>By {name} on {comment_date format="%Y %m %d"}</p>
	        
	        Rating: {exp:channel_ratings:rating_comment comment_id="{comment_id}"} {rating:overall:stars} {/exp:channel_ratings:rating_comment}
	{/exp:comment:entries}