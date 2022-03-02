# PING
## Теоретическая часть

## Задача
Написать собственную утилиту ping
```shell
ping ya.ru
PING ya.ru (87.250.250.242) 56(84) bytes of data.
64 bytes from ya.ru (87.250.250.242): icmp_seq=1 ttl=246 time=9.54 ms
64 bytes from ya.ru (87.250.250.242): icmp_seq=2 ttl=246 time=12.2 ms
64 bytes from ya.ru (87.250.250.242): icmp_seq=3 ttl=246 time=9.92 ms
^C
--- ya.ru ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2004ms
rtt min/avg/max/mdev = 9.541/10.559/12.222/1.185 ms

```

```shell
Usage
  ping [options] <destination>

Options:
  <destination>      dns name or ip address
  -c <count>         stop after <count> replies
  -D                 print timestamps
  -d                 use SO_DEBUG socket option
  -f                 flood ping
  -h                 print help and exit
  -i <interval>      seconds between sending each packet
  -L                 suppress loopback of multicast packets
  -l <preload>       send <preload> number of packages while waiting replies
  -m <mark>          tag the packets going out
  -q                 quiet output
  -s <size>          use <size> as number of data bytes to be sent
  -v                 verbose output
  -V                 print version and exit
  -w <deadline>      reply wait <deadline> in seconds
  -W <timeout>       time to wait for response
```

### Потенциальные языки
- C/C++
- Потенциальные библиотеки:
  - Boost::Asio
  - Asio standalone
  - POCO (для отмороженных)
  - CURL
### Требования к утилите
- Наличие консольного API
- Возможность установки программы с помощью .msi или .exe
- Ограничения по времени

## Тесты
Необходимо протестировать утилиту на общедоступных сайтах (google.com, ya.ru, etc)
