# Safe App

After starting the service for the first time with ``$ sudo docker-compose up -d``, sign up as new user.

Once you have created your user, you have the option to disable sign-up of further new users. Simply uncomment the following line in the ``.env`` file by removing the leading ``#`` character:

```
SIGNUPS_ALLOWED=false
```

Then, re-compose the service by executing the following command:

```
$ sudo docker-compose down && sudo docker-compose up -d
```
