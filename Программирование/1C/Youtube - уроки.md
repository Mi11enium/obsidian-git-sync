# Модуль
Модуль - это <mark style="background: #FFF3A3A6;">место, где мы пишем код</mark>.
Есть модуль у объектов, модуль у формы и т.д.

Структура модуля:
// Раздел объявления переменных

// Тело модуля

// Раздел инициализации переменных

# Переменные
- Названия переменных должны быть осмысленным.
- Переменные имеют стиль PascalCase
- Начальное значение переменной (в случае числового типа данных), мы должны указывать в блоке "Раздел инициализации переменных".

## Глобальные переменные
Основное свойство глобальной переменной в том, что к ней можно обращаться из любого обработчика (процедуры, функции) данного модуля.

## Локальные переменные
Локальные переменные объявляются в теле обработчика (процедуры, функции). 

Мы можем объявить имя локальной переменной такое же как и глобальной, но при этом у нас не будет доступа к глобальной переменной, а локальная будет доступна только в теле обработчика. Значение глобальной переменной при этом не изменится и его можно использовать в любом месте модуля.

Для переменных обычно не используется ключевое слово "Перем", а сразу описывается имя переменной и присваивается к ней значение.

Глобальные переменные указываются с префиксом "м", локальные переменные указываются без префикса:

Глобальная: мСтат = 0;
Локальная: Стат = 0;
### Способы объявления локальных переменных
Информация о типе переменной заносится в момент присваивания этой переменной какого-либо значения.

Переменная подстраивает свой тип под то значение, которое мы в неё заносим.
# Общие правила
- Для каждого элемента должен быть написан свой обработчик - нельзя прикреплять несколько элементов (например кнопок) к одному обработчику.

- CTRL + SPACE вызывает контекстную подсказку в модуле.
# Условные операторы
Реквизиты объекта - это данные объекта.
После создания реквизита, необходимо сразу же определить тип.

Синтаксис:
~~~pascal
	Если {Условие} Тогда
		{Оператор};
	ИначеЕсли {Условие2} Тогда // не обязательно
		{Оператор2} // не обязательно
	Иначе // не обязательно
		{Оператор3} // не обязательно
	КонецЕсли;
~~~

# Summary
Модуль - это <mark style="background: #FFF3A3A6;">место, где мы пишем код</mark>.
Обработчик - это тело модуля (процедура или функция)


# Управляемое приложение
В управляемом приложении, в форме, <mark style="background: #BBFABBA6;">для размещения элементов горизонтально</mark> , необходимо создать обычную группу и поместить туда реквизиты.

![[Pasted image 20230412220331.png]]
***
<mark style="background: #BBFABBA6;">Для создания кнопки</mark> необходимо создать соответствующую комманду.
Чтобы создать обработчик для комманды, необходимо в свойстве "Действие" нажать кнопку с лупой и в появившемся окне выбрать:
- Создать на клиенте (если входные данные есть в нашей форме)
- Создать на клиенте и процедуру на сервере без контекста (если считываем входные данные из БД)
- Создать на клиенте и процедуру на сервере (если считываем входные данные из БД)

![[Pasted image 20230412220747.png]]
***
В отличие от обычной формы, <mark style="background: #BBFABBA6;">в управляемой конфигурации обращение к реквизитам идет через объект "Объект.Реквизит" </mark> 

![[Pasted image 20230412221943.png]]
***
<mark style="background: #BBFABBA6;">Для того чтобы кнопка появилась на форме</mark> , нужно команду перетащить на форму

![[Pasted image 20230412222340.png]]
***
Для того, <mark style="background: #BBFABBA6;">чтобы сделать кнопку желтой</mark> , в свойстве кнопки ставим галочку "КнопкаПоУмолчанию"
***

# Процедуры и функции
Отличие функции от процедуры в том, что <mark style="background: #BBFABBA6;">функция всегда возвращает значение</mark> .

Синтаксис функции:
~~~pascal
Функция ИмяФункции(арг1, арг2)
	// Тело функциии
	// Возврат арг1; или Возврат арг2;
КонецФункции
~~~

Синтаксис процедуры:
~~~pascal
Функция ИмяПроцедуры()
	// Тело процедуры
	// Возврат арг1; или Возврат арг2;
КонецПроцедуры
~~~
