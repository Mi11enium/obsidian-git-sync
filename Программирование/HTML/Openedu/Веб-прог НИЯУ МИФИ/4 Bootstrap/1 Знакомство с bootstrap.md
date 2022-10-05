# Знакомство с bootstrap
> [!summary] Bootstrap
> это открытый и бесплатный HTML, CSS, и JS фреймворк, который используется веб-разработчиками для быстрой вёрстки адаптивных дизайнов сайтов и веб-приложений.

Основная область его применения это frontend разработка сайтов и интерфейсов панели администратора. Фреймворк bootstrap - это набор CSS и JS файлов. Чтобы его использовать, необходимо подключить файлы к странице.

https://getbootstrap.com/

## Установка
~~~html
```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Bootstrap demo</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-Zenh87qX5JnK2Jl0vWa8Ck2rdkQ2Bzep5IDxbcnCeuOxjzrPF/et3URy9Bv1WTRi" crossorigin="anonymous">
  </head>
  <body>
    <h1>Hello, world!</h1>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-OERcA2EqjJCMA+/3y+gxIOqMEjwtxJY7qPCqsdltbNJuaOe923+mo//f6V8Qbsw3" crossorigin="anonymous"></script>
  </body>
</html>
```
~~~

## Система сеток
![[Picture/web_s.png]]

## Способы подключения
01 - Extra small (xs)
02 - Small (s)
03 - Medium (md)
04 - Large (lg)
05 - Extra large (xl)
06 - Extra extra large (xxl)

![[web_size.png]]

## Компоненты bootstrap
https://getbootstrap.com/docs/5.2/customize/components/
Для размещения компонента достаточно вставить код компонента в необходимую область.
### Аккордеон
Аккордеон - это вертикальный сворачивающийся список.