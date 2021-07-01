# Вопросы для собеседования

## Общее (10 мин)

* Какую роль ты выполнял в последнем проекте? Что делала остальная команда? Что нравится или не нравится на этом месте?
* Расскажите о сложностях в работе над проектом. Как их решали?
* Есть ли собственный проект? Что в нем интересного?
* Что тебя мотивирует в работе? А что демотивирует?

## Архитектурные вопросы (30 мин)

### 0. (5 мин)

Для разминки: с какими терминами ты знаком, и пара слов о них.

* KISS, DRY, YAGNI, SOLID
* TDD, BDD
* DDD
* CRUD, ACID
* ORM, ODM  
* MVC, MVVM

### 1. (5 мин)

Есть микросервис "курс валют". При получении валютных пар (рубль-доллар) сервис долго отвечает.

Как можно исправить проблему его медленной работы?

### 2. (5 мин)

Нужно сделать страницу котировок с он-лайн обновлением данных. Как бы ты ее сделал?

### 3. (5 мин)

Есть REST-сервис на Symfony, который обеспечивает взаимодействие вебсайт => внутренние банковские системы (вне сайта):

* оформление заявки на кредит
* открытие расчетного счета
* проверка номера телефона по СМС
* ...

Эта система морально устарела и содержит ошибки. Тебе поручили ее переделать.

Твой план действий?

### 4. (5 мин)

На сайте есть страница типа FAQ https://www.uralsib.ru/faq/personal/kreditnye-karty/kk-cashback

Фронтовая часть запрашивает содержимое страницы по REST API. Как это реализовать в терминах REST?

* Транспортный протокол
* Формат данных
* Метод
* Ресурс
* URI

### 5. (5 мин)

Ты знаком с микросервисной архитектурой? Как могут взаимодействовать МС между собой?

### 6. (5 мин)

Я ввел `curl -v https://uralsib.ru`. Из каких частей состоит и что рассказывает этот лог?  

```
*   Trying 193.109.114.7:443...
* TCP_NODELAY set
* Connected to uralsib.ru (193.109.114.7) port 443 (#0)
* ALPN, offering h2
* ALPN, offering http/1.1
* successfully set certificate verify locations:
*   CAfile: /etc/ssl/certs/ca-certificates.crt
    CApath: /etc/ssl/certs
* TLSv1.3 (OUT), TLS handshake, Client hello (1):
* TLSv1.3 (IN), TLS handshake, Server hello (2):
* TLSv1.2 (IN), TLS handshake, Certificate (11):
* TLSv1.2 (IN), TLS handshake, Server key exchange (12):
* TLSv1.2 (IN), TLS handshake, Server finished (14):
* TLSv1.2 (OUT), TLS handshake, Client key exchange (16):
* TLSv1.2 (OUT), TLS change cipher, Change cipher spec (1):
* TLSv1.2 (OUT), TLS handshake, Finished (20):
* TLSv1.2 (IN), TLS handshake, Finished (20):
* SSL connection using TLSv1.2 / ECDHE-RSA-AES128-GCM-SHA256
* ALPN, server did not agree to a protocol
* Server certificate:
*  subject: C=RU; ST=Republic of Bashkortostan; L=Ufa; O=Public joint stock company BANK URALSIB; CN=*.uralsib.ru
*  start date: Nov 30 00:00:00 2020 GMT
*  expire date: Dec 30 23:59:59 2021 GMT
*  subjectAltName: host "uralsib.ru" matched cert's "uralsib.ru"
*  issuer: C=US; O=DigiCert Inc; OU=www.digicert.com; CN=Thawte RSA CA 2018
*  SSL certificate verify ok.
> GET / HTTP/1.1
> Host: uralsib.ru
> User-Agent: curl/7.68.0
> Accept: */*
>
* Mark bundle as not supporting multiuse
  < HTTP/1.1 301 Moved Permanently
  < Date: Wed, 30 Jun 2021 23:48:30 GMT
  < Content-Type: text/html
  < Content-Length: 162
  < Connection: keep-alive
  < Location: https://www.uralsib.ru/
  < Strict-Transport-Security: max-age=31536000
  < Set-Cookie: TS01389dea=0131b76752acbab92584644c5fecf3d13477443d43908e93e4f7e1ebbee9f63e3a215e7eafd886699c239d3ca55b8b8ae988a2c6d5; Path=/; Domain=.uralsib.ru
  <
<html>
<head><title>301 Moved Permanently</title></head>
<body>
<center><h1>301 Moved Permanently</h1></center>
<hr><center>nginx</center>
</body>
</html>
* Connection #0 to host uralsib.ru left intact
```

## Базы данных (10 мин)

### 1. (5 мин)

* С какими базами данных ты работал? Какую базу ты бы рекомендовал использовать и почему?
* Как можно организовать поиск текстовой информации по БД?
* Сервер БД перегружен. Как можно выяснить причину нагрузки и что-то с этим сделать?

### 2. (5 мин)

Допустим, есть 2 банковских счета. Нужно перевести 200 рублей с первого счета на второй.  

```
mysql> select * from bank_account;
+----+----------+
| id | balance  |
+----+----------+
|  1 |   300.00 |
|  2 |   100.00 |
+----+----------+
```

Как это правильно сделать? Дай развернутый ответ. Если можешь, напиши в виде SQL запросов.

## Языки программирования (21 мин)

### 0. (5 мин)

Какие языки программирования ты знаешь, что в них нравится, а что нет? Какой самый лучший язык?

### 1. (3 мин)

Что такое Copy-on-Write, счетчик ссылок, и сборщик мусора?

### 2. (3 мин)

Ты знаком с методологией TDD? Какие виды тестов бывают? Есть ли опыт интеграции систем автотестирования в проект?
Какой подход следует применить во время тестирования кода, который имеет внешние зависимости (например, обращение к API Банка)?

### 3. (5 мин)

Зачем нужны шаблоны проектирования? Какие из них ты используешь?

### 4. (5 мин)

В запросе `$_GET['user_ids']` должна приходить строка с номерами пользователей через запятую, например: 1,2,17,48.

Оцени качество кода. Что бы ты исправил?

```php
<?php

function load_users_data($user_ids)
{
    $user_ids = explode(',', $user_ids);
    foreach ($user_ids as $user_id) {
        $db = mysqli_connect("localhost", "root", "123123", "database");
        $sql = mysqli_query($db, "SELECT * FROM users WHERE id=$user_id");
        while ($obj = $sql->fetch_object()) {
            $data[$user_id] = $obj->name;
        }
        mysqli_close($db);
    }
    return $data;
}

$data = load_users_data($_GET['user_ids']);
foreach ($data as $user_id => $name) {
    echo "<a href=\"/show_user.php?id=$user_id\">$name</a>";
}
```

## Laravel (15 мин)

### 1. (2 мин)

У нас есть микросервис авторизации. Нужно быстро посмотреть, сколько в нем сейчас пользователей. Как это сделать?

### 2. (3 мин)

Как в Laravel работают механизм событий и слушателей? В чем его удобство?

### 3. (5 мин)

В каких случаях нужно использовать механизм очередей? Как он работает в Laravel?

### 4. (5 мин)

Что такое Service Container и зачем он нужен? Зачем нужен Observer (наблюдатель)?

Поясни, что делает этот код:

```php
<?php

namespace App\Providers;

// use ...

class AppServiceProvider extends ServiceProvider
{
    public function boot()
    {
        $this->app->singleton(WorkingDirectoryInterface::class, function ($app) {
            return new WorkingDirectory();
        });

        $this->app->bind(RecordExporter::class, function ($app, $params) {
            $className = sprintf("\\App\\DataExchange\\Exporters\\%sRecordExporter", Str::studly($params["format"]));
            if (!class_exists($className)) abort(404, sprintf("No concrete class %s", $className));
            return new $className();
        });

        \App\Models\Table::observe([TableFilesObserver::class]);
    }
}
```

## Алгоритмы (15 мин)

### 1. (5 мин)

Какие виды индексов ты знаешь? В чем их отличия?

### 2. (5 мин)

Два города А и В находятся на расстоянии 300 км друг от друга. 

Одновременно из этих городов выезжают навстречу друг другу два велосипедиста и мчатся, не останавливаясь, со скоростью 50 километров в час каждый. 

Но вместе с первым велосипедистом из города А вылетает муха, пролетающая в час 100 км. Муха опережает первого велосипедиста, летит навстречу другому, выехавшему из В. 

Встретив этого, она тотчас поворачивает назад к велосипедисту А. Повстречав его, опять летит обратно навстречу велосипедисту В.

И так продолжала летать взад и вперёд до той поры, пока велосипедисты не съехались. Тогда она успокоилась и села одному из велосипедистов на шапку.

Сколько километров пролетела муха?

![Муха и велосипедисты](assets/muha.jpg)

### 3. (5 мин)

Что ты можешь рассказать про B-Tree?

## Инструменты, командная строка и Linux (11 мин)

### 1. (5 мин)

Какой командой узнать, где находится php?

Что делают следующие команды:

* chmod, chown
* curl, wget, nc
* ping, traceroute, dig, nslookup
* docker, docker-compose  
* strace
* nohup

### 2. (3 мин)

Ты нашел какой-то странный участок кода. Как понять, кто его написал и зачем?

Какие команды git ты используешь?

### 3. (3 мин)

Есть файл `srs.xml` с такой структурой

```xml
<?xml version="1.0" encoding="windows-1251"?>
<Offices>
    <BankOffice id="4">
        <Title>Операционный офис "Череповец" Филиала ПАО "БАНК УРАЛСИБ" в г.Санкт-Петербург</Title>
        <INN>0274062111</INN>
        <City>Череповец</City>
    </BankOffice>
    <BankOffice id="12">
        <Title>Отделение "Выборгское" Филиала ПАО "БАНК УРАЛСИБ" в г.Санкт-Петербург</Title>
        <INN>0274062111</INN>
        <City>Санкт-Петербург</City>
    </BankOffice>
</Offices>
```

Как быстро посчитать общее количество городов?

## Дополнительные вопросы

### (5 мин)

Ты ввел в строку браузера сайт uralsib.ru и нажал Enter. Расскажи о процессах, которые произойдут дальше.

### (5 мин)

У нас есть деление на фронт и бек. Ты разработал REST-сервис. Чтобы ты сделал для того, чтобы даже джун-фронтенд смог
начать с ним работать?

### (5 мин)

Для чего нужны шаблонизаторы и какие из них ты использовал?

### (5 мин)

Какие ORM ты использовал? Для чего они нужны?

### (1 мин)

В каком месте хранится список пользователей с их базовыми настройками?

### (5 мин)

Есть таблица заказов:

```
SELECT * FROM orders;
+----+--------+
| id | state  |
+----+--------+
|  1 | open   |
|  2 | close  |
|  3 | close  |
|  4 | active |
+----+--------+
```

Как отсортировать эти данные в порядке статусов `open`, `active`, `close`, то есть получить такие данные?

```
SELECT ...
+----+--------+
| id | state  |
+----+--------+
|  4 | active |
|  1 | open   |
|  2 | close  |
|  3 | close  |
+----+--------+
```

PS.

```sql
CREATE TABLE orders
(
    id    int unsigned auto_increment,
    state varchar(255) not null,
    primary key (id)
);
INSERT INTO orders VALUES (default, 'open');
INSERT INTO orders VALUES (default, 'close');
INSERT INTO orders VALUES (default, 'close');
INSERT INTO orders VALUES (default, 'active');
```