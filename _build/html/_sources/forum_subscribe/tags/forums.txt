############
Forums Tag
############
::

  {exp:forum_subscribe:forums}
      <!-- Template Code -->
  {/exp:forum_subscribe:forum}

You can add a link within your forums templates to allow users to subscribe.
Then provide a link within each forum to allow them to unsubscribe. This gives members quick subscription access.

.. contents::
  :local:

**********************
Variables
**********************

{forum_category}
=================
The forum Category the forum belongs to

****************************
Variable Pairs
****************************

{forums} {/forums}
==================================
Lists all forums within the category
Here is a list of available variables WITHIN this variable pair

{forum_name}
-----------------
The forum name

{forum_url}
------------------
The URL to the forum

{forum_subscribe_url}
---------------------
This variable will output a unique URL which allows the user to subscribe to the forum if he has not subscribed yet.
Or unsubscribe if he already has. So this URL has dual purpose.

****************************
Conditionals
****************************

{if subscribed}
=====================
This tag will conditionally display the code inside the tag if the user is subscribed!


**********************
Example
**********************
::

	{exp:forum_subscribe:forums}
		<strong>{forum_category}</strong>
		
		{forums}
			<p>
				{forum_name}: 
				{if subscribed}
					<strong>SUBSCRIBED</strong> - <a href="{forum_subscribe_url}">Click to Unsubscribe</a> 
				{if:else}
					<a href="{forum_subscribe_url}">Subscribe to forum</a>
				{/if}
			</p>
		{/forums}
	{/exp:forum_subscribe:forums}