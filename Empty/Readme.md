# Пусто (Forensic 50)

Дана [электронная табличка .xlsx] (https://github.com/vnide/AeroSpace-CTF/blob/master/Empty/Empty.xlsx)

Файл похож на записки сумасшедшего:) И ни один флаг не подходит под регламент (Aero{MD5}). По всем листам документа разбросаны фразы, путаницы, уловки. Скорее всего в содержимом файла нет ничего полезного - пустая трата времени исследовать всё это.

Давайте-ка заглянем внутрь:)

Как известно, любой файл .docx можно открыть с помощью архиватора. Файл .xlsx не исключение. Переименуем его в .rar и посмотрим, что у него внутри.

![](https://github.com/vnide/AeroSpace-CTF/blob/master/Empty/files/1.jpg)

на первый взгляд ничего необычного. Однако, на пути "Empty.rar\xl\worksheets\\_rels\\_rels\\_rels" находим интересный файл "flag.xml", со следующим содержанием: 

"Aero{b902624cl3f1n0tf1ag5lol0e22e71be67928999lol}     hehehehehehehe"

Опять же, флаг не подходит под регламент (слишком много символов). Похоже, над нами опять подшутили:)

Продолжаем искать дальше. Для удобства исследования, возьмём произвольный .xlsx файл, для сравнения с нашим.

![](https://github.com/vnide/AeroSpace-CTF/blob/master/Empty/files/2.jpg)

В итоге, найден лишний файл, которого нет в других .xlsx файлах. И, как показало дальнейшее исследование, файл "fontTable.xml" содержится в файлах .docx ! Значит перед нами шпионский файл, затесавшийся в структуру .xlsx файла:)

После извлечения "fontTable.xml" откроем его с помощью любого текстового редактора.

Недолго полистав небольшой файл, можно заметить флаг:

![](https://github.com/vnide/AeroSpace-CTF/blob/master/Empty/files/3.jpg)

На этот раз, флаг соответствует регламенту. Значит мы нашли то, что и должны были найти:)

Aero{3aec9dc28fbbf49b470820cdf6843ba2}
