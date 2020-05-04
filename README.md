HelpSpot allows the option to save all request file attachments in the database. This makes for easy backups. However, on some high volume installations or installations which deal in many large attachments it's better to save the attachments to disk to prevent the database from becoming unwieldy.

# Moving to File System Storage

Create a directory to store attachments in. This directory should be outside the web root and writable by the web server.
In Admin->Settings->System change Attachment Storage Location to "Server File System"
In the box that appears (Attachment File System Directory) put the full path to the directory you created
Save the settings

# Converting Database Stored Attachments to the File System

By default, after the change above HelpSpot will store new attachments to the file system, but old attachments will continue to be stored and served from the database. **On version 4 and greater you can use the HelpSpot command attachments:tofile, you don't need to use this script.**
 
 If you'd like to convert these old attachments on HelpSpot version 3 to the file system you can use the script linked below do to so. To use the script:

1. Download the script found in this repository, move it to the root HelpSpot folder. This is the one with config.php in it. If using FTP to move the file be sure to force binary mode.
2. Backup your database (seriously)
3. Place HelpSpot in maintenance mode to prevent new requests while the script runs (Admin->Settings)
4. From the command line do "/path/to/php -f /path/to/convert_attach_from_db_to_file.php"

you can run it from the browser if you have no choice, though you may have to restart it from time to time if the web server times out. Note that the file may take hours to run if you have a lot of attachments.
