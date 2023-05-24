SQL — язык структурированных запросов (SQL, Structured Query Language), который используется в качестве эффективного способа сохранения данных, поиска их частей, обновления, извлечения и удаления из базы данных.

Если в запросе нет FROM, то после ключевого слов (INSERT INTO) идет название таблицы и в скобках название столбц(а, ов).

# Последовательность команд в запросе
SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY

# Типы данных атрибутов
<mark style="background: #FFB86CA6;">DESCRIBE</mark> table_name;

ИЛИ

<mark style="background: #FFB86CA6;">PRAGMA Table_info</mark> (table_name); // SQLite

ИЛИ же посмотреть на ERD-диаграмму схемы базы данных:

![[Pasted image 20230515221624.png]]

# Работа с данными
## Просмотр таблицы (SELECT)
<mark style="background: #FFB86CA6;">SELECT * FROM</mark> table_name;

ИЛИ

<mark style="background: #FFB86CA6;">SELECT</mark> atr_name, atr2_name <mark style="background: #FFB86CA6;">FROM</mark> table_name;

## Представление (AS)
SELECT <mark style="background: #FFB86CA6;">Author AS Автор, Books_title AS Название</mark> FROM Books;

ИЛИ Как представление вычесления

SELECT <mark style="background: #FFB86CA6;">Price * Amount AS Total FROM</mark> Books;

ИЛИ Как представление вычесления с функцией

SELECT <mark style="background: #FFB86CA6;">IIF</mark> (Amount<200, Round(Price\*0.5, 2), Round(Price\*0.8, 2)) AS Sale FROM Books

## Фильтр (WHERE)
SELECT Author, Book, Publisher, Amount, Price
FROM Books
<mark style="background: #FFB86CA6;">WHERE</mark> Amount < 40 <mark style="background: #FFB86CA6;">AND</mark> PRICE > 100;

SELECT Author, Book, Publisher, Amount, Price
FROM Books
<mark style="background: #FFB86CA6;">WHERE</mark> Amount < 40 <mark style="background: #FFB86CA6;">OR</mark> PRICE > 100;

### IS NULL, BETWEEN, IN, \[NOT\] LIKE, ESCAPE
ИЛИ с диапазоном (между)

SELECT Author, Book, Publisher, Amount, Price
FROM Books
<mark style="background: #FFB86CA6;">WHERE</mark> Amount <mark style="background: #FFB86CA6;">BETWEEN</mark> 1 AND 40;

ИЛИ по индексу (содержит)

SELECT Author, Book, Publisher, Amount, Price
FROM Books
<mark style="background: #FFB86CA6;">WHERE</mark> Price <mark style="background: #FFB86CA6;">IN(40, 113, 450)</mark> 

Или по пустым ячейкам (NULL)
SELECT Author, Book, Publisher, Amount, Price
FROM Books
<mark style="background: #FFB86CA6;">WHERE</mark> Price <mark style="background: #FFB86CA6;">IS NULL</mark> 

ИЛИ соответствует шаблону (LIKE)

SELECT Author, Book, Publisher, Amount, Price
FROM Books
<mark style="background: #FFB86CA6;">WHERE</mark> Price <mark style="background: #FFB86CA6;">LIKE</mark> '\%@mail.ru';

ИЛИ содержит экранирующий символ (ESCAPE)

SELECT Author, Book, Publisher, Amount, Price
FROM Books
<mark style="background: #FFB86CA6;">WHERE</mark> Price LIKE '5<mark style="background: #FFB86CA6;">!</mark> %'' <mark style="background: #FFB86CA6;">ESCAPE '!'</mark> ;

## Группировка (GROUP BY)

SELECT home_type
FROM Rooms
<mark style="background: #FFB86CA6;">GROUP BY</mark> home_type

При использовании GROUP BY мы можем выводить только:
1. литералы
2. результаты агрегатных функций
3. поля группировки
Следует иметь в виду, что для GROUP BY все значения NULL трактуются как равные, т.е. при группировке по полю, содержащему NULL-значения, все такие строки попадут в одну группу

## Агрегатные функции
Агрегатная функция – это функция, которая выполняет вычисление на наборе значений и возвращает одиночное значение.

SELECT \[литералы, <mark style="background: #FFB86CA6;">агрегатные_функции</mark> , поля_группировки]
FROM имя_таблицы
GROUP BY поля_группировки;

| Функция           | Описание                         |
| ----------------- | -------------------------------- |
| SUM(table_name)   | Возвращает сумму значений        |
| AVG(table_name)   | Возвращает среднее значение      |
| COUNT(table_name) | Возвращает количество записей    |
| MIN(table_name)   | Возвращает минимальное значение  |
| MAX(table_name)   | Возвращает максимальное значение |

Агрегатные функции применяются для значений, не равных NULL. Исключением является функция COUNT(\*).

## Фильтрация сгрупированных данных (HAVING)
HAVING используется для фильтрации результатов агрегатных функций после группировки данных.

SELECT home_type
FROM Rooms
<mark style="background: #FFB86CA6;">GROUP BY</mark> home_type
<mark style="background: #FFB86CA6;">HAVING</mark> cost < 10000;

Порядок выполнения операций, при использовании HAVING
SELECT [константы, агрегатные_функции, поля_группировки] // 5
FROM имя_таблицы // 1
WHERE условия_на_ограничения_строк // 2
GROUP BY поля_группировки // 3
HAVING условие_на_ограничение_строк_после_группировки // 4
ORDER BY условие_сортировки // 6

## Сортировка (ORDER BY)
SELECT Author, Book, Publisher, Amount, Price
FROM Books
WHERE Price IN(1, 115, 450)
<mark style="background: #FFB86CA6;">ORDER BY</mark> Amount;

Или по убыванию

SELECT Author, Book, Publisher, Amount, Price
FROM Books
WHERE Price IN(1, 115, 450)
<mark style="background: #FFB86CA6;">ORDER BY</mark> Amount <mark style="background: #FFB86CA6;">DESC</mark> ;

## Ограничение (LIMIT)
SELECT name
FROM books
<mark style="background: #FFB86CA6;">LIMIT 2, 3</mark> // на какой строке встать, сколько строк после вывести, не включая ту, на которую встали?

## Подзапросы
Подзапрос — это запрос, использующийся в другом SQL запросе. Подзапрос всегда заключён в круглые скобки и обычно выполняется перед основным запросом.
### Подзапрос с одной строкой с одним столбцом (скалярный подзапрос)

SELECT
(<mark style="background: #FFB86CA6;">SELECT name FROM company LIMIT 1</mark> )
AS company name;

Или для фильтрации строк с помощью WHERE

SELECT \*
FROM FamilyMembers
<mark style="background: #FFB86CA6;">WHERE</mark> birthday =
(<mark style="background: #FFB86CA6;">SELECT MAX(birthday) FROM FamilyMembers</mark> );

При использовании результата подзапроса с операторами сравнения, как в нашем примере, важно, чтобы подзапрос возвращал именно скалярное значение (1 строка и 1 колонка).





## Добавление значения (INSERT INTO)

Добавлять данные (значения) в таблицу мы можем только если мы знаем её структуру и порядок атрибутов.
Если атрибут внешний, то мы должны знать ID этого атрибута.

Шаблон добавления:
<mark style="background: #FFB86CA6;">INSERT INTO</mark> Table_name
<mark style="background: #FFB86CA6;">VALUES</mark> (empty_value, col2_value...),
    (empty1_value, col2_value...);

ИЛИ

<mark style="background: #FFB86CA6;">INSERT INTO</mark> Table_name (atr_name, atr_name2)
<mark style="background: #FFB86CA6;">VALUES</mark> (value_atr_name, value_atr_name2...),
    (empty1_value, col2_value...);

## Обновление значения (UPDATE)

<mark style="background: #FFB86CA6;">UPDATE</mark> имя_таблицы
<mark style="background: #FFB86CA6;">SET</mark> столбец1 = новое_значение1, столбец2 = новое_значение2, ..., столбецN = новое_значениеN
<mark style="background: #FFB86CA6;">WHERE</mark> условие;

## Удаление значения (DELETE)
<mark style="background: #FFB86CA6;">DELETE FROM</mark> table_name
<mark style="background: #FFB86CA6;">WHERE</mark> ID = 4;







# Отдельные замечания:
## Поиск строк с одинаковым значением(GROUP BY и HAVING)
SELECT
FROM
<mark style="background: #FFB86CA6;">GROUP BY</mark> name
<mark style="background: #FFB86CA6;">HAVING COUNT(*) > 0</mark> ;

## Вывод самого длинного имени
SELECT name 
FROM passenger 
<mark style="background: #FFB86CA6;">WHERE LENGTH(name) = (SELECT MAX(LENGTH(name)) FROM passenger);</mark> 