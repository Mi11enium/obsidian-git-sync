# HTTP
> [!summary] HTTP
> Hyper Text Transfer Protocol - клиент- серверный протокол передачи гипертекстовой разметки, обмен сообщениями идёт по схеме "запрос-ответ" в виде ASCII-команд.

![[HTTPR.png]]

## HTTP Methods
В URL не отображается только тип выполняемого REST- запроса - они известны как HTTP глаголы и их легко понять.

<mark style="background: #ADCCFFA6;">C</mark> --> Create --> <mark style="background: #ADCCFFA6;">POST</mark>  - Создает запись в БД
<mark style="background: #ADCCFFA6;">R</mark> --> Read --> <mark style="background: #ADCCFFA6;">GET</mark>  - Получает запись из БД
<mark style="background: #ADCCFFA6;">U</mark> --> Update --> <mark style="background: #ADCCFFA6;">PUT</mark> - Берет запись из базы и заменяет её новой
<mark style="background: #ADCCFFA6;">D</mark> --> Delete --> <mark style="background: #ADCCFFA6;">DELETE</mark> - Удаляет запись из БД
P --> Change --> PATCH - Меняет существующую запись в БД

## Коды состояния ответа HTTP
После отправки запроса сервер возвращает ответ. Ответы от сервера содержат коды состояния для обращения к клиенту об успехе операции.

1xx - Informational
2xx - Success
3xx - Redirection
4xx - Client Error
5xx - Server Error

![[HTTPStatus.png]]