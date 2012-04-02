######################
Structure Support
######################

The Forms module supports Structure based sites since version 2.0.4.
At the Time of Writing Structure (3.2.3) does not support the method Forms uses to display inline errors.

We have asked the makers of Structure to add needed code change. (this page will be updated once that has happened)

To enable this support a super small change has to be made to ext.structure.php
Please follow these instructions:

#. Please backup your site and your structure files. Just to be safe!
#. Open ext.structure.php which is located in the /system/expressionengine/third_party/structure/ folder.
#. Around line 46 find: if (REQ == 'PAGE'
#. Replace that with: if ( (REQ == 'PAGE' OR REQ == 'ACTION')
#. That whole line should now read like this:

::	
	if ( (REQ == 'PAGE' OR REQ == 'ACTION') && array_key_exists('uris', $this->site_pages) && is_array($this->site_pages['uris']) && count($this->site_pages['uris']) > 0)

