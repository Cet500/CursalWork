## Введение

Тема курсовой работы: автоматизация работы банка

Цель курсовой работы: создание ИС на основе СУБД Access для автоматизации, ускорения и упрощения выполнения банковских задач

Задачи курсовой работы:

1. Хранение, изменение и получение всевозможных данных о клиентах и сотрудниках банка и предоставляемых услугах. Обеспечение защиты, сохранности и целостности данных. Итоговое представление данных в удобочитаемом виде.
2. Возможность изменения данных в любой момент.
3. Обеспечение невозможности поломки данных при использовании ИС по назначению.
4. Обеспечение корректного хранения и преобразования данных особых форматов.
5. Возможность использования базы данных по прямому назначения.
6. Возможность для дальнейшего расширения базы данных.

Части пояснительной записки:

1. Теоретическая. В данной части производится описание используемых технических терминов и понятей, используемых типов данных и SQL-запросов.
2. Практическая. В данной части описывается ход анализа, разработки и создания базы данных.


## Теоритическая часть

### Основные термины и понятия баз данных

1. База данных ( БД ) - это совокупность специальным образом организованных данных, хранимых в памяти вычислительной системы. При этом данные должны быть непротиворечивы, минимально избыточны и целостны.
2. Система управления базами данных ( СУБД ) - совокупность программных и лингвистических средств общего или специального назначения, обеспечивающих управление созданием и использованием баз данных.
3. Модели баз данных - описания содержания, структуры и ограничений целостности, используемые для создания и поддержки базы данных. Выделяют следующие основные модели баз данных:
	1. Реляционная - несколько взаимосвязанных между собой двумерных таблиц, наиболее распространённая модель БД.
	2. Постреляционная - расширенная реляционная модель, снимающая ограничение неделимости данных, хранящихся в записях таблиц, с помощью многозначных полей, т.е. полей, значения которых состоят из подзначений. Проще говоря таблица в таблице.
	3. Сетевая - все данные связаны со всеми. Такая модель обычно делится на уровни, так, чтобы протоколы вышестоящего уровня использовали бы протоколы нижестоящего уровня.
	4. Документно-ориентированная - хранение данных в виде коллекций документов. Обычно в формате JSON.
	5. Иерархическая - представление базы данных в виде древовидной структуры, состоящей из объектов различных уровней
4. Реляционная база данных - база данных, основанная на реляционной модели данных. Она представляет связанную между собой совокупность таблиц - сущностей базы данных. Основу реляционной БД составлют следующие элементы:
	1. Таблица - это совокупность связанных данных, хранящихся в структурированном виде в базе данных. Она состоит из столбцов и строк. Таблица содержит определенное число столбцов, но может иметь любое количество строк.
	2. Поля - это столбцы таблицы в реляционной БД. Они отвечают за какие-либо характеристики объекта и содержат значения данного свойства.
	3. Записи - это строки таблицы в реляционной БД. Они отвечают за собственно объекты, хранимые в БД, и содержат набор значений свойств, размещенных в полях базы данных. Каждая запись однозначно определяется одним или несколькими уникальными значениями.
	4. Связь - отношение подчиненности, которое определяет, что для каждой записи главной таблицы может существовать одна или несколько записей во внешней таблице. Выделяют следующие виды связей:
		1. Ключевое поле ( первичный ключ ) - это поле, значения которого однозначно определяют записи в таблице и являются уникальными в пределах данной таблицы. Служит как ограничение целостности.
		2. Внешний ключ ( вторичный ключ ) - поле связи дочерней таблицы, является ограничением целостности - дочерняя таблица не может ссылаться на несуществующие записи главной таблицы.
		3. Связь один-к-одному ( 1:1 ) - к одному главной первой таблицы соответствует только один атрибут внешней таблицы и наоборот.
		4. Связь один-ко-многим ( 1:М ) - к одному атрибуту главной таблицы соответствует несколько атрибутов внешней таблицы.
		5. Связь многие-ко-многим ( М:М ) - к одному атрибуту главной таблицы соответствует несколько атрибутов внешней таблицы и наоборот.
	5. Индекс - объект базы данных, создаваемый с целью повышения производительности поиска данных. При этом индексы замедляются процессы вставки и удаления данных, т.к. они должны производить перерасчёт индексов.
    6. Данные - формы представления информации, с которыми имеют дело информационные системы и их пользователи.

### Нормализация баз данных

Нормализация базы данных ( нормализация ) - процесс преобразования реляционной базы данных к виду, отвечающему нормальной форме. Проще говоря, это процесс организации данных в базе данных. Нормализация позволяет избежать различных ошибок при проектировании баз данных, которые могут привести к ошибкам, избыточности ( лишним, бесполезным или дублированным, повтояющимся данным ), нарушению целостности, аномалиям добавлений, обновлений, удалений, а также помешать расширению и развитию базы данных в дальшейшем. Обычно данные преобразования производятся с помощью декомпозиции, т.е. разбивания данных на атомарные ( неделимые ), первичные ( невыводимые, исходные ) значения. Не смотря на то, что нормализация баз данных является по сути рекомендацией для разроботчиков, её принципов лучше придерживаться, так они позволяют сразу создать правильную модель базы данных.

Нормальная форма ( НФ ) -  совокупность требований и рекомендаций, предъявляемых к структуре таблиц реляционной базы данных, для устранения из базы избыточных зависимостей полями таблиц. При этом каждая последующая нормальная форма требует выполнения также и предущих, если они есть. Также, к базовой и обычно достаточной нормализации относят первые три НФ, остальные же являются более затратными и даже не всегда полностью выполнимыми, и выполняются в зависимости от заданной задачи.

Возможные нормальные формы:

1. 1 НФ ( первая НФ ) - таблица находится в 1 НФ, если все значения данных в её полях являются атомарными. Т.е. если в каждой ячейке таблицы содержится одно и только одно значение. Если это не так, то необходимо разделить значения из одной строки на несколько, даже если они будут повторяться. 
2. 2 НФ ( вторая НФ ) - таблица находится во 2 НФ, если она уже соответствует 1 НФ, и каждое не ключевое поле зависит только от ключевого поля . Т.е. если значения в каждом поле не повторяются, за исключением внешних ключей и нет подмножеств данных, что можно вынести в отдельную таблицу. В противном случае необходимо выявить повторяющиеся данные и переместить их в отдельную таблицу, а затем объединить их с помощью ключей.
3. 3 НФ ( третья НФ ) - таблица находится в 3 НФ, если она уже соответствует 2 НФ, и каждое не ключевое поле логически зависит от таблицы и ключевого поля. Т.е. если какое-либо поле в базе данных может быть связанно более с чем одной таблицей, оно должно быть вынесено, а остальные поля должны зависить лишь от своей таблицы.

### Типы данных в СУБД Access

Все данные в Access хранятся в виде заранее определённых типов и форматов данных, которые указываются при таблицах:

1. Короткий текст - поле для короткого текста ( указывается до 255 символов ). Если введённых данных меньше длины поля, остатки заполняются пробелами. Обычно этот тип используется для хранения нескольких слов или данных особого формата. Не имеет заранеее определённых форматов, но поддерживает маски хранения и ввода.
2. Длинный текст / поле MEMO - поля для большого текста ( до 65535 символов при ручном вводе, или до 2ГБ текста при автозаполнении ( 2 байта на знак ) ). Не имеет форматов, по сути являсь обычным текстом.
3. Числовой - поле для хранения числовых значений. Подразделяется на несколько форматов:
	1. Байт ( 1 байт / 0 - 255 )
	2. Целое ( 2 байта / -32 768 - 32 767 )
	3. Длинное целое ( 4 байта / -2 147 483 648 - 2 147 483 647 )
	4. Одинарное с плавающей точкой ( 4 байта / -3.4e38 - 3.4e3.8 / точность - 7 знаков )
	5. Двойное с плавающей точкой ( 8 байт / -1.797e308 - 1.797e308 / точность - 15 знаков )
	6. Действительное ( 12 байт / точность - 28 знаков )
	7. Код репликации ( 16 байт ) - число в 16-тиричной системе счисления, формата {00000000-0000-0000-0000-000000000000}.
4. Дата и время - поля для хранения временных значений. Имеет несколько форматов:
	1. Полный формат даты ( dd.MM.yyyy hh:mm:ss )
	2. Длинный формат даты ( dd month yyyy г. )
	3. Средний формат даты ( dd-mon-yyyy ) 
	4. Краткий формат даты ( dd.MM.yyyy )
	5. Длинный формат времени ( hh:mm:ss )
	6. Средний формат времени ( h:mm )
	7. Краткий формат времени ( hh:mm )
5. Денежный - поле для хранение денежных или нестандартных числовых значений. По сути явлется обычным числом, но никогда не округляется при вычислениях. Обладает следующими форматами:
	1. Основной ( 1000,000 ) - обычный числовой формат
	2. Денежный ( 1 000,00 Р ) - денежный формат в рублях
	3. Евро ( 1 000,00 E ) - денежный формат в евро
	4. Фиксированый ( 1000,00 ) - числовой формат с фиксированными ограничениями размеров
	5. С разделителями разрядов ( 1 000,00 ) - числовой формат с разделением разрядов пробелом
	6. Процентный ( 1000,00% ) - формат для процентов
	7. Экспоненцинальный ( 1,000E+03 ) - запись числа в виде степени 10
6. Счётчик - поле для последовательных или случайных числовых значений. Обычно используется для ключевого поля, в качестве уникального индефикатора. Не всегда отображает реальное количество строк в таблице. Не может быть более одного в таблице. Не может иметь пустое значение ( NULL ). Имеет лишь два формата:
	1. Длинное целое ( 4 байта ) - обычные целые числа, могут быть как последовательными, так и случайными. Обычно используется для создания уникального значения в таблице. Часто называется просто ID ( identificator / идентификатор ).
	2. Код репликации ( 16 байт ) - число в 16-тиричной системе счисления, формата {00000000-0000-0000-0000-000000000000}. Используется для репликации нескольких баз данных, либо для создания разных объектов в одинаковых баз данных. Также называется GUID ( global unicue identificator / глобальный уникальный идентификатор ).
7. Логический - поле для хранения булевых значений, т.е. формата да / нет. Может быть отображено в виде поля с флажком.
8. Поле объекта OLE - поля для хранения изображений, документов, графиков и других объектов из других программ Windows, размером до 2ГБ.
9. Вложение - поле для хранения файлов в виде вложений как в электронной почте. Одно поле может иметь неограниченное количество вложенных файлов, но суммарно размером не более 2ГБ.
10. Гиперссылка - поле для указания адреса ссылки на объект в интернете, локальной сети или локальном компьютере. 
11. Вычисляемое поле - поле для вычисляемых значений любого типа и формата данных.
12. Мастер подстановок - мастер для создания подстановок для любых типов и форматов данных. Не изменяет тип, но автоматически добавляет подстановочные значения.

### Структурированный язык запросов ( SQL )

Структрурированный язык запросов ( Structure Query Language / SQL ) - декларативный ( описательный ) язык программирования, применяемый для создания, модификации и управления данными в реляционной базе данных, управляемой соответствующей системой управления базами данных.

Методология CRUD ( Create / Read / Update / Delete ) - 

Основные типы SQL-запросов:
1. Создание ( CREATE ) - запрос на создание собственно базы данных или объекта базы данных.
2. Выборка ( SELECT ) - запрос на получение данных из определённых таблиц и полей, отобранные и отсортированные по заранее заданным параметрам.
3. Вставка ( INSERT ) - запрос на добавление данных в таблицу. При этом данные могут быть как заданы явно, так и быть получены или изменены самой СУБД.
4. Обновление ( UPDATE ) - запрос на изменение уже существующих данных в таблице.
5. Изменение таблицы ( ALTER TABLE ) - запрос на изменение метаданных, свойств и структуры таблицы.
6. Удаление ( DELETE ) - запрос на удаление данных из таблицы, всех или по шаблону.
7. Очистка ( TRUNCATE ) - запрос на удаление всех данных и метаданных из определённой таблицы.
8. Полное удаление ( DROP ) - запрос на полное удаление всей таблицы или даже базы данных целиком.

Синтаксис SQL сильно разнится в зависимости от типа запроса, и незначительно - в зависимости от диалекта SQL для выбранной СУБД.

Примеры запросов:


## Практическая часть

### Анализ предметной области

### Разработка базы данных в среде СУБД Access

### Обосновать выбор платформы технических средств при создании ИС


## Заключение


## Список источников