# Mark Service

The mark service (i.e. Wallabag) comes with the predefined admin user ``wallabag``. Remember to at least change the password of this default user—which can be done directly via the Wallabag web interface.

For advanced users: In case you want to also change the username, you can use the data service to connect to the MySQL database of the mark service (i.e. to the host ``mark_mysql_1`` and the database ``mark``). Just use the credentials that you configured in the ``.env`` file of the mark service. Then browse to the user table and modify the username of the default user.
