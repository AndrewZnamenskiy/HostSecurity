# Домашнее задание к занятию  «Защита хоста»

------

### Задание 1

1. Установите **eCryptfs**.
2. Добавьте пользователя cryptouser.
3. Зашифруйте домашний каталог пользователя с помощью eCryptfs.


*В качестве ответа  пришлите снимки экрана домашнего каталога пользователя с исходными и зашифрованными данными.*  

### Задание 2

1. Установите поддержку **LUKS**.
2. Создайте небольшой раздел, например, 100 Мб.
3. Зашифруйте созданный раздел с помощью LUKS.

*В качестве ответа пришлите снимки экрана с поэтапным выполнением задания.*

----

### Решение 1

**Подготовка**

Установка: `sudo apt install ecryptfs-utils`

Создание нового пользователя: `sudo adduser --encrypt-home crypto`

Миграция домашнего каталога пользователя: `sudo ecryptfs-migrate-home -u crypto`

Информация для восстановления: `ecryptfs-unwrap-passphrase`

#### Скриншот 1:

![Commit Task1](https://github.com/AndrewZnamenskiy/HostSecurity/blob/main/img/task1p1.png)


#### Скриншот 2:

![Commit Task1](https://github.com/AndrewZnamenskiy/HostSecurity/blob/main/img/task1p2.png)


#### Скриншот 3:

![Commit Task1](https://github.com/AndrewZnamenskiy/HostSecurity/blob/main/img/task1p3.png)


#### Скриншот 4:

![Commit Task1](https://github.com/AndrewZnamenskiy/HostSecurity/blob/main/img/task1p4.png)


---


### Решение 2

**Подготовка**

Установка утилиты разметки диска:  `sudo apt install parted`

Установка LUKS:  `sudo apt install cryptsetup`

Проверка установки: `cryptsetup --version`

Подготовка раздела (luksFormat): `sudo cryptsetup -y -v --type luks2 luksFormat /dev/sdb1`

Монтирование раздела: 
		       ```
	 	       sudo cryptsetup luksOpen /dev/sdb1 disk
		       ls /dev/mapper/disk
	 ```

Форматирование раздела:
			```
		         sudo dd if=/dev/zero of=/dev/mapper/disk
			sudo mkfs.ext4 /dev/mapper/disk
   ```


#### Скриншот 1:

![Commit Task2](https://github.com/AndrewZnamenskiy/HostSecurity/blob/main/img/task2p1.png)


#### Скриншот 2:

![Commit Task2](https://github.com/AndrewZnamenskiy/HostSecurity/blob/main/img/task2p2.png)


#### Скриншот 3:

![Commit Task2](https://github.com/AndrewZnamenskiy/HostSecurity/blob/main/img/task2p3.png)


#### Скриншот 4:

![Commit Task2](https://github.com/AndrewZnamenskiy/HostSecurity/blob/main/img/task2p4.png)



