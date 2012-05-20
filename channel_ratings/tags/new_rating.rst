########################
RATING: New Rating
########################
::

  {exp:channel_ratings:new_rating}
      <!-- Template Code -->
  {/exp:channel_ratings:new_rating}

This tag generates a form so you can submit ratings

.. contents::
  :local:

***********************
Parameters
***********************

entry_id=""
==============
For Channel Entries

url_title=""
==============
For Channel Entries

comment_id=""
==============
For Individual Comments

member_id=""
==============
For Site Members

ci_id=""
==============
For Channel Images

cf_id=""
==============
For Channel Files

cv_id=""
==============
For Channel Videos

br_id=""
==============
For BrilliantRetail Products

.. important:: You MUST use one of the above parameters.

collection=""
==============
A specific ratign collection

**Default:** collection="default"

min_value=""
==============
This parameter is used to force the user to have to submit a value equal to or higher than the specified value.

**Default:** min_value="1"

max_value=""
==============
This parameter is used to force the user to have to submit a value equal to or lower than the specified value.

**Default:** max_value="5"

allow_guests=""
==================
Allow guest submissions?

**Default:** no

allow_multiple=""
===================
Allow multiple submissions? Lets say you want to allow people to rate an entry multiple times.

**Default:** no

captcha=""
==============
Enable captcha?

**Default:** no (if yes, only works with guests)

return=""
=============
This parameter allows you to define where the user will be returned after submitting a rating. The parameter can be defined in two ways:

- Use the standard Template_Group/Template syntax to specify where to return the user. For instance, if you want the user to be returned to the "local" Template in the "news" Template Group, you would use: return="news/local"
- Use a full URL. For example: return="http://example.com/return.html"

If this parameter is not defined, they will be returned to the form page.

prefix=""
=============
This parameter allows you to change the default variable prefix used. This is especially useful when you are nesting tags to avoid variable collisions.

**Default:** prefix="rating"

For example the variable `{rating:count}`, if you use prefix="cr" the variable will now be {cr:count}

**********************
Variables
**********************

{rating:captcha}
=======================
This variable will render the captcha image is captcha in enabled

****************************
Variable Pairs
****************************

{rating:fields} {/rating:fields}
==================================
Loops over all rating fields defined for the collection

Here is a list of available variables WITHIN this variable pair

{rating:field_title}
---------------------
The rating field title

{rating:form_name}
-------------------
The form input name for this field 

****************************
Conditionals
****************************

{if rating:no_access}
======================
This tag will conditionally display the code inside the tag if the user has no access to view the form.
This can happen if the user is banned OR is a guest and gues access is not enabled

{if rating:already_rated}
==========================
This tag will conditionally display the code inside the tag if the user has already rated this item

{if rating:not_rated}
======================
This tag will conditionally display the code inside the tag if the user has not yet rated this item

**********************
Example
**********************
::

	{exp:channel_ratings:new_rating entry_id="{entry_id}" captcha="yes" max_value="5" return="/channel_rating/new_rating/"}
	
		{if rating:already_rated} You have already rated this entry{/if}

		{if rating:not_rated}
		
			{rating:fields}
				<label>{rating:field_title}</label>
				
				<select name="{rating:form_name}">
					<option value="1">1</option>
					<option value="2">2</option>
					<option value="3">3</option>
					<option value="4">4</option>
					<option value="5">5</option>
				</select>
			{/rating:fields}
			
			{!-- YOU CAN STILL HARDCODE THE form input name, for example: <select name="rating[default]"> --}
			
			{if rating:captcha}
				{rating:captcha}
				<input name="captcha" type="text"/>
			{/if}
			
			<input type="submit">
		{/if}
	
	{/exp:channel_ratings:new_rating}