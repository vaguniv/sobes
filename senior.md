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
* OLAP

### 1. (5 мин)

Есть микросервис "курс валют". При получении валютных пар (рубль-доллар) сервис долго отвечает.

Как можно исправить проблему его медленной работы?

### 2. (5 мин)

Есть микросервис управления пользователями и авторизации. В нем все пользователи привязаны к группам. 
Также есть микросервис коротких ссылок, имеющий свою базу данных. При создании короткой ссылки, передается группа,
чтобы привязать к ней ссылку, и пользователи этой же группы имели возможность видеть эту ссылку.
Нужно синхронизировать группы этих микросервисов. Как бы ты это сделал?

### 3. (5 мин)

Есть REST-сервис на Symfony, который обеспечивает взаимодействие вебсайт => внутренние банковские системы (вне сайта):

* оформление заявки на кредит
* открытие расчетного счета
* проверка номера телефона по СМС
* ...

Эта система морально устарела и содержит ошибки. Тебе поручили ее переделать.

Твой план действий?

### 4. (5 мин)

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

## Базы данных (10 мин)

### 1. (5 мин)

* Зачем нужны индексы? Какие типы индексов ты знаешь?
* Как можно организовать поиск сайту?
* Сервер БД перегружен. Как можно выяснить причину нагрузки и что-то с этим сделать?

### 2. (5 мин)

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

Как это правильно сделать? Дай развернутый ответ. Если можешь, напиши в виде SQL запросов.

## Языки программирования (21 мин)

### 0. (5 мин)

Что тебе нравится, а что нет в PHP? Что бы ты добавил в язык?

### 1. (3 мин)

Что такое Copy-on-Write, счетчик ссылок, и сборщик мусора?

### 2. (3 мин)

Ты знаком с методологией TDD? Какие виды тестов бывают? Есть ли опыт интеграции систем автотестирования в проект?
Какой подход следует применить во время тестирования кода, который имеет внешние зависимости (например, обращение к API Банка)?

### 3. (5 мин)

Зачем нужны шаблоны проектирования? Какие из них ты используешь?

### 4. (5 мин)

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

Что такое Service Container и зачем он нужен? Зачем нужен Observer (наблюдатель)?

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
* curl, wget, nc
* ping, traceroute, dig, nslookup
* docker, docker-compose  
* strace
* nohup

### 2. (3 мин)

Ты нашел какой-то странный участок кода. Как понять, кто его написал и зачем?

Какие команды git ты используешь?

### 3. (3 мин)

Объясни, что делает эта команда:

https://speed24.ru/q/sh_0579.png

```bash
docker run -it --rm `docker-compose build laravel-app | awk '/Successfully tagged/{ print $$3 }'` sh -c 'composer test'
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

