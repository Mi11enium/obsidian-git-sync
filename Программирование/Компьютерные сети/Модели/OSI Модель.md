# Что такое модель OSI?

Модель Open Systems Interconnection (OSI) - это концептуальная модель, созданная Международной организацией по стандартизации, которая позволяет различным системам связи взаимодействовать с использованием стандартных протоколов. Говоря простым языком, OSI предоставляет стандарт для различных компьютерных систем, позволяющий взаимодействовать друг с другом.

Модель OSI можно рассматривать как универсальный язык для компьютерных сетей. Он основан на концепции разделения коммуникационной системы на семь абстрактных уровней, каждый из которых накладывается на предыдущий. Каждый уровень модели OSI выполняет определенную работу и взаимодействует с уровнями выше и ниже себя.

OSI означает "Взаимодействие открытых систем". Эта модель была разработана ISO – **Международной организацией по стандартизации**, в 1984 году. Это 7-уровневая архитектура, каждый уровень которой обладает определенной функциональностью. Все эти 7 уровней работают совместно для передачи данных от одного человека к другому по всему миру.
***
## Характеристики модели OSI

- Модель OSI разделена на две группы уровней: верхние уровни и нижние уровни.  
- Верхний уровень модели OSI в основном занимается вопросами, связанными с приложениями, они реализованы только в программном обеспечении. Прикладной уровень находится ближе всего к конечному пользователю. Конечный пользователь и прикладной уровень взаимодействуют с программным обеспечением. Верхний уровень относится к уровню, расположенному непосредственно над другим уровнем.  
- Нижний уровень модели OSI имеет дело с вопросами передачи данных. Канальный уровень передачи данных и физический уровень реализованы в аппаратном и программном обеспечении. Физический уровень является самым низким уровнем модели OSI и находится ближе всего к физической среде. Физический уровень в основном отвечает за размещение информации на физическом носителе.
***
### Уровни OSI

Существует 7 уровней модели OSI:

- физический (Physical layer)  
- канальный (Data-Link layer)  
- сетевой (Network layer)  
- транспортный (Transport layer)  
- сессионный (Session layer)  
- представления (Presentation layer)  
- прикладной (Application layer)
***
### Физический уровень (Physical layer)

Физический уровень координирует функции, необходимые для передачи  
битового потока данных по физическому носителю.
***
### Канальный уровень (Data-Link layer)

Уровень канала передачи данных преобразует физическую связь в реальную и  
отвечает за доставку от одного узла(node) к другому.
***
### Сетевой уровень (Network layer)

Сетевой уровень отвечает за доставку пакета от источника к получателю по нескольким каналам связи.
***
### Транспортный уровень (Transport layer)

Транспортный уровень отвечает за доставку сообщения от источника к месту назначения.
***
### Сеансовый уровень (Session layer)

Сеансовый уровень устанавливает, поддерживает и синхронизирует  
взаимодействие между системами.
***
### Уровень представления (Presentation layer)

Основная функция уровня представления заключается в определении формата и шифровании данных.
***
### Прикладной уровень (Application layer)

Прикладной уровень позволяет пользователю получать доступ к сети, а также предоставляет пользовательские  
интерфейсы и поддержку таких служб, как электронная почта, удаленный доступ к файлам, управление базами данных и т.д.

![[V5GzaL9IkiA.jpg]]