# Fin App

According to the official [Firefly III Documentation](https://firefly-iii.readthedocs.io/en/latest/installation/docker.html#docker-hub-with-automatic-updates-via-docker-compose), the database requires initialization after starting the app. So, after ``$ sudo docker-compose up -d``, run the following additional commands:

```
$ sudo docker-compose exec firefly php artisan migrate --seed
$ sudo docker-compose exec firefly php artisan firefly:upgrade-database
$ sudo docker-compose exec firefly php artisan firefly:verify
$ sudo docker-compose exec firefly php artisan passport:install
```
