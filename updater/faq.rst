###########################
Frequently asked questions
###########################

The Updater module supports updating ExpressionEngine installations and addons. But there are some limitations and guidelines.

What are the system requirements?
==================================
Updater needs a couple of things to work correctly.

======================= ===============================================================================================================================================
Requirement             Description
======================= ===============================================================================================================================================
**php_zip**             Your installation needs to have the PHP ZIP extension enabled. We need this to unzip the .zip (it's enabled by default in PHP 5.3)
**post_max_size (5MB)** Your server must be able to support file uploads of that are larger then 5MB. A typical ExpressionEngine installation is around 5MB in size
**upload_max_size**     Ditto as above..
**File Permissions**    The webserver must have write permissions to the system dir.
======================= ===============================================================================================================================================

Is Updater MSM compatible?
============================
Short answer: Yes
MSM sites are really only seperated in the database. All files are shared among the sites.

Where does Updater stores backup files?
=========================================
By default Updater will put them in your document_root. This can be changed in the module settings as of v2.0.5

