# Fin Service

According to the official [Firefly III Documentation](https://firefly-iii.readthedocs.io/en/latest/installation/docker.html#docker-hub-with-automatic-updates-via-docker-compose), the database requires initialization after starting the service. So, after ``$ sudo docker-compose up -d``, run the following additional commands:

```
$ sudo docker-compose exec firefly php artisan migrate --seed
$ sudo docker-compose exec firefly php artisan firefly:upgrade-database
$ sudo docker-compose exec firefly php artisan firefly:verify
$ sudo docker-compose exec firefly php artisan passport:install
```

Also, as long as [Issue #1320](https://github.com/firefly-iii/firefly-iii/issues/1320) is not released, please perform the following additional steps:

```
$ sudo docker exec -it wapps_fin_firefly_1 bash
$ chown www-data: /var/www/firefly-iii/storage/logs/laravel.log
```
