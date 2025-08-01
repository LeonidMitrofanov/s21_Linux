## Part 1. Установка ОС
### Установить Ubuntu 20.04 Server LTS без графического интерфейса.
![Ubuntu version](images/part_1/1_vm_install.png "Ваша подпись к изображению")\
Рисунок 1: Версия убунту

## Part 2. Создание пользователя
### Создать пользователя, отличного от пользователя, который создавался при установке.
![](images/part_2/1_add_user.png "Ваша подпись к изображению")

### Пользователь должен быть добавлен в группу adm.
![](images/part_2/2_usermod.png "Ваша подпись к изображению")

### Проверяем был ли создан пользователь.
![](images/part_2/3_cat_passwd.png "Ваша подпись к изображению")

## Part3. Настройка сети ОС
### Задать название машины вида user-1
![](images/part_3/1_change_hostname.png "Ваша подпись к изображению")

### Установить временную зону, соответствующую вашему текущему местоположению.
![](images/part_3/2_set_timezone.png "Ваша подпись к изображению")

### Вывести названия сетевых интерфейсов с помощью консольной команды.
![](images/part_3/3_network_interface.png "Ваша подпись к изображению")\
Заметим, что в выводи присутствует неизвестный нам интерфейс lo.

lo (loopback) - интерфейс локальной петли. Все адреса в сети 127.0.0.1 могут идентифицировать только данную машину и никогда не уходят в сеть. Любая посылка, отправленная на адрес 127.0.0.1, не покинет компьютер (виртуальную машину). Такая адресация может быть использована для взаимодействия между локальными приложениями (Nginx обращается к Apache2, который слушает
TCP порт 80 по адресу 127.0.0.1, PHP обращается к MySQL, который слушает TCP-порт 3306 по адресу 127.0.0.1, и т. д.).

### Используя консольную команду получить ip адрес устройства, на котором вы работаете, от DHCP сервера.
![](images/part_3/4_local_ip.png "Ваша подпись к изображению")\
Видим, что локальный IP машины - 192.168.64.9

Для работы по сети любому устройству требуется IP-адрес. В протоколе IPv4 это числовой идентификатор, состоящий из 4 разрядов, каждый из которых отделяется точкой, без него устройство не может быть определено в сетевой инфраструктуре. \
Прикладной протокол DHCP выполняет всю работу по подбору сетевых настроек автоматически, без необходимости присваивать вручную каждому устройству свой IP-адрес. Это очень упрощает работу системного администратора в случае расширения сети.

### Определить и вывести на экран внешний ip-адрес шлюза (ip) и внутренний IP-адрес шлюза, он же ip-адрес по умолчанию (gw).
![](images/part_3/5_route&local_ip.png "Ваша подпись к изображению")\
Внешний IP шлюза: 2.155.159.223 \
Внутренний IP шлюза: 192.168.64.1

### Задать статичные настройки ip, gw, dns.
![](images/part_3/6_set_static_ip.png "Ваша подпись к изображению")

1. Изменили конфигурационный файл с помощью vim
2. Применили изменения с помощью ```sudo netplan apply```

### Успешно пропинговать удаленные хосты 1.1.1.1 и ya.ru
![](images/part_3/7_ping_1111_yaru.png "Ваша подпись к изображению")

## Part 4. Обнавление ОС.
### Обновить системные пакеты до последней на момент выполнения задания версии.
![](images/part_4/1_apt_upgrade.png "Ваша подпись к изображению")

## Part 5. Использование команды sudo
Команда sudo (от англ. SuperUser DO) — это команда в Linux и других Unix-подобных системах, которая позволяет выполнять действия с правами суперпользователя (root).
### Разрешить пользователю, созданному в Part 2, выполнять команду sudo.
![](images/part_5/1_sudo.png "Ваша подпись к изображению")
### Поменять hostname ОС от имени пользователя, созданного в пункте Part 2.
![](images/part_5/2_change_hostname.png "Ваша подпись к изображению")

## Part 6. Установка и настройка службы времени
### Настроить службу автоматической синхронизации времени.
![](images/part_6/1_NTPSunchronized.png "Ваша подпись к изображению")

## Part 7. Установка и использование текстовых редакторов
### Установка текстовых редакторов
- Установка текстового редактора vim:\
 `sudo apt install vim`
- Установка текстового редактора nano:\
 `sudo apt install nano`
- Установка текстового редактора mcedit:\
  `sudo apt install mc`
### Создание файла
#### VIM
1. Создайте файл test_vim.txt:\
  `vim test_vim.txt`
2. Для записи в файл: `i`
3. Для выхода из редактора с сохранением: `Esc`, `:`, `wq`

<img src="images/part_7/vim/1_nickname.png" heigth="300"/>

#### NANO
1. Создайте файл test_nano.txt:\
`nano test_nano.txt`
2. Управление:
- `Ctrl+x` - выйти из редактора
- `Y` - сохранить файл
- `Enter`- сохранить с прежним именем

<img src="images/part_7/nano/1_nickname.png" heigth="300"/>

#### MCEDIT
1. Создайте файл test_mcedit.txt:\
`mcedit test_mcedit.txt`
2. Управление:
- `esc` - выйти из редактора
- `Да` - сохранить файл

<img src="images/part_7/mcedit/1_nickname.png" heigth="300"/>

### Редактирование файла
#### VIM
1. Откройте файл test_vim.txt:\
  `vim test_vim.txt`
2. Для записи в файл: `i`
3. Для выхода из редактора без сохранения: `Esc`, `:`, `q!`

<img src="images/part_7/vim/2_no_change.png" heigth="300"/>

#### NANO
1. Откройте файл test_nano.txt:\
`nano test_nano.txt`
2. Управление
- `Ctrl+x` - выйти из редактора
- `N` - не сохранять изменения

<img src="images/part_7/nano/2_no_change.png" heigth="300"/>

#### MCEDIT
1. Откройте файл test_mcedit.txt:\
`mcedit test_mcedit.txt`
2. Управление:
- `esc` - выйти из редактора
- `Нет` - сохранить файл

<img src="images/part_7/mcedit/2_no_change.png" heigth="300"/>

### Работа с поиском и заменой в текстовых редакторах
#### **VIM**  
##### **Поиск слова**  
1. Откройте файл:  
   ```bash
   vim test_vim.txt
   ```  
2. Введите команду:  
   ```
   /clever
   ```

<img src="images/part_7/vim/3_find.png" heigth="300"/>

#### **Замена слова**  
1. Введите команду:  
   ```
   :%s/старое_слово/новое_слово/g
   ```  
   `%s` — замена во всём файле.  
   `g` — все совпадения в строке.  

<img src="images/part_7/vim/4_replace.png" heigth="300"/>

---

### **NANO**  
#### **Поиск слова**  
1. Откройте файл:  
   ```bash
   nano test_nano.txt
   ```  
2. Нажмите `Ctrl+W`
3. Введите искомое слово → `Enter`

<img src="images/part_7/nano/3_find.png" heigth="300"/>

#### **Замена слова**  
1. Нажмите `Ctrl+\`
2. Введите:  
   - `Старое_слово` → `Enter` 
   - `Новое_слово` → `Enter`
3. Подтвердите замену:  
   - `A` — заменить все

   **Скриншот замены в Nano:**  
   <img src="images/part_7/nano/4_replace.png" heigth="300"/>

---

### **MCEdit**  
#### **Поиск слова**  
1. Откройте файл:  
   ```bash
   mcedit test_mcedit.txt
   ``` 
2. Нажмите `F7` → введите слово → `Enter`
   <img src="images/part_7/mcedit/3_find.png" heigth="300"/>

#### **Замена слова**  
1. Нажмите `F7`
2. Введите:  
   - `Старое_слово` → `Enter` 
   - `Новое_слово` → `Enter`

   <img src="images/part_7/mcedit/4_replace.png" heigth="300"/>


## Part 8. Установка и базовая настройка сервиса SSHD
### Установить службу SSHd.
Установите пакет openssh:
```bash
sudo apt install openssh-server
```

### Добавить автостарт службы при загрузке системы
Добавьте пакет SSH-сервера в автозагрузку:
```bash
sudo systemctl enable ssh
```
Проверьте работу SSH
```bash
systemctl status ssh
```
<img src="images/part_8/1_autostart_enabled.png" heigth="300"/>

### Перенастроить службу SSHd на порт 2022
Отредактируйте файл sshd_config с помощью:
```bash 
sudo vim /etc/ssh/sshd_config
```
<img src="images/part_8/2_change_port.png" heigth="300"/>

### Используя команду ps, показать наличие процесса sshd. Для этого к команде нужно подобрать ключи
ps (Process Status) — утилита для вывода информации о запущенных процессах.
- -p \<PID\> — показать только процесс с указанным PID.
- -e — флаг, показать все процессы (не только текущего пользователя).
- | (pipe) — перенаправляет вывод ps в grep.
- grep sshd — фильтрует строки, содержащие "sshd".

<img src="images/part_8/3_show_sshd.png" heigth="300"/>

### Вывод команды `netstat -tan`
<img src="images/part_8/4_netstat_output.png" heigth="300"/>

Команда `netstat` выводит сетевые соединения, а флаги `-tan` задают формат вывода:

| Флаг | Описание |
|------|----------|
| **`-t`** | Показать только **TCP-соединения** (исключая UDP и другие протоколы). |
| **`-a`** | Показать **все соединения** (включая слушающие сокеты и установленные подключения). |
| **`-n`** | Выводить **числовые адреса и порты** (без попытки разрешения имён через DNS). |

**Почему `-n` полезен?**  
Без него `netstat` попытается преобразовать IP-адреса в имена хостов (например, `0.0.0.0:22` → `localhost:ssh`), что замедляет вывод.

**Значение `0.0.0.0` и `::`**
- **`0.0.0.0:22`** (IPv4):  
  Сервер слушает **на всех доступных сетевых интерфейсах** (Wi-Fi, Ethernet, локальный интерфейс).  
  **Пример:** SSH-сервер доступен по любому IP-адресу компьютера.

- **`:::22`** (IPv6, аналог `0.0.0.0`):  
  Сервер принимает подключения по IPv6 **на всех интерфейсах**.  
  Если в системе включён IPv6, этот сокет может обрабатывать и IPv4-подключения (зависит от настройки `IPV6_V6ONLY`).




## Part 9. Установка и использование утилит **top**, **htop**
### **top**
<img src="images/part_9/1_top.png" heigth="300"/>

| Параметр | Значение | Комментарий |
|----------|----------|-------------|
| **Uptime** | `3:52` | Время работы системы без перезагрузки. |
| **Авторизованные пользователи** | `1 users` | Компьютер использует только 1 пользователь (cleverbo). |
| **Общая загрузка системы (load average)** | `0.75, 0.60, 0.55` | Средняя загрузка за 1, 5 и 15 минут. |
| **Общее количество процессов** | `159 total` | Из них `1` работает, `158` спят. |
| **Загрузка CPU** | `100% idle` | CPU не нагружен. |
| **Загрузка памяти** | `307.0 MiB used ` | Память заполнена на 10%. |
| **PID процесса с max памятью** | `PID: 3238 (fwupd)` | Занимает 2% памяти. |
| **PID процесса с max TIME** | `PID: 645 (multipathd)` | `0:09:03` процессорного времени. |

#### **Управление `top`:**
| Команда | Действие |
|---------|----------|
| `Shift + M` | Сортировка по **памяти**. |
| `Shift + T` | Сортировка по **времени работы**. |

#### Сортировка по памяти:
<img src="images/part_9/top/2_orderby_mem.png" heigth="300"/>

#### Сортировка по времени:
<img src="images/part_9/top/3_orderby_time.png" heigth="300"/>

### **htop**
1. **Сортировка:**  
   - По `PID` → `F6` → Выбрать `PID`.
   <img src="images/part_9/htop/sorts/1_time.png" heigth="200"/>
   - По `PERCENT_CPU` → `F6` → Выбрать `CPU%`.
   <img src="images/part_9/htop/sorts/2_CPU.png" heigth="200"/>
   - По `PERCENT_MEM` → `F6` → Выбрать `MEM%`.
   <img src="images/part_9/htop/sorts/3_mem.png" heigth="200"/>
   - По `TIME` → `F6` → Выбрать `TIME+`.
   <img src="images/part_9/htop/sorts/4_time.png" heigth="200"/>

2. **Фильтр для `sshd`:**
   - Нажать `F4` → Ввести `sshd`.
   <img src="images/part_9/htop/1_sshd.png" heigth="300"/>

3. **Поиск `syslog`:**
   - Нажать `F3` → Ввести `syslog` → Enter.
   <img src="images/part_9/htop/2_syslog.png" heigth="300"/>

4. **Дополнительная информация:**  
   - Включить `hostname`, `clock`, `uptime` через `F2` → `Meters`.
   <img src="images/part_9/htop/3_addition_info.png" heigth="300"/>

## Part 10. Использование утилиты **fdisk**
### Запуск команды `fdisk -l`:
<img src="images/part_10/1_fdisk.png" heigth="300"/>

### Жесткий диск:
| Название | Размер | Количество секторов | 
|---------|----------|----------|
| /dev/vda | 64 GiB | 127817728 |

### Swap
### Запуск команды `swapon --show`:
<img src="images/part_10/2_swap.png" heigth="300"/>

## Part 11. Использование утилиты **df**
<img src="images/part_11/1_df.png" heigth="300"/>

#### **Результат `df /`:**  
- **Размер:** `31270768 KB`
- **Занято:** `7411928 KB`
- **Свободно:** `22244812 KB`
- **Использование:** `25%`  
- **Единица измерения:** **Килобайты (1K-blocks)**  

<img src="images/part_11/2_df_Th.png" heigth="300"/>

#### **Результат `df -Th /`:**  
- **Тип ФС:** `ext4`  
- **Размер:** `30G`  
- **Занято:** `7,1G`  
- **Свободно:** `22G`  
- **Использование:** `25%`  
- **Единица измерения:** **Гигабайты (автомасштабирование)**  



## Part 12. Использование утилиты **du**
### Вывести размер папок /home, /var, /var/log
<img src="images/part_12/1_dir.png" heigth="300"/>

### Вывести размер всего содержимого в /var/log
<img src="images/part_12/2_var_log_all.png" heigth="300"/>


## Part 13. Установка и использование утилиты **ncdu**
### Установка: `sudo apt install ncdu`
### Размер /home:
<img src="images/part_13/1_home.png" heigth="300"/>

### Размер /var:
<img src="images/part_13/2_var.png" heigth="300"/>

### Размер /var/log:
<img src="images/part_13/3_var_log.png" heigth="300"/>

## Part 14. Работа с системными журналами
### **1. Просмотр лог-файлов**

**1.1. `/var/log/dmesg`**  
Содержит журнал сообщений ядра.
```bash
sudo less /var/log/dmesg
```

**1.2. `/var/log/syslog`**  
Основной системный лог.
```bash
sudo less /var/log/syslog
```

**1.3. `/var/log/auth.log`**  
Лог аутентификации (ключевой файл для задания).  
```bash
sudo less /var/log/syslog
```

---

#### **2. Поиск последней успешной авторизации**  
**Команда для поиска:**  
```bash
sudo grep -a "sesson opened" /var/log/auth.log | tail -n 1
```
**Параметры для отчёта:**  
- **Время:** `May 11 15:05:18`  
- **Имя пользователя:** `cleverbo`  
- **Метод входа:** `Локальный вход через консоль`

**Скриншот:**  
<img src="images/part_14/1_session_opened.png" heigth="300"/>

---

#### **3. Перезапуск службы SSHd**  
**Команда:**  
```bash
sudo systemctl restart sshd
```

**Поиск сообщения о рестарте в логах:**  
```bash
sudo grep -a "Secure Shell" /var/log/syslog | tail -n 4
```

**Скриншот:**
<img src="images/part_14/2_restart_sshd.png" heigth="300"/>

## Part 15. Использование планировщика заданий **CRON**
### Создание задания в CRON для команды uptime каждые 2 минуты

Откроем crontab для редактирования:
```bash
crontab -e
```

Добавим строку:
```
*/2 * * * * uptime
```

#### Поиск записей в системных журналах

Просмотрим логи CRON (для Ubuntu/Debian):
```bash
grep CRON /var/log/syslog | grep uptime
```

Вывод:
<img src="images/part_15/1_CRON_work.png" heigth="300"/>

#### Просмотр текущих заданий CRON

Выполним:
```bash
crontab -l
```

Вывод: \
<img src="images/part_15/2_curent_tasks.png" heigth="300"/>

### Удаление всех заданий из CRON

Выполним:
```bash
crontab -r
```

Проверим, что задания удалены:
```bash
crontab -l
```

Вывод: \
<img src="images/part_15/3_no_crontab.png" heigth="300"/>