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