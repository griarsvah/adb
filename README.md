# Android SDK Platform-Tools
ADB (Android Debug Bridge) — это инструмент командной строки, который позволяет взаимодействовать с устройством Android из командной строки компьютера.

## Скачивание
- Перейти на страницу
```https://developer.android.com/tools/releases/platform-tools?hl=ru#downloads```
- Выборать платформу

### Условия соглашения
- Я прочитал и согласен с вышеуказанными условиями
- [Скачать Android SDK Platform-Tools для Windows](https://dl.google.com/android/repository/platform-tools-latest-windows.zip?hl=ru)

## Извлечь
- После скачивания
- ПКМ, Extract All...
- Browse... , Ctrl + N, Type "Android", Select Folder, Extract

##№ Скопировать путь
"C:\Android\platform-tools"

### Добавить в переменную окружения
- Win + R
- Type: ```rundll32 sysdm.cpl,EditEnvironmentVariables```
- Double click path, New, add copy path directory, Ok, Ok

## Разблокировать раздел "Для разработчиков"
- Настройки - О телефоне - Подробная информация и характеристики - Версия ОС
- Настройки - Расширенные настройки - Для разработчиков
- Вкл - Отладка по USB

[adb](https://developer.android.com/tools/adb?hl=ru)
```* daemon not running; starting now at tcp:5037```
Демон ADB не был запущен(система автоматически его запускает)

```* daemon started successfully```
Начинает работу на TCP-порту 5037, который используется ADB для связи между устройством и компьютером.

```* daemon started successfully```
Демон успешно запущен

```List of devices attached```
Выводит список подключенных Android-устройств.

- Уникальный идентификатор (серийный номер) подключенного устройства и напротив слово device — означает, что устройство успешно подключено и готово для работы с ADB
- Если вместо device был бы статус unauthorized, offline или другой, это означало бы проблемы с подключением или авторизацией.

----
Команда запустит ADB-демон, если он не работает
```adb start-server```

Принудительно остановить ADB
```adb kill-server```


Основные команды ADB:
```adb devices``` — список подключенных устройств
```adb install <apk>``` — установка APK
```adb uninstall <apk>``` — удаление APK
```adb shell``` — вход в командную строку устройства
```adb pull <remote> <local> — скачивание файлов с устройства
```adb push <local> <remote> — загрузка файлов на устройство
```adb logcat — Посмотреть все логи

---


## Проверить, подключено ли устройство
```adb devices```


## Выдача приложению разрешений вручную через ADB, без запроса у пользователя
```adb shell pm grant```

## Посмотреть список установленных приложений
```adb shell pm list packages```

## Открыть камеру ```adb shell am start -a android.media.action.IMAGE_CAPTURE```
- Помогло запустить лаунчер напрямую

## Записать видео с экрана
```adb shell screenrecord /sdcard/video.mp4```
- Остановить запись можно `Ctrl + C`, а забрать файл:
```adb pull /sdcard/video.mp4```

## Посмотреть логи работы устройства ```adb logcat```
- Грепнуть```adb shell logcat -d | grep keyevent```

## Грепнуть на винде
```adb shell pm list packages | Select-String "com.microsoft"```
```adb shell pm list packages | findstr "com.microsoft"```


## Перезагрузить устройство
```adb reboot```


### Доп.инфа:
1. На новых Android(13+) методы с `input keyevent` могут не работать** из-за защиты.
2. Если экран выкл то команды могут не выполняться, а терминал может показывать подключение
