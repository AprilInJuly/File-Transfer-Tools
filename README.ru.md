# Виджет передачи файлов

## Введение

File Transfer Tools содержит два компонента FTS (File Transfer Server) и FTC (File Transfer Client), которые являются **легкими**, **быстрыми**, **безопасными** и т.д. мощный скрипт передачи файлов между устройствами.

### Функция

1. Передача файлов

- Перенос отдельных файлов или целых папок
- Гарантия безопасности: можно использовать зашифрованную передачу (с использованием протокола Secure Sockets Layer) и передачу в открытом виде.
- Гарантия правильности: проверьте согласованность файлов с помощью значения хэша и оцените, все ли файлы в папке передаются правильно.
- Отображение индикатора выполнения: отображение в реальном времени хода передачи файлов, текущей скорости сети и оставшегося времени передачи.
- Три метода переименования файла с тем же именем, избегая дублирования передачи и перезаписывая передачу

2. Командная строка, которая может легко выполнять команды удаленно и возвращать результаты в режиме реального времени, аналогично ssh
3. Автоматически найти хост службы или вручную указать хост подключения
4. Сравнение папок, которое может отображать такую ​​информацию, как одинаковые и различия файлов в двух папках.
5. Просмотр состояния и информации системы клиента и сервера.
6. Вывод журналов на консоль и в файлы в режиме реального времени, а также возможность автоматической организации сжатых файлов журналов.
7. Удобно тестировать пропускную способность сети между клиентом и сервером
8. Вы можете установить пароль для подключения к серверу для повышения безопасности
9. Удобно синхронизировать содержимое буфера обмена клиента и сервера

### Функции

1. Запускайте, работайте и быстро реагируйте
2. Примите принцип минимальной конфигурации по умолчанию, который можно использовать «из коробки», и вы можете легко изменить конфигурацию самостоятельно.
2. Его можно использовать в любой сетевой среде, такой как локальная сеть и общедоступная сеть, если два хоста могут подключаться к сети.
3. Многопоточная передача, высокая скорость передачи, фактический тест может работать с пропускной способностью до 1000 Мбит / с из-за ограничений оборудования, нет теста на более высокую пропускную способность.
4. Использование памяти во время выполнения невелико, а режим ленивой загрузки используется для обеспечения минимального использования ресурсов.
5. Мгновенно открыть, закрыть и уйти, после закрытия программы не останется никакого процесса
6. В настоящее время совместим с платформами Windows и Linux.

### как выбрать

1. Если вам нужна более мощная служба передачи файлов, выберите FTP-сервер, клиент (например, «FileZilla», «WinSCP» и т. д.)
2. Если вам нужна стабильная синхронизация файлов и обмен ими, рекомендуется использовать «Resilio Sync», «Syncthing» и т. д.
3. Если вы только время от времени передаете файлы/не любите фоновое хранилище и использование ресурсов вышеуказанными сервисами/не нуждаетесь в таком мощном сервисе/хотите настроить функции, выберите «Инструменты для передачи файлов».

## Установите и запустите

`FTS` по умолчанию занимает порты 2023 и 2021, а FTC по умолчанию занимает порт 2022. Среди них порт 2023 используется в качестве TCP-порта прослушивания FTS, а 2021 и 2022 используются в качестве интерфейсов передачи UDP между сервером и клиентом.
Вы можете проверить подробную информацию о конфигурации и изменить вышеуказанную конфигурацию в конце этой статьи.

### Скачать исполняемую программу

1. Нажмите «Отпустить» справа.
2. Загрузите `File Transfer Tools.zip`
3. Разархивируйте папку, дважды щелкните `FTC.exe` или `FTS.exe`, чтобы запустить
4. Или запустите программу в терминале, чтобы использовать параметры программы, такие как `.\FTC.exe [-h] [-t thread] [-host host] [-p]`

### Запуск с интерпретатором Python

1. Клонируйте исходный код в папку вашего проекта.
2. Установите все зависимости, используя `pip install -r requirements.txt`
3. Выполните скрипт с помощью интерпретатора Python.

#### метод быстрого выполнения
```
Взяв в качестве примера Windows, вы можете записать запущенные команды FTS и FTC в виде пакетных файлов, а затем добавить каталог пакетного файла в переменную среды, чтобы вы могли просто ввести `FTS`, `FTC`
Давайте используем стандартную и самую простую команду для запуска программы.

Например, вы можете написать следующую команду в файл `FTS.bat`

``PowerShell
@эхо выключено
"Каталог вашего интерпретатора Python"\Scripts\python.exe "Каталог вашего проекта"\FTS.py %1 %2 %3 %4 %5 %6
```

Запишите следующую команду в файл `FTC.bat`

``PowerShell
@эхо выключено
"Каталог вашего интерпретатора Python"\Scripts\python.exe "Каталог вашего проекта"\FTC.py %1 %2 %3 %4 %5 %6
```

Затем добавьте пакетную папку в переменные среды и, наконец, введите следующую команду в своем терминале, чтобы быстро запустить код.

​```PowerShell
FTC.py [-h] [-t поток] [-host хост] [-p пароль] [--открытый текст]
или
FTS.py [-h] [-d базовый_каталог] [-p пароль] [--открытый текст] [--avoid]
```

В приведенном выше пакетном файле `%1~%9` представляет параметры, переданные программой (`%0` представляет текущий путь)
Обратите внимание, что рабочий путь терминала по умолчанию — это пользовательский каталог (~), если вам нужно изменить файл конфигурации, измените его в этом каталоге.

## Использование

### ФТК

FTC — это клиент для отправки файлов и инструкций.

```
использование: FTC.py [-h] [-t поток] [-хост-хост] [-p пароль] [--открытый текст]

Клиент передачи файлов, используемый для ОТПРАВКИ файлов и инструкций.

необязательные аргументы:
   -h, --help показать это справочное сообщение и выйти
   -t потоки потоков (по умолчанию: 8)
   -host имя хоста или IP-адрес назначения хоста
   -p пароль, --password пароль
                         Используйте пароль для подключения хоста.
   --plaintext Использовать передачу открытого текста (по умолчанию: использовать ssl)
```

#### Параметр Описание

`-t`: указывает количество потоков, по умолчанию это количество логических процессоров.

`-host`: явно укажите имя хоста сервера (имя хоста или IP-адрес) и номер порта (необязательно). Если этот параметр не используется, клиент будет автоматически искать сервер в **той же подсети**

`-p`: Явно укажите пароль для подключения к серверу (по умолчанию у сервера нет пароля).

`--plaintext`: Явно укажите данные для передачи в виде открытого текста, требуя, чтобы сервер также использовал передачу в виде открытого текста.

#### Описание команды

После обычного подключения введите команду

1. Введите путь к файлу (папке), и файл (папка) будет отправлен
2. Введите «sysinfo», отобразится системная информация обеих сторон.
3. Введите `speedtest n`, и скорость сети будет протестирована, где n — это объем данных в этом тесте в МБ. Обратите внимание, что в **Компьютерных сетях** 1 ГБ = 1000 МБ = 1 000 000 КБ.
4. Введите `compare local_dir dest_dir`, чтобы сравнить разницу между файлами в локальной папке и папке сервера.
5. Введите «clip pull/push» или «clip get/send», чтобы синхронизировать содержимое буфера обмена клиента и сервера.
6. Когда вводится другой контент, он используется как инструкция для выполнения сервером, и результат возвращается в режиме реального времени.

#### Выполнить Скриншот

Ниже приведены скриншоты, запущенные на том же хосте.

запуск программы

![запуск](assets/startup.png)

передавать файлы
![файл](assets/file.png)

Команда выполнения: sysinfo

![sysinfo](assets/sysinfo.png)

Выполните команду: speedtest

![спидтест](assets/speedtest.png)

Выполните команду: сравнить

![сравнить](assets/compare.png)

Выполните команду: клип

![клип](assets/clip.png)

Выполнять команды командной строки

![команда](assets/cmd.png)

### ФНС

«FTS» — это серверная часть, используемая для приема и хранения файлов и выполнения инструкций, отправленных клиентом.

```
использование: FTS.py [-h] [-d base_dir] [-p пароль] [--открытый текст] [--avoid]

Сервер передачи файлов, используемый для ПОЛУЧЕНИЯ файлов и выполнения инструкций.

необязательные аргументы:
   -h, --help показать это справочное сообщение и выйти
   -d базовый_каталог, --dest базовый_каталог
                         Место хранения файлов (по умолчанию: C:\Users\admin/Desktop)
   -p пароль, --password пароль
                         Установите пароль для хоста.
   --plaintext Использовать передачу открытого текста (по умолчанию: использовать ssl)
   --avoid Не продолжать передачу, если имя файла повторяется.
```

#### Параметр Описание

`-d, --dest`: Явно укажите место получения файла, по умолчанию используется значение элемента конфигурации "platform_default_path" (платформа Windows по умолчанию **рабочий стол**).

`-p, --password`: Установите пароль для сервера, чтобы предотвратить вредоносные подключения.

`--plaintext`: Явно укажите передачу данных в виде обычного текста и используйте шифрованную передачу ssl по умолчанию.

`--avoid`: если включено, если в каталоге уже есть файл с таким именем, возможны два случая. Если размер файла на принимающей стороне больше или равен размеру отправляющей стороны, ** заблокировать** передачу файла, в противном случае получить и **переписать* *Этот файл; эта функция в основном используется для повторной передачи после того, как большое количество файлов было прервано одновременно, аналогично повторной передаче точки останова, **используйте с осторожностью ** в остальных случаях. Если этот параметр не включен, если существующее имя файла — «a.txt», передаваемые файлы будут называться в соответствии с последовательностью «a (1).txt», «a (2).txt».

#### Запустить скриншот

![FTS](assets/FTS.png)

## конфигурация

Элементы конфигурации находятся в файле конфигурации `config.txt`, если файл конфигурации не существует, программа автоматически создаст файл конфигурации по умолчанию.

### Основная конфигурация Главной программы
`windows_default_path`: расположение получения файлов по умолчанию на платформе Windows.

`linux_default_path`: место получения файла по умолчанию на платформе Linux.

`cert_dir`: место хранения файла сертификата.

### Конфигурация, связанная с журналом
`windows_log_dir`: место хранения файла журнала по умолчанию на платформе Windows.

`linux_log_dir`: место хранения файла журнала по умолчанию на платформе Linux.

`log_file_archive_count`: Архивировать, когда количество файлов журнала превышает этот размер.

`log_file_archive_size`: Архивировать, когда общий размер (в байтах) файла журнала превышает этот размер.

### Конфигурация порта Содержимое, связанное с портом
`server_port`: порт прослушивания TCP сервера

`server_signal_port`: порт прослушивания UDP сервера

`client_signal_port`: порт прослушивания UDP клиента