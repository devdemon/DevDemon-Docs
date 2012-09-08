######################
Directory Structure
######################

We need some way of detecting a valid addon package one of them is by enforcing a specific directory structure in the .zip file.
It's pretty straightforward since we are using the same layout as the ExpressionEngine installation .zip

=============== ===============================================
DIR             Path
=============== ===============================================
SYSTEM          /system/expressionengine/third_party/ADDON/
SYSTEM          /ee2/third_party/ADDON/
THEMES          /themes/third_party/ADDON/
=============== ===============================================

They can live in Sub-directories (unlimited depth)
For example:

::

	/one/two/three/system/expressionengine/third_party/ADDON/
