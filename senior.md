# Вопросы для собеседования senior

## Общее (10 мин)

* Какую роль ты выполнял в последнем проекте? Что делала остальная команда? Что нравится или не нравится на этом месте?
* Расскажите о сложностях в работе над проектом. Как их решали?
* Есть ли собственный проект? Что в нем интересного?
* Что тебя мотивирует в работе? А что демотивирует?

## Архитектурные вопросы (30 мин)

### (5 мин)

Для разминки: с какими терминами ты знаком, и пара слов о них.

* KISS, DRY, YAGNI, SOLID
* TDD, BDD
* DDD
* CRUD, ACID
* ORM, ODM
* MVC, MVVM

### (5 мин)

Есть микросервис "курс валют". При получении валютных пар (рубль-доллар) сервис долго отвечает.

Как можно исправить проблему его медленной работы?

https://speed24.ru/q/callgraph-before.png

```
# Rank Query ID           Response time Calls R/Call  V/M   Item
# ==== ================== ============= ===== ======= ===== ==============
#    1 0x93CFB226660D35EA 50.0813 76.3%     1 50.0813  0.00 UPDATE b_sale_product?product b_sale_basket
#    2 0xB40B7BB93898D8B5 11.3354 17.3%     1 11.3354  0.00 INSERT SELECT b_sale_product?product b_sale_basket b_sale_product?product
#    3 0x5D460ECCCA8798B9  2.2000  3.4%     1  2.2000  0.00 SELECT b_iblock b_lang b_iblock_element
# MISC 0xMISC              1.9989  3.0%    28  0.0714   0.0 <24 ITEMS>


UPDATE b_sale_product2product p2p, b_sale_basket b, b_sale_basket b1
        SET  p2p.CNT = p2p.CNT + 1
        WHERE b.ORDER_ID = b1.ORDER_ID AND
          b.ID <> b1.ID AND
          b.ORDER_ID = 36057 AND
          p2p.PRODUCT_ID = b.PRODUCT_ID AND
          p2p.PARENT_PRODUCT_ID = b1.PRODUCT_ID\G
```

### (5 мин)

https://speed24.ru/q/ms-groups.jpg

Есть два микросервиса, каждый со своей базой данных. Есть понятие группа пользователей. Нужно синхронизировать
группы пользователей первого МС со вторым МС. Как бы ты это сделал?

### (5 мин)

Есть REST-сервис на Symfony, который обеспечивает взаимодействие вебсайт => внутренние банковские системы (вне сайта):

* оформление заявки на кредит
* открытие расчетного счета
* проверка номера телефона по СМС
* ...

Эта система морально устарела и содержит ошибки. Тебе поручили ее переделать.

Твой план действий?

### (5 мин)

Я ввел `telnet www.baidu.com 80` и получил такой ответ. Из каких частей он состоит и что рассказывает?

https://speed24.ru/q/sh_0573.png

```
$ telnet www.baidu.com 80
Trying 103.235.46.39...
Connected to www.wshifen.com.
Escape character is '^]'.
GET / HTTP/1.1
Host: www.baidu.com
User-Agent: hacker
Accept: */*

HTTP/1.1 200 OK
Bdpagetype: 1
Bdqid: 0xd1090c79000012b0
Cache-Control: private
Connection: keep-alive
Content-Type: text/html;charset=utf-8
Date: Mon, 02 Aug 2021 06:07:26 GMT
Expires: Mon, 02 Aug 2021 06:06:48 GMT
P3p: CP=" OTI DSP COR IVA OUR IND COM "
P3p: CP=" OTI DSP COR IVA OUR IND COM "
Server: BWS/1.1
Set-Cookie: BAIDUID=6A487A8AA2C26ADC6466ECC89FD2E35B:FG=1; expires=Thu, 31-Dec-37 23:55:55 GMT; max-age=2147483647; path=/; domain=.baidu.com
Set-Cookie: BIDUPSID=6A487A8AA2C26ADC6466ECC89FD2E35B; expires=Thu, 31-Dec-37 23:55:55 GMT; max-age=2147483647; path=/; domain=.baidu.com
Set-Cookie: PSTM=1627884446; expires=Thu, 31-Dec-37 23:55:55 GMT; max-age=2147483647; path=/; domain=.baidu.com
Set-Cookie: BAIDUID=6A487A8AA2C26ADCDD74E46EB04767A2:FG=1; max-age=31536000; expires=Tue, 02-Aug-22 06:07:26 GMT; domain=.baidu.com; path=/; version=1; comment=bd
Set-Cookie: BDSVRTM=0; path=/
Set-Cookie: BD_HOME=1; path=/
Set-Cookie: H_PS_PSSID=34300_34099_33969_34334_34370_34144_34375_34004_34092_34111_26350_34242; path=/; domain=.baidu.com
Traceid: 1627884446046251853815062584142547915440
Vary: Accept-Encoding
Vary: Accept-Encoding
X-Frame-Options: sameorigin
X-Ua-Compatible: IE=Edge,chrome=1
Transfer-Encoding: chunked

b10
<!DOCTYPE html><!--STATUS OK-->


    <html><head><meta http-equiv="Content-Type" content="text/html;charset=utf-8"><meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"><meta content="always" name="referrer"><meta name="theme-color" content="#2932e1"><meta name="description" content="全球领先的中文搜索引擎、致力于让网民更便捷地获取信息，找到所求。百度超过
```

### 5. (5 мин)

https://speed24.ru/q/openssl.txt

Я ввел `openssl s_client -connect uralsib.ru:443` и получил такой ответ. Из каких частей он состоит и что рассказывает?

## Базы данных (10 мин)

### (5 мин)

* Зачем нужны индексы? Какие типы индексов ты знаешь?
* Как можно организовать поиск сайту?
* Сервер БД перегружен. Как можно выяснить причину нагрузки и что-то с этим сделать?

### (2 мин)

https://speed24.ru/q/sh_0606.png

В базе есть такие данные:

```
SELECT * FROM data;
+------+
| val  |
+------+
|    0 |
|    1 |
|    2 |
| NULL |
+------+

SELECT AVG(val) FROM data;

???
```

Что выведет запрос `SELECT AVG(val) FROM data`?

### (5 мин)

https://speed24.ru/q/sh_0605.png

Есть 2 таблицы:

```
mysql> select  * from t_1;
+------+
| val  |
+------+
|    1 |
|    2 |
|   10 |
+------+
3 rows in set (0.00 sec)

mysql> select  * from t_2;
+------+
| val  |
+------+
|    1 |
|    2 |
+------+
2 rows in set (0.00 sec)

```

Как найти строки из таблицы t_1, отсутствующие в таблице t_2?

### (5 мин)

Допустим, есть 2 банковских счета. Нужно перевести 200 рублей с первого счета на второй.

https://speed24.ru/q/sh_0580.png

```
mysql> select * from bank_account;
+----+----------+
| id | balance  |
+----+----------+
|  1 |   300.00 |
|  2 |   100.00 |
+----+----------+
```

Как это правильно сделать? Если можешь, напиши в виде SQL запросов.

## Языки программирования (21 мин)

### (5 мин)

Что тебе нравится, а что нет в PHP? Что бы ты добавил в язык?

###  (3 мин)

https://speed24.ru/q/sh_0604.png

Какой результат выполнения следующего кода?

```php
class Foo {
    public static function getClassName()
    {
        return __CLASS__;
    } 
}

class Bar extends Foo { }

echo Bar::getClassName();
```

А как сделать, чтобы вывелось `Bar`?

### (3 мин)

Что такое Copy-on-Write, счетчик ссылок, и сборщик мусора?

### (3 мин)

* Ты знаком с методологией TDD?
* Есть ли опыт интеграции систем автотестирования в проект?

Допустим, есть класс, который получает заявку на кредит и отправляет данные во внешнюю Банковскую систему.
Нам не хочется слать тестовые данные в эту систему, но нам нужно протестировать логику этого класса.
Как это можно сделать?

### (5 мин)

Зачем нужны шаблоны проектирования? Какие из них ты используешь?

### (5 мин)

Недавно мне потребовалось вывести ссылки на профили пользователей. Я загуглил и нашел такой ответ на StackOverflow.

Что ты можешь сказать про этот код?

https://speed24.ru/q/sh_0575.png

Вам нужно получить данные по каждому пользователю, и затем показать результаты на странице. Как-то так:

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

У нас есть микросервис авторизации. Нужно быстро посмотреть общее количество пользователей в базе. Как это сделать?

### 2. (3 мин)

Как в Laravel работают механизм событий и слушателей? В чем его удобство?

### 3. (5 мин)

В каких случаях нужно использовать механизм очередей? Как он работает в Laravel?

### 4. (5 мин)

Что такое Service Container и зачем он нужен?

Поясни, что делает этот код:

https://speed24.ru/q/sh_0577.png

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

https://speed24.ru/q/muha.jpg

![Муха и велосипедисты](assets/muha.jpg)

## Инструменты, командная строка и Linux (11 мин)

### 1. (5 мин)

Какой командой узнать, где находится php?

Что делают следующие команды:

* chmod, chown
* curl, wget, telnet
* ping, traceroute, dig, nslookup
* docker, docker-compose

### 2. (3 мин)

Ты нашел какой-то странный участок кода. Как понять, кто его написал и зачем?

Какие команды git ты используешь?

### 3. (3 мин)

Объясни, что делает эта команда:

https://speed24.ru/q/sh_0607.png

```bash
docker run -it --rm `docker-compose build laravel-app | awk '/Successfully tagged/{ print $3 }'` sh -c 'composer test'
```

### 4. (3 мин)

Есть файл `srs.xml` с такой структурой

https://speed24.ru/q/sh_0578.png

```xml
<?xml version="1.0" encoding="windows-1251"?>
<Offices>
    <BankOffice id="4">
        <Title>Операционный офис "Череповец" Филиала ПАО "БАНК УРАЛСИБ"</Title>
        <INN>0274062111</INN>
        <City>Череповец</City>
    </BankOffice>
    <BankOffice id="12">
        <Title>Отделение "Выборгское" Филиала ПАО "БАНК УРАЛСИБ"</Title>
        <INN>0274062111</INN>
        <City>Санкт-Петербург</City>
    </BankOffice>
</Offices>
```

Как быстро посчитать общее количество городов?

