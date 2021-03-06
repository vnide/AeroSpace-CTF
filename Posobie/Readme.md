# Пособие (Stego 200)

Нам дан архив [stego.rar](https://github.com/vnide/AeroSpace-CTF/blob/master/Posobie/stego.rar), после разархивации которого мы наблюдаем PDF документ.

![alt tag](https://github.com/vnide/AeroSpace-CTF/blob/master/Posobie/files/1.jpg)

Исследовав документ, обращаем внимание, что вес файла не соответствует содержимому. 1 страничка PDF весит 10,8 Мб.

Кроме того, после закрытия документа, Adobe Acrobat Reader спрашивает о сохранении файла... И если мы его сохраним, то новый PDF-документ будет вешать всего 360 Кб... Подозрительно...

![alt tag](https://github.com/vnide/AeroSpace-CTF/blob/master/Posobie/files/2.jpg)

![alt tag](https://github.com/vnide/AeroSpace-CTF/blob/master/Posobie/files/3.jpg)

Изучив подробно "Шпаргалку", можно заметить описание команды Copy, которая собирает несколько файлов в один.

Рассмотрим структуру PDF файла получше. Для этого воспользуемся программой Hex Editor.
Любой PDF документ начинается с заголовка "%PDF" и заканчивается "%%EOF". В нашем случае начальный заголовок совпадает, однако конец файла совсем не похож на PDF.

![alt tag](https://github.com/vnide/AeroSpace-CTF/blob/master/Posobie/files/4.jpg)

С помощью поиска попробуем найти конец PDF-документа.

![alt tag](https://github.com/vnide/AeroSpace-CTF/blob/master/Posobie/files/5.jpg)

Бинго! К нашему PDF-файлу что-то приклеено! Давайте определим, что именно.

Известно, что JPG-изображения могут иметь начальный заголовок "яШяа". Значит, скорее всего, к концу PDF-файла приклеено изображение.

С помощью того же Hex Editor'а, или любого текстового редактора (например NotePad++), убираем весь PDF-документ. То есть всё, что находится до заголовка "яШяа".

![alt tag](https://github.com/vnide/AeroSpace-CTF/blob/master/Posobie/files/6.jpg)

Теперь осталось поменять у получившегося файла расширение с PDF в JPG.

Открываем, и перед нами милый котёнок:3

![alt tag](https://github.com/vnide/AeroSpace-CTF/blob/master/Posobie/files/7.jpg)

Однако, всё равно, для такого изображения, размер в 10,4 Мб слишком велик.

Обратимся к "Шпаргалке" ещё раз. В списке утилит для скрытия информации в файлах, про JPG говорится лишь в одном: "Free File Camouflage 1.25". Начнём, пожалуй, с него.

Скачиваем, устанавливаем, запускаем. Выбираем вкладку "De-camouflage a file", выбираем наше изображение с котом, и указываем путь сохранения. Жмём кнопку "De-camouflage!"

О чудо! Из картинки извлёкся архив! В архиве же лежит бесполезное видео, и текстовый файл.

![alt tag](https://github.com/vnide/AeroSpace-CTF/blob/master/Posobie/files/8.jpg)

Мы нашли секретную строку! Осталось перевести её в MD5 и превратить в флаг:

Aero{b7e27fab8123d8bbae1945c4a6f5ee7a}
