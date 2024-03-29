Многое из этого теперь автоматизировано и находится в отдельном репозитории - https://github.com/Drovosek01/settings

В данном репозитории мало смысла, потому что делать вручную то, что можно автоматизировать - мало полезно.

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

     ```plaintext
     Windows Registry Editor Version 5.00

     [-HKEY_CLASSES_ROOT\*\shellex\ContextMenuHandlers\EPP]

     [-HKEY_CLASSES_ROOT\Directory\shellex\ContextMenuHandlers\EPP]
     ```

   * Удалить "Восстановить прежнюю версию" и "Предыдущие версии" из контекстного меню. Нужно создать файл с расширением .reg и вставить туда этот текст

     ```plaintext
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

[Important Apps](/ProgramsList/ImportantApps.md)

### Устанавливаемое ПО

[Installing Apps](/ProgramsList/InstallingApps.md)

### Портативное ПО

[Portable Apps](/ProgramsList/PortableApps.md)
