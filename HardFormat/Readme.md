# HardFormat (Stego 50)

Дан [архив](https://github.com/vnide/AeroSpace-CTF/blob/master/HardFormat/HardFormat.zip) с непонятным видеофайлом внутри. Разархивируем, и глянем это "видео" в Hex Editor'е:

![](https://github.com/vnide/AeroSpace-CTF/blob/master/HardFormat/files/1.jpg)

Да это же RAR архив! Меняем ему расширение, и смотрим, что в нём.

Теперь у нас 2 файла: "Instructions.doc" и "Linux.exe".

Займёмся сперва DOC файлом. Microsoft Word открывать его корректно отказывается. Взглянем опять на его заголовок:

![](https://github.com/vnide/AeroSpace-CTF/blob/master/HardFormat/files/2.jpg)

JPG-изображение! Меняем расширение .doc на .jpg, и смотрим.

Хм... Картинка с большим разрешением. Размер соответствует. Подробное изучение рисунка не дало результатов. Флаг не изображён.

Займёмся файлом "Linux.exe". Сразу же смотрим в заголовок файла:

![](https://github.com/vnide/AeroSpace-CTF/blob/master/HardFormat/files/3.jpg)

Hex Editor говорит, что это WIM файл.


