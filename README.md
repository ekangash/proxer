

C:\Windows\System32\drivers\etc\hosts


# Получаем сертификаты

Находясь в папке nginx вводим

```shell
curl -L https://raw.githubusercontent.com/dancheskus/nginx-docker-ssl/master/init-letsencrypt.sh > init-letsencrypt.sh
```

Затем открываем полученный init-letsencrypt.sh и вписываем:

- вместо example.com свои домены через пробел
- email
- меняем пути, если меняли их в папке
- staging временно ставим 1 (для теста)

`chmod +x init-letsencrypt.sh`

`sudo ./init-letsencrypt.sh`


Выполнив последнюю команду в папке nginx -> data появятся новые папки с сертификатами необходимые для работы nginx и certbot Если в тестовом режиме все получилось, то ставим staging=0 и повторяем процедуру.


`docker-compose run --rm --entrypoint "certbot certificates" certbot` - позволяет проверить зарегистрированные сертификаты и узнать их срок годности.