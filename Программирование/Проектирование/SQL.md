SQL — язык структурированных запросов (SQL, Structured Query Language), который используется в качестве эффективного способа сохранения данных, поиска их частей, обновления, извлечения и удаления из базы данных.

Если в запросе нет FROM, то после ключевого слов (INSERT INTO) идет название таблицы и в скобках название столбц(а, ов).

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

SELECT IIF(Amount<200, Round(Price\*0.5, 2), Round(Price\*0.8, 2)) AS Sale FROM Books

## Фильтр (WHERE)
SELECT Author, Book, Publisher, Amount, Price
FROM Books
WHERE Amount < 40 AND PRICE > 100;

ИЛИ с диапазоном (между)

SELECT Author, Book, Publisher, Amount, Price
FROM Books
WHERE Amount BETWEEN 1 AND 40;

ИЛИ по индексу (содержит)

SELECT Author, Book, Publisher, Amount, Price
FROM Books
WHERE Price IN(40, 113, 450)

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

## Представление по шаблону (LIKE)
SELECT Author, Book, Publisher, Amount, Price
FROM Books
<mark style="background: #FFB86CA6;">WHERE</mark> Book <mark style="background: #FFB86CA6;">LIKE ("%и")</mark> ; // процент - это метасимвол от 0 до бесконечности

ИЛИ

SELECT Author, Book, Publisher, Amount, Price
FROM Books
<mark style="background: #FFB86CA6;">WHERE</mark> Book <mark style="background: #FFB86CA6;">LIKE("__с%")</mark> ; // \_ - один любой символ
# Работа с таблицами
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

