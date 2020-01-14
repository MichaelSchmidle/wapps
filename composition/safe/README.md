# About Safe Wapp

The safe wapp is based on [Passit](https://passit.io/).

> Peace of mind for passwords

# Notes

After deploying and upgrading this wapp, you need to run the database migration routine via the containers command line. Inside Portainer, select the container ``${NAME}_passit_1``. Connect to the container's console, and execute the following command:

``./manage.py migrate``
