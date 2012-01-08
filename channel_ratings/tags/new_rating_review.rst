#############################
RATING: Comment With Rating
#############################
::

  {exp:comment:form}
      <!-- Template Code -->
  {/exp:comment:form}

To attacht a rating to a comment (like reviews), you need to use the {exp:comment:form} tag and configure rating through parameters.

.. contents::
  :local:

***********************
Parameters
***********************

rating:enabled=""
==================
REQUIRED: You need to set this parameter to "yes" for the ratings function to work.

**Default:** rating:enabled="no"

rating:required=""
==================
Is a rating required? Set this to "no" if you don't want to force people to submit a rating along with their comments

**Default:** rating:required="yes"

rating:collection=""
=====================
A specific ratign collection

**Default:** rating:collection="default"

rating:min_value=""
=====================
This parameter is used to force the user to have to submit a value equal to or higher than the specified value.

**Default:** min_value="1"

rating:max_value=""
====================
This parameter is used to force the user to have to submit a value equal to or lower than the specified value.

**Default:** max_value="5"

rating:allow_guests=""
=======================
Allow guest submissions?

**Default:** no

rating:allow_multiple=""
=========================
Allow multiple submissions? Lets say you want to allow people to rate an entry multiple times.

**Default:** no

rating:return=""
=================
This parameter allows you to define where the user will be returned after submitting a rating. The parameter can be defined in two ways:

- Use the standard Template_Group/Template syntax to specify where to return the user. For instance, if you want the user to be returned to the "local" Template in the "news" Template Group, you would use: return="news/local"
- Use a full URL. For example: return="http://example.com/return.html"

If this parameter is not defined, they will be returned to the form page.

rating:prefix=""
==================
This parameter allows you to change the default variable prefix used. This is especially useful when you are nesting tags to avoid variable collisions.

**Default:** prefix="rating"

For example the variable `{rating:count}`, if you use prefix="cr" the variable will now be {cr:count}

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
============================
This tag will conditionally display the code inside the tag if you have already submitted a comment WITH rating for this entry, since you can comment an entry multiple times

{if rating:not_rated}
===========================
This tag will conditionally display the code inside the tag if you have NOT already submitted a comment WITH rating for this entry, since you can comment an entry multiple times 


**********************
Example
**********************
::

	{exp:comment:form channel="products" entry_id="{entry_id}" dynamic="off" rating:enabled="yes"}
	
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
		{/if}
		
		<label>Review</label>
		<textarea name="comment" cols="70" rows="2"></textarea> <br />
		
		<input type="submit" value="Submit Comment">
	
	{/exp:comment:form}