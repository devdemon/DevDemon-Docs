########################
Form Tag
########################
::

  {exp:forms:form}
      <!-- Template Code -->
  {/exp:forms:form}

Allows you to track hits on cached templates. This tag outputs and img tag which points to a special URL on your site to track hits.
It will do it's best to ignore the most popular search engines. You will place this tag only on Single Entry Pages, sicne you only want to count the hits for a single entry at a time right?

.. contents::
  :local:

***********************
Parameters
***********************

entry_id=""
==============
Entry ID of an Channel Entry. Use this parameter to grab the form linked to a specific entry.

url_title=""
==============
Same as entry_id="" but now it with the entry's url_title.

form_name=""
==============
This parameter can be used to specify a specific form by using it's form name

display_error=""
==============
This parameter allows you to specify how forms errors will be displayed

=================== ====================================================================================
Type                Description
=================== ====================================================================================
**default**         Standard EE error page
**inline**          Inline error reporting
=================== ====================================================================================

- **Default:**: default
- **Recommended**: inline

return=""
=============
This parameter allows you to define where the user will be returned after submitting the form. The parameter can be defined in two ways:

- Use the standard Template_Group/Template syntax to specify where to return the user. For instance, if you want the user to be returned to the "local" Template in the "news" Template Group, you would use: return="news/local"
- Use a full URL. For example: return="http://example.com/return.html"

If this parameter is not defined, they will be returned to the form page.

output_submit=""
==============
You can use this parameter to disable the output of the submit button.

**Default:** yes

output_js=""
==============
You can use this parameter to disable the output of the javascript

**Default:** yes

output_css=""
==============
You can use this parameter to disable the output of the CSS.

**Default:** yes

prefix=""
=============
This parameter allows you to change the default variable prefix used. This is especially useful when you are nesting tags to avoid variable collisions.

**Default:** prefix="forms"

For example the variable `{forms:count}`, if you use prefix="fm" the variable will now be {fm:count}

****************************
Conditionals
****************************

{if forms:no_form}
=====================
This tag will conditionally display the code inside the tag if no form was found

{if forms:closed}
=====================
This tag will conditionally display the code inside the tag if the form is closed


**********************
Variables
**********************

{forms:form_id}
=================
The internal Form ID

{forms:}
============
The full URL to the original image

	
**********************
Example
**********************

::

	{exp:channel:entries channel="blog"}
	
		<h2>{title}</h2>
		{body}
		
		{exp:hits:count_hits_image entry_id="{entry_id}"}
		{!-- EXAMPLE OUTPUT: <img src="http://www.mysite.com/?ACT=123?t=2&i=66" alt="" /> --}
	{/exp:channel:entries}