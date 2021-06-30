### 5.

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
```

Что выведет запрос `SELECT AVG(val) FROM data`?

### 6.

Какие строки НЕ содержат ошибки?

```
/* 1 */ $a = 42;
/* 2 */ $b = &$a;
/* 3 */ $70a = 70 * $a;
/* 4 */ $a0 = ${"a"} + 0;
```

### 7.

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

### 8.

Каким будет результат выполнения кода?

```php
function foo(&$r)
{ 
    $r++;
}

$r = 1;
foo(foo(&$r));

echo $r;
```

### 9.

Каким будет результат выполнения кода?

```php
interface Foo {
    const A = 'Foo';
}

class Bar implements Foo {
    const A = 'Bar';
}

echo Bar::A;
```

* Foo
* Bar
* Сообщение об ошибке, интерфейс не может содержать константы
* Сообщение об ошибке, класс не может перекрывать константы интерфейса

### 3.

Есть 2 таблицы:

```
mysql> SELECT * FROM t_1;
+------+
| val  |
+------+
|    1 |
|    2 |
|   10 |
+------+
3 rows in set (0.00 sec)

mysql> SELECT * FROM t_2;
+------+
| val  |
+------+
|    1 |
|    2 |
+------+
2 rows in set (0.00 sec)
```

Как найти строки из таблицы `t_1`, которых нет в таблице `t_2`?

### 4.

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