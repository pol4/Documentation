# Команды OTL

**OTL** – **O**pen **T**echnology **L**anguage – высокоуровневый язык для работы с данными, не требующий от пользователя навыков программирования.

Язык OTL применяется в интерактивной среде разработки EVA для создания поисковых запросов к различным источникам данных для последующей визуализации и анализа данных.

Структура поиска на языке OTL выглядит следующим образом:

**данные из индекса <аргументы> | команда1 <аргументы> | команда2 <аргументы> | ...**

Запрос состоит из серии команд, разделенных конвейером (|), который принимает выходные данные одной команды и передает их в следующую.

Команды в запросе используются для получения индексированных данных, фильтрации нежелательной и извлечения дополнительной информации, вычисления значений и проведения статистического анализа.

Результаты поиска, извлеченные из индекса, можно рассматривать как динамически создаваемую таблицу.

В документе представлены команды языка OTL.

Описание каждой команды снабжено многочисленными примерами, позволяющими наглядно продемонстрировать её возможности в решении разноплановых задач обработки данных.

| **Команда** | **Действие** | **Пример** |
| --- | --- | --- |
| [**addcoltotals**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#addcoltotals) | Добавляет сумму каждого числового поля в конец набора результатов запроса. | _... | addcoltotals labelfield=Total label=Flights_ |
| [**addinfo**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#addinfo) | Добавляет к каждому событию информацию о времени и идентификаторе запроса, в результате выполнения которого получена запись. | _... | addinfo_ |
| [**addtotals**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#addtotals) | Вычисляет арифметическую сумму числовых полей для каждого результата запроса. | _... | addtotals Germany Russia USA fieldname=SUM_ |
| [**append**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#append-union) | Добавляет результаты подзапроса, как новые записи текущего запроса. | _... | append \[search index=access\_web\_server | top 1 clientip by method\]_ |
| [**appendcols**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#appendcols) | Добавляет результаты подзапроса, как новые поля текущего запроса. | _... | appendcols \[serach index=LA\_Air\]_ |
| [**appendpipe**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#appendpipe) | Добавляет дополнительные преобразования (subpipeline) к результатам основного запроса. | _... | appendpipe \[| eval SUM=TerminalA+TerminalB+TerminalC\]_ |
| [**bin**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#bin) | Отображает значения поля в дискретный набор значений. | _... | bin bins=3 testField_ |
| [**chart**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#chart) | Группирует записи по указанному полю. | _... | chart count(Population) by Country_ |
| [**collect**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#-5) | Сохраняет результаты запроса в указанном индексе. | _... | collect index=transactions\_russia source=transactions sourcetype=transactions_ |
| [**command**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#command) | Использует функции Spark. | _... | command empty\_check=isnotnull(phrase)_ |
| [**convert**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#convert) | Конвертирует значения поля в числовые значения. | _... | convert ctime(<testField>)_ |
| [**dedup**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#dedup) | Удаляет события с повторяющимися значениями полей. | _... | table Terminal, Arrival\_Departure| dedup Terminal_ |
| [**delta**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#delta) | Вычисляет разницу между текущим значением поля и его значением несколькими записями ранее. | _... | where currency="EUR" | sort \_time | delta sum as delta\_sum\_eur_ |
| [**eval**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#eval) | Создаёт новое поле и заполняет его вычисленными значениями. | _... | eval currency\_low=lower(currency)_ |
| [**eventstats**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#eventstats) | Считает статистику из значений полей без трансформации исходных данных. | _... | eventstats max(temperature) as temperature_ |
| [**fields**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#fields-table) | Отображает только указанные поля. Синоним команды **table**. | _... | fields testField1 testField2_ |
| [**fieldsummary**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#fieldsummary) | Отображает количество значений, максимальное, среднее, минимальное значения и стандартное отклонение для каждого поля. | _... | fieldsummary_ |
| [**filldown**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#filldown) | Заполняет пропуски значениями из предыдущей записи. | _... | filldown_ |
| [**fillnull**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#fillnull) | Заполняет пропуски указанным значением. | _... | fillnull value="noValue"_ |
| **filter** | Фильтрует записи в зависимости от заданного условия. Синоним команды [**search**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#search-filter). | _... | filter {"query": "!(Terminal=\\"Terminal 6\\")"}_ |
| [**foreach**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#foreach) | Для каждого из полей выполняет шаблонный подзапрос. | _... | foreach test\* \[eval sum=test1+test2\]_ |
| [**head**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#head) | Отображает заданное количество первых записей запроса. | _... | head 3_ |
| [**inputlookup**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#inputlookup) | Загружает данные из csv-файла. | _| inputlookup testTable.csv |..._ |
| [**join**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#join) | Объединяет результаты поискового подзапроса с результатами основного запроса. | _search index=... | join \[ index=... \]_ |
| [**lookup**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#lookup) | Добавляет данные из внешней таблицы. | _... | lookup students.csv Name, age_ |
| [**makemv**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#makemv) | Конвертирует поле, состоящее из одного значения, в поле, состоящее из нескольких значений. | _... | makemv testFied delim=";"_ |
| [**makeresults**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#makeresults) | Создает (генерирует) требуемое количество результатов поиска. | _| makeresults count=3 | ..._ |
| [**mvcombine**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#mvcombine) | Группирует записи, отличающиеся только значениями в отдельных полях. | _... | mvcombine testField_ |
| [**mvexpand**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#mvexpand) | Преобразует событие с полем из нескольких значений в несколько отдельных событий. | _... | mvexpand fields_ |
| [**nomv**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#nomv) | Конвертирует поле, состоящее из нескольких значений, в поле, состоящее из одного значения (в строку). | _... | nomv testField_ |
| [**otloadjob**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#otloadjob) | Извлекает из кеша результаты ранее выполненного запроса. | _otloadjob spl="index=\\"apache\\" | ..._ |
| [**otstats**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#otstats) | Получает проиндексированные данные из индекса. | _otstats index="linux-log" severity="ERR\*" | ..._ |
| [**outputlookup**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#outputlookup) | Сохраняет результаты запроса в статическую таблицу (lookup). | _... | outputlookup transactions\_eur.csv_ |
| [**rangemap**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#rangemap) | Преобразует числовое поле в текстовое по заданному правилу. | _... | rangemap field=sum min=1-5 med=6-15 max=16-30_ |
| [rare](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#rare) | Находит наименее распространённые значения в выбранных полях. | _... | rare 2 Name_ |
| [**rename**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#rename) | Переименовывает одно или несколько полей. | _... | rename dest as "destination country"_ |
| [**replace**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#replace) | Заменяет значение поля указанным значением. | _... | replace oldValue1 newValue in testField_ |
| [**return**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#return) | Используется в подзапросах для подстановки в исходный запрос значения из определенной колонки полученного набора данных. | _... | return avgTemp\] - 1) > 0.05_ |
| [**reverse**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#reverse) | Получает записи в обратном порядке. | _... | reverse_ |
| [**rex**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#rex) | Применяет регулярное выражение к указанному полю. | _... | rex field=testField ".\*(?<new\_host>Q)(?<new\_host2>.\*)"_ |
| [**search**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#search-filter) | Получает необработанные данные из индекса. Синоним команды **filter**. | _search index="linux-log"_ |
| [**sort**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#sort) | Сортирует результаты по заданному полю. | _... | sort testField_ |
| [**spath**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#spath) | Извлекает информацию из структурированных данных в формате JSON. | _... | spath input=github\_response output=commit\_author path=commits{}.author.name_ |
| [**stats**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#stats) | Применяет агрегирующую функцию к полю. | _... | stats max(testField)_ |
| [**streamstats**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#streamstats) | Вычисляет статистику по значениям полей в "потоковом" режиме и добавляет поле результата к каждому событию. | _... | streamstats sum(testField) window=5_ |
| [**superjoin**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#superjoin) | Объединяет результаты из таблицы на диске с результатами основного запроса. | _… | superjoin id, day type=left format=parquet path=folder/table1_ |
| **table** | Отображает только указанные поля. Синоним команды [**fields**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#fields-table). | _... | table testField1 testField2_ |
| [**tail**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#tail) | Отображает заданное количество последних записей запроса. | _... | tail 3_ |
| [**timechart**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#timechart) | Агрегирует результаты по времени. | _... | timechart span=2d sum(Air\_traffic) by Terminal_ |
| [**top**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#top) | Получает наиболее часто встречающиеся значения указанных полей, количество таких значений и их процент среди общего количества значений. | _… | top 3 testField_ |
| [**transaction**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#transaction) | Находит среди множества записей, сгруппированных по указанному набору полей, первую по времени запись (в своей группе). | _... | transaction deposit, well, metric\_name, value_ |
| [**transpose**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#transpose) | Превращает строки таблицы в столбцы и наоборот. | _... | transpose_ |
| [**untable**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#untable) | Преобразует данные из широкой таблицы в длинную таблицу. | _... | untable \_time, metric\_name, value_ |
| [**where**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#where) | Отфильтровывает записи согласно заданным условиям. | _... | where Population > 1000000_ |
| [**xyseries**](http://127.0.0.1:1080/1.2.0.beta/OTL/OTL_commands/OTL_commands/#xyseries) | Конвертирует результаты в пригодный для визуализации табличный формат. | _... | xyseries testField1_ |

# ADDCOLTOTALS

Команда добавляет сумму каждого числового поля в конец набора результатов запроса. Если указан аргумент **labelfield**, в таблицу результатов добавляется столбец с указанным именем.

### Синтаксис команды
