#  Домашнее задание к занятию "Уязвимости и атаки на информационные системы" - Марчук Кирилл


### Задание 1
Скачайте и установите виртуальную машину Metasploitable
Просканируйте эту виртуальную машину, используя nmap.
Ответьте на следующие вопросы:
Какие сетевые службы в ней разрешены?
Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)


1. `Скачеваем Metasploitable и запускаем nmap для сканирования`
2. `Сетевые службы которые в ней разрешены,FTP (vsftpd 2.3.4 и ProFTPD 1.3.1), SSH (OpenSSH 4.7p1), Telnet, SMTP, DNS (BIND 9.4.2), HTTP (Apache 2.2.8), Samba (3.X-4.X), RPC, NFS, MySQL (5.0.51a), PostgreSQL (8.3), VNC, и другие`
3. `vsftpd 2.3.4 — бэкдор с доступом к root-оболочке,https://www.exploit-db.com/exploits/17491`
4. `Samba 3.x — удаленное выполнение команд,https://www.exploit-db.com/exploits/16320`
5. `UnrealIRCd 3.2.8.1 — бэкдор с удаленным выполнением команд,https://www.exploit-db.com/exploits/13853`


---

### Задание 2 Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.Запишите сеансы сканирования в Wireshark.Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?
Как отвечает сервер?

1. `SYN - полуоткрытый скан, сервер отвечает SYN+ACK или RST`
2. `FIN и XMAS - "аномальные" сканы, используют некорректные комбинации флагов, обходят простые файрволы`
3. `XMAS — самый "шумный" и легко обнаружимый из-за нелогичного набора флагов (FIN+PSH+URG вместе)`
4. `UDP — работает принципиально иначе: нет флагов, ответ через ICMP`
5. `Как отвечает сервер? - На открытый TCP-порт: При SYN - отвечает SYN+ACK,При FIN или XMAS - не отвечает`
6. `На закрытый TCP-порт: Всегда отвечает RST (сброс соединения) на любой TCP-пакет`
7. `На открытый UDP-порт: Может ответить UDP-пакетом или ничего не отвечать.`
8. `На закрытый UDP-порт: Отвечает ICMP Port Unreachable (type 3, code 3)`

### Примеры работы сканирования которые выдал Wireshark - FIN-сканирование,SYN-сканирование,XMAS-сканирование,UDP-сканирование.

![zadanie2](https://github.com/ottofonciceron-coder/Vulnerabilities-and-attacks-on-information-systems-13-01-hw/blob/main/FIN-сканирование.png)`

![zadanie2](https://github.com/ottofonciceron-coder/Vulnerabilities-and-attacks-on-information-systems-13-01-hw/blob/main/SYN-scan.png)`

![zadanie2](https://github.com/ottofonciceron-coder/Vulnerabilities-and-attacks-on-information-systems-13-01-hw/blob/main/XMAS%20scan.png)`

![zadanie2](https://github.com/ottofonciceron-coder/Vulnerabilities-and-attacks-on-information-systems-13-01-hw/blob/main/UDP%20scan.png)`

---
