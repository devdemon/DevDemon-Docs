########################
LIKE: New Like
########################
::

  {exp:channel_ratings:new_like}
      <!-- Template Code -->
  {/exp:channel_ratings:new_like}

This tag generates an url so you can submit likes/dislikes

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

allow_guests=""
==================
Allow guest submissions?

**Default:** no

allow_multiple=""
===================
Allow multiple submissions? Lets say you want to allow people to like an entry multiple times.

**Default:** no

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

{rating:like_url}
=======================
The Like URL

{rating:dislike_url}
=======================
The DisLike URL

****************************
Conditionals
****************************

{if rating:no_access}
======================
This tag will conditionally display the code inside the tag if the user has no access to view the form.
This can happen if the user is banned OR is a guest and gues access is not enabled

**********************
Example
**********************
::

	{exp:comment:entries channel="default" entry_id="{entry_id}"}
	
	    {exp:channel_ratings:likes comment_id="{comment_id}"}
	        {rating:liked} people found this review usefull <br />
	        
	        {if rating:not_voted}
	        
	            {exp:channel_ratings:new_like comment_id="{comment_id}"}
	            
	            	I <a href="{rating:like_url}">like</a> this
	            	I <a href="{rating:dislike_url}">don't like</a> this
	            	
	            {/exp:channel_ratings:new_like}
	            
	        {/if}
	        
	    {/exp:channel_ratings:likes}
	
	    {comment}
	    <p>By {name} on {comment_date format="%Y %m %d"}</p>
	    
	{/exp:comment:entries}