###########################
Custom Editor Buttons
###########################

You can create custom Editor buttons with ease by following this document.


Sample
==========================
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
			'name' 		=> 'My Btn',
			'version'	=> '1.0.0',
			'callback'	=> 'my_custom_function',
			'dropdown'	=> FALSE,
		);

		public $dropdown = array();

		/**
		 * Constructor
		 *
		 * @access public
		 *
		 * Calls the parent constructor
		 */
		public function __construct()
		{
			parent::__construct();
		}

		// ********************************************************************************* //
	}

