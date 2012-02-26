########################
Form Tag
########################
::

  {exp:forms:form}
      <!-- Template Code -->
  {/exp:forms:form}

This tag is responsible for displaying the complete form. Most of it's behaviour is specified in the UI. But you can still adjust some specific options.

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
=================
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
=================
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

**********************
Variables
**********************

{forms:form_id}
=================
The internal Form ID

{forms:label}
==============
The form label

{forms:short_name}
====================
The form short name

{forms:entry_id}
================
The entry_id linked to this form (if any)

{forms:channel_id}
===================
The channel_id of the entry linked to this form (if any)

{forms:ee_field_id}
====================
The field_id of the entry linked to this form (if any)

{forms:member_id}
==================
The member_id of the member who created this form

{forms:date_created}
=====================
Creation date of this form

{forms:date_last_entry}
========================
The date of the last entry submission

{forms:total_entries}
========================
The total amount of submissions

{forms:current_page}
======================
The current page number

{forms:total_pages}
=====================
The total amount of pages this form has

{forms:paged}
==============
A simpel variable that outputs "yes" if the current form has multiple pages

****************************
Variable Pairs
****************************

{forms:fields} {/forms:fields}
==================================
Lists all fields for this form

Here is a list of available variables WITHIN this variable pair

{forms:field}
--------------
Renders the field

{forms:field_type}
--------------------
The field type

****************************
Conditionals
****************************

{if forms:no_form}
==================
This tag will conditionally display the code inside the tag if no form was found

{if forms:closed}
=================
This tag will conditionally display the code inside the tag if the form is closed

**********************
Example
**********************
There are two ways to display a form. Using a single tag or a tag pair.
Difference? The tag pair version allows you to specify conditionals and style your multipage variables

Single Tag Version
===================

::

	{exp:forms:form form_name="untitled" display_error="inline"}


Tag Pair Version
==================

::

	{exp:forms:form form_name="untitled" display_error="inline"}

	<h1>{forms:label}</h1>
	{if forms:paged} <h3>Current Page: {forms:current_page} of {forms:total_pages}</h3>{/if}

	{if forms:closed} FORM IS CLOSED! {/if}
	{if forms:no_form} NO FORM FOUND! {/if}

	{forms:fields}
		{forms:field}
	{/forms:fields}

	{/exp:forms:form}

