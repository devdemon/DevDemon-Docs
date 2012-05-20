#############
AJAX Likes
#############

These days users expect a more modern way of casting their vote. This tutorial will help you with creating a dynamic like voting system using AJAX.

Minimum Requirements
=====================
- Channel Ratings 4.0.2
- jQuery 1.7+

Live DEMO
===========
We created a demo page where you can see this in action: http://demo.devdemon.com/channel_ratings_likes/ajax_like/

The Template
================
There is nothing special about the template code we are going to use. We are going to use the regular tags add some CSS classes. The same template code will work with users who have Javascript disabled.

.. code-block:: ci

	{exp:channel:entries}
		<h1>{title}</h1>

		{channel_ratings_body}

		<div class="likeblock">
		{exp:channel_ratings:likes entry_id="{entry_id}"}

			{if rating:not_voted}

			{exp:channel_ratings:new_like entry_id="{entry_id}" allow_guests="yes"}
			<div class="like_btn"><a href="{rating:like_url}">I like this</a></div>
			{/exp:channel_ratings:new_like}

			{/if}
			<span class="total_likes">{rating:liked}</span> people likes this
		{/exp:channel_ratings:likes}
		</div>

		<br><br>
	{/exp:channel:entries}

This is just an example template code. You should modify your `{exp:channel:entries}` to fit your site/design.
The `{exp:channel_ratings:likes}` template can also be modified but the `<div class="likeblock">` and `<div class="like_btn">` HTML tag should not be changed since the Javascript code we are going to use will look for those classes.

The CSS
==========
This is just a regular CSS to style the like button.

.. code-block:: css

	.likeblock {margin:6px 0;}
	.likeblock .like_btn {background-color:#ECEEF5; border-color: #CAD4E7; border-radius:3px 3px 3px 3px; display:inline-block; padding: 4px 5px;}
	.likeblock .loading {display:none}


The Javascript
===============
This Javascript code is responsible for everything. It will execute the AJAX request and act depending on the return response from the server.

.. code-block:: javascript

	$(document).ready(function(){

		$('.likeblock .like_btn a').on('click', function(e){
			e.preventDefault();
			var Parent = $(e.target).closest('.likeblock');
			$(e.target).html('loading...');
			$.get( e.target.href, {}, function(rData){

				if (rData.success == 'yes') {
					Parent.find('.total_likes').html(rData.stats.likes);
					if (rData.action == 'new_like') Parent.find('.like_btn a').attr('href', rData.delete_url ).html('Undo');
					if (rData.action == 'del_like') Parent.find('.like_btn').html(rData.body);
				} else {
					alert(rData.body);
				}
			}, 'json');
		});
	});


We didn't include any comments in the code since comments are not recommended in production. Lets go step by step over this code.

::

	$('.likeblock .like_btn a').on('click', function(e){

Here is where everything starts. Attaching the 'click' event to the `<a>` tag inside of the .like_btn div. The rest of the code will only execute when you click on the tag.

:: 

	e.preventDefault();

This method call prevents the browser from following the link. People with Javascript disabled will just follow the link and register their like the old fashion way.

::

	var Parent = $(e.target).closest('.likeblock');

For performance reasons we are going to store the parent .likeblock in a variable.

::

	$(e.target).html('loading...');

Now we need to tell the user we are going to do something. We can show them a 'loading' spinner. But in this example we are just going to replace the text in the `<a>` tag with: loading...

::

	$.get( e.target.href, {}, function(rData){

Now we are actually going to execute the AJAX call. 

::

	if (rData.success == 'yes') {

When the AJAX request comes back in JSON form. We can check if the action we executed was successful. There are a couple of reasons why this might fail. For example if the user already liked the entry. If the 'success' property is not yes, we are going to alert the user with the error message.

:: 

	Parent.find('.total_likes').html(rData.stats.likes);

If the request was successful we are going to update the like count on the page.

::	

	if (rData.action == 'new_like') Parent.find('.like_btn a').attr('href', rData.delete_url ).html('Undo');

If we just liked the entry, we have the option to give the user an UNDO link. With this code we are replacing the `href` attribute and changing the text to: Undo. When the user clicks on the same link again the whole process will start over but this time it will delete his 'like' vote.

::	

	if (rData.action == 'del_like') Parent.find('.like_btn').html(rData.body);

If the user just deleted their 'like' vote. We should remove the `<a>` tag and replace it with a success message.











