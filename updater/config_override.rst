###########################
Config.php overrides
###########################

All settings in Updater can be set in the config.php file.

These settings will override settings stored in the DB and will prevent them from being changed (form input will be disabled).
::

	$config['updater']['file_transfer_method'] = 'local'; // local, ftp, sftp

	$config['updater']['ftp']['hostname'] = '';
	$config['updater']['ftp']['username'] = '';
	$config['updater']['ftp']['password'] = '';
	$config['updater']['ftp']['port'] = '21';
	$config['updater']['ftp']['passive'] = 'yes'; // yes, no
	$config['updater']['ftp']['ssl'] = 'no'; // yes, no

	$config['updater']['sftp']['hostname'] = '';
	$config['updater']['sftp']['username'] = '';
	$config['updater']['sftp']['password'] = '';
	$config['updater']['sftp']['port'] = '22';

	$config['updater']['path_map']['root'] = ''; // Document Root
	$config['updater']['path_map']['backup'] = ''; // Backup Dir
	$config['updater']['path_map']['system'] = ''; // System Dir
	$config['updater']['path_map']['system_third_party'] = ''; // Third Party dir system dir
	$config['updater']['path_map']['themes'] = ''; // Themes dir
	$config['updater']['path_map']['themes_third_party'] = ''; // Third Party dir in themes dir
