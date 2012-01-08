################
Decode Tag
################
::

  {exp:tagger:tagname}
      <!-- Template Code -->
  {/exp:tagger:tagname}

This template tag allows you to decode a tag name super quick.

.. contents::
  :local:

***********************
Parameters
***********************

tag=""
==============
The tag you would want to decode

unitag=""
==============
If it's a unitag, use this parameter.

**********************
Example
**********************
::

	<h1>Entries tagged: {exp:tagger:tagname tag="{segment_3}"}</h1>  