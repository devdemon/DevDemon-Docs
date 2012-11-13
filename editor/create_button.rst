###########################
Custom Editor Buttons
###########################

You can create custom Editor buttons with ease by following this document.
You also will need to reference the redactor.js API to work with the editor itself.


Anatomy of a Plugin
==========================
A button consists of a class and at least one function:

::

	// File: editor.mybtn.php

	class Mybtn_ebtn extends Editor_button
	{
		/**
		 * Button info - Required
		 *
		 * @access public
		 * @var array
		 */
		public $info = array(
	        'name'          => 'Button Label',
	        'author'        => 'Author',
	        'author_url'    => 'Author URL',
	        'description'   => 'Button Description',
	        'version'       => 'Version Number',
	        'settings'      => FALSE,
	        'callback'      => 'JS Callback',
	        'button_css'    => '',
	        'button_css_hq' => '',
	    );

		/**
		 * Constructor
		 *
		 * @access public
		 *
		 * Calls the parent constructor
		 */
		public function __construct($settings=array())
		{
			parent::__construct($settings;
		}

		// ********************************************************************************* //
	}

Class properties & methods
=====================================
In addition to the class and function, you should also add some information that will display in the Button Manager.


$info array
-----------------------
The information is as follows:

- **name:** The display name of the button
- **version** The button version number
- **author::** The name of the button author
- **author_url:** The URL associated with the author (or a URL to a page about the Button)
- **description:**  A short description of the purpose of the Button
- **settings:** (bool) Does this button have any settings?
- **callback:** Javascript Callback that gets called when the button is pressed. Leave empty or BOOL false to use Dropdowns instead
- **button_css:** (optional) Button CSS. Example base64encoded background image: background-image: url(data:image/png;base64,fooooo);
- **button_css_hq:** (optional) Button CSS High Quality (for retina displays)

__constructor()
---------------------
$this->EE =& get_instance(); is already called for you in the parent constructor. $this->settings is also automatically mapped for you.


display()
---------------------
If present, this method gets called while preparing the Editor HTML output. Return any HTML you would like to be included.
Here you can also call the css/js helper method in case you need to include any css/js on the page.

- Example use jquery plugin: $this->css_js('js', 'url', URL_TO_PLUGIN, 'jquery', 'colorpicker');
- Example use inline css: $this->css_js('css', 'inline', $inline_css, 'mybutton', 'main');

display_settings()
------------------------
Render your settings page. Return valid HTML. Do not include a <form> element, this has already been done for you.

save_settings()
------------------------
Return a valid array
