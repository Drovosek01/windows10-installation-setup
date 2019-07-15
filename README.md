# Что я сделал при установки Windows 10

Эту инструкцию я писал для себя, чтобы после переустановки не вспоминать что и как делать. Инструкция написана после установки Windows 10 v 1903. Некоторые пункты позаимствованы из сборки Windows 10 by kuloymin

## Создание загрузочной флешки

1. Скачиваем rufus
2. Скачиваем оригинальный образ Windows 10 Pro x64 MSDN
3. В rufus выбираем iso образ, разметку GPT и записываем на флешку

## Установка Windows 10

1. Стандартная установка Windows
2. Создание учетной записи с паролем и ответом на 3 контрольных вопроса

## Настройка Windows 10

1. При первом заходе в Windows 10 подключаемся к интернету и ждем пока Windows сама скачает нужные драйвера

2. Скачиваем Windows 10 Digital Activator и активируем Windows

3. **Настройки в "Параметры"**
   1. В "Обновление и безопасность" проверяем наличие обновлений и устанавливаем их
   2. В "Обновление и безопасность" открываем вкладку "Безопасность Windows", открываем пункт "Защита от вирусов и угроз" и выключаем все пункты
   3. Там же в "Безопасность Windows" открываем пункт "Управление приложениями/браузером" и отключаем всю защиту
   4. В поиске параметров пишем "UAC" (либо запускаем любую программу), открываем предложенный вариант и ставим пункт "Никогда не уведомлять"
   5. В "Учетные записи" открываем пункт "Варианты входа" и отключаем автоматический перезапуск приложений
   6. В "Персонализация" переходим в пункт "Цвета" и выбираем цвет "Темный"
   7. В "Персонализация" переходим в пункт "Пуск" и отключаем "Иногда показывать предложения в меню Пуск"
   
4. Скачиваем все драйвера с официального сайта ноутбука и устанавливаем их

    * С драйверами для аудио возможно нужно поэкспериментировать, а так же с их настройками, т.к. в некоторых случаях при воспроизведении звука он слышен только через пару секунд после начала воспроизведения.

5. Настраиваем Проводник
   * Включаем отображение расширений имен файлов

   * Включаем отображение скрытых элементов

   * "Открывать проводник для" ставим "Этот компьютер"

   * Снимаем галочку с "Показать недавно использовавшиеся файлы на панели быстрого доступа"

   * Снимаем галочку с "Показать часто используемые папки на панели быстрого доступа"

   * Ставим галочку в пункте "Выводить полный путь в заголовке окна"

   * ПКМ в пустом месте -> Группировка -> Нет

   * Удаление папок из "Этот компьютер"

   * Удалить "Проверить с помощью Windows Defender" из контекстного меню. Нужно создать файл с расширением .reg и вставить туда этот текст

     
     ```
     Windows Registry Editor Version 5.00
     
     [-HKEY_CLASSES_ROOT\*\shellex\ContextMenuHandlers\EPP]
     
     [-HKEY_CLASSES_ROOT\Directory\shellex\ContextMenuHandlers\EPP]
     ```

   * Удалить "Восстановить прежнюю версию" и "Предыдущие версии" из контекстного меню. Нужно создать файл с расширением .reg и вставить туда этот текст
     
     ```
     Windows Registry Editor Version 5.00
     
     [HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\PreviousVersions]
     
     "DisableLocalPage"=dword:00000001
     "DisableRemotePage"=dword:00000001
     
     [HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\PreviousVersions]
     
     "DisableLocalPage"=dword:00000001
     "DisableRemotePage"=dword:00000001
     ```

   * Перенести "Ножницы", "Paint", "Notepad++", "Typora", "VSCode" на панель задач

6. Настройка панели задач
   * Открепить "Почта"
   * Открепить Microsoft Appstore

7. **Перенести папки пользователя на другой диск**
    * В "Параметры" открываем пункт "Система" вкладку "Память устройства" и нажимаем "Изменить место сохранения нового содержимого". Активируем все пункты, кроме "Новые приложения будут сохранятся...", чтобы файлы сохранялись НЕ на диске с Windows (чтобы в случае переустановки не переносить их вручную)
    * Перейти в папку пользователя и с папками "Рабочий стол", "Документы", "Изображения", "Видео", "Загрузки", "Музыка" сделать следующее:
      * Открыть свойства
      * В свойствах открыть вкладку "Расположение"
      * В строке заменить путь на свой, например в строке `C:\Users\MyUser\3D Objects` удалить все до `\3D Objects` и вставить новый путь, чтобы получилась строка `D:\MyUser\3D Objects`

8. Отключить предупреждения системы безопасности, чтобы при установки программ каждый раз не появлялось уведомление с подтверждением запуска: Открываем "Панель управления" -> "Свойства браузера" -> вкладка "Безопасность" -> кнопка "Другой" -> "Запуск программ и небезопасных файлов" -> Включить

9. Установить курсор "Night Diamond v3" или "DIM v3.2"

## Установка программ

### Важные компоненты

1. Microsoft Visual C++ 2005-2008-2010-2012-2013-2019 Redistributable Package
2. Java
3. Python
4. .Net Framework
5. DirectX 9 или выше
6. Nodejs
7. Adobe Flash Player - сейчас почти нигде не нужен

### Устанавливаемое ПО

1. Google Chrome <https://www.google.ru/chrome/>
2. Bandizip <https://www.bandisoft.com/bandizip/>
3. Notepad++ <https://notepad-plus-plus.org/>
4. K-Lite Codec Pack <https://www.codecguide.com/>
5. VLC Media Player <https://www.videolan.org/vlc/>
6. PotPlayer <http://potplayer.daum.net/?lang=ru>
7. Git Bash <https://git-scm.com/download/>
8. Typora <https://typora.io/>
9. uTorrent
10. Office
11. WinRAR
12. 7-zip <https://www.7-zip.org/>
13. Internet Download Manager
14. Firefox <https://www.mozilla.org/ru/firefox/new/>
15. SumatraPDF <https://www.sumatrapdfreader.org/>
16. XnView <https://www.xnview.com/>
17. Adobe Photoshop
18. HashTab

### Портативное ПО

- Everything
- OldNewExplorer
- Telegram
- SublimeText
- Visual Studio Code
- Tor Browser
- 4K Video Downloader
- AIDA64
- Bandicam
- cmder
- HandBrake
- MediaInfo GUI
- ZDSoft Screen Recorder
- Uninstall Tool
- Unlocker
- XnConvert
- IrfanView
- Explorer++