# Notes

How to recreate, in theory:

```sh
/workspaces/gluetun master ❯ ping 1.1.1.1 -c 3
PING 1.1.1.1 (1.1.1.1): 56 data bytes
64 bytes from 1.1.1.1: seq=0 ttl=63 time=15.637 ms
64 bytes from 1.1.1.1: seq=1 ttl=63 time=21.831 ms
64 bytes from 1.1.1.1: seq=2 ttl=63 time=23.036 ms

--- 1.1.1.1 ping statistics ---
3 packets transmitted, 3 packets received, 0% packet loss
round-trip min/avg/max = 15.637/20.168/23.036 ms
/workspaces/gluetun master ❯ iptables -A OUTPUT -d 1.1.1.1 -j REJECT
/workspaces/gluetun master ❯ ping 1.1.1.1 -c 3
PING 1.1.1.1 (1.1.1.1): 56 data bytes
ping: sendto: Operation not permitted
/workspaces/gluetun master ❯ iptables -D OUTPUT -d 1.1.1.1 -j REJECT
/workspaces/gluetun master ❯ ping 1.1.1.1 -c 3
PING 1.1.1.1 (1.1.1.1): 56 data bytes
64 bytes from 1.1.1.1: seq=0 ttl=63 time=15.544 ms
64 bytes from 1.1.1.1: seq=1 ttl=63 time=21.445 ms
64 bytes from 1.1.1.1: seq=2 ttl=63 time=22.651 ms

--- 1.1.1.1 ping statistics ---
3 packets transmitted, 3 packets received, 0% packet loss
round-trip min/avg/max = 15.544/19.880/22.651 ms
```
