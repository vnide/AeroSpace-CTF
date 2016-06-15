# HardFormat (Stego 50)

Дан [архив](https://github.com/vnide/AeroSpace-CTF/blob/master/HardFormat/HardFormat.zip) с непонятным видеофайлом внутри, который отказывается воспроизводиться. Разархивируем, и глянем это "видео" в Hex Editor'е:

![](https://github.com/vnide/AeroSpace-CTF/blob/master/HardFormat/files/1.jpg)

Да это же RAR архив, а не видео! Меняем ему расширение, и смотрим, что в нём.

Теперь у нас 2 файла: "Instructions.doc" и "Linux.exe".

Займёмся сперва DOC файлом. Microsoft Word открывать его корректно отказывается. Взглянем опять на его заголовок:

![](https://github.com/vnide/AeroSpace-CTF/blob/master/HardFormat/files/2.jpg)

JPG-изображение! Меняем расширение .doc на .jpg, и смотрим.

Хм... Картинка с большим разрешением. Размер соответствует. Подробное изучение рисунка не дало результатов. Флаг не изображён.

Займёмся файлом "Linux.exe". Сразу же смотрим в заголовок файла:

![](https://github.com/vnide/AeroSpace-CTF/blob/master/HardFormat/files/3.jpg)

Hex Editor говорит, что это WIM файл. Для его открытия нам понадобится 7-Zip. Он с лёгкостью открывает архив, и теперь у нас опять 2 новых файла: "mur_mur_mur.bmp" и "voice.mp3".

Не изменяя традициям сразу же смотрим на заголовок файла "mur_mur_mur.bmp". "ID3" говорит нам о том, что перед нами mp3 файл. Слушаем, ничего интересного, обычная песенка:)

Далее исследуем файл "voice.mp3". В самом начале файла имеется заголовок "1f 8b 08 00". Как подсказывает интернет, перед нами архив с расширением .gz. Открываем его.

Снова файл с именем "voice". Смотрим в заголовок. "./PaxHeaders.8128/". Опять же обратившись к интернету, можно понять, что это .tar архив. Открываем его и извлекаем на этот раз "voice.mp3".

Смотрим в заголовок: "50 4B 03 04" (PK..). На этот раз .zip архив!

![](https://github.com/vnide/AeroSpace-CTF/blob/master/HardFormat/files/4.jpg)

После разархивации получаем очередной "voice.wav". Смотрим в Hex Editor'е:

![](https://github.com/vnide/AeroSpace-CTF/blob/master/HardFormat/files/5.jpg)

А вот и наш флаг! Ура!

Aero{e0abfbcacbe25d19756f793bd3d9a5dd}
