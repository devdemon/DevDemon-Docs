###########################
Config.php overrides
###########################

All settings in Updater can be set in the config.php file.

These settings will override settings stored in the DB and will prevent them from being changed (form input will be disabled).
::

	$config['editor']['s3']['aws_access_key'] = '';
	$config['editor']['s3']['aws_secret_key'] = '';
