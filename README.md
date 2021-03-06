# DeviceFirmwareTemplate
Шаблон проекта прошивки для более прозрачной, структурированной и предсказуемой разработки

Это шаблон для проектов прошивок в IAR, в оригинале не предназначен для
прошивки. В зависимости от области применения устройства некоторые уровни могут
отсутствовать. Разработка ведется снизу вверх. В зависимости от устройства раз-
ные уровни могут занять различное время разработки.

1.	UX/UI: представление информации пользователю и прием информации.
	Уровень любого взаимодействия с пользователем и вербальной передачи
	информации. Описывает организацию графики на экране, издаваемые устройством
	звуки, поведение индикаторов, активные области сенсорных панелей, мультитач-
	зум изображений. Уровень пользовательского интерфейса. Автономные устройства
	могут не иметь этот уровень.

2.	Functions: реализует функционал устройства с точки зрения пользователя.
	Реагирует на сигналы полученные через уровень пользовательского интерфейса,
	придает значение действиям пользователя, является источником данных для вы-
	вода их через верхний уровень. Содержит всю логику функционирования устройс-
	тва, математику обработки принимаемых и отправляемых данных. Может быть са-
	мым сложным уровнем в разработке. Устройства прямого вывода данных могут не
	иметь этот уровень.

3.	System/OS: реализует многозадачность, планировщик, файловый менеджер и т.д.
	Распределяет вычислительные ресурсы между задачами, создает/удаляет задачи,
	планирует события, позволяет создавать цепочки событий. Обеспечивает целост-
	ную работу сложного устройства. Однозадачные или простые устройства могут не
	иметь этот уровень.

4.	Middleware: предоставляет высокоуровневые библиотеки частей ОС/системы.
	Включает в себя стеки протоколов, библиотеки графического интерфейса, фай-
	ловых систем и т.д. Не требующие стороних библиотек устройства могут не
	иметь этот уровень.
	
5.	Board: содержит драйвера управления компонентами на плате с помощью CPU.
	Драйвера дисплеев, датчиков, ПЗУ, ОЗУ, аудиокодеков, и др. электронных уст-
	ройств размещенных на плате и подключенных к CPU. Не имеющие подключенных к
	CPU электронных компонентов устройства могут не иметь этот уровень.
	
6.	Peripheral: универсальные драйвера встроенной периферии CPU.
	Драйвера удобного управления периферией CPU для взаимодействия HAL и уровня
	поддержки компонентов платы (BSP). Представляет гибкий API для чтения/записи
	и управления периферией CPU (SPI, DMA, I2C, UART, Timers...). Возможно пот-
	ребуется замена при портировании. Очень простые или короткоживущие устройс-
	тва могут не иметь этот уровень.

7.	HAL: библиотеки производителя МК для его программирования.
	Представляет собой готовый API для написания любого ПО для МК. Возможно пот-
	ребуется замена при портировании.

8.	Device: разметка адресного пространства и стартовый файл производителя МК.
	Содержит все именованные адреса в адресном пространстве для полного управле-
	ния МК и его встроенной периферией.	Заменяется при портировании.