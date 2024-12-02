# 12-03-hw
Домашнее задание к занятию «SQL. Часть 1»  Семиошко Андрей

### Задание 1

Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.

### Решение 1

```sql
SELECT DISTINCT district
FROM sakila.address
WHERE district like 'K%a'
      and POSITION(' ' IN district) = 0;
```

### Задание 2

Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года **включительно** и стоимость которых превышает 10.00.

### Решение 2

```sql
SELECT *
FROM sakila.payment
WHERE Date(payment_date) between '2005-06-15' and '2005-06-18'
		and amount > 10.0;
```
### Задание 3

Получите последние пять аренд фильмов.

### Решение 3

```sql
SELECT *
FROM sakila.rental
ORDER BY rental_id DESC
LIMIT 5;
```
### Задание 4

Одним запросом получите активных покупателей, имена которых Kelly или Willie. 

Сформируйте вывод в результат таким образом:
- все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,
- замените буквы 'll' в именах на 'pp'.

### Решение 4

```sql
SELECT REPLACE(LOWER(first_name), 'll', 'pp'), LOWER(last_name), active
FROM sakila.customer
WHERE first_name IN ('Kelly', 'Willie') and active = 1;
```
