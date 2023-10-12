---
layout: post
categories: ko
---

Homelab을 구축하고나서 가장 신경쓰였던 것은 보안이었다. 물론 나만쓰는 작은 개인 서버지만, 일반 가정 네트워크를 사용하는 이상 보안에 취약할 수 밖에 없다. 거기에 자취방에 서버를 돌려두기 어려워 멀리 떨어져있는 곳에 서버가 있는 바람에, 특히나 보안설정은 하나하나를 조심히 만져야한다. SSH가 잠겨버리기라도하면 몇일동안 아무 조치를 못하고 기다려야한다.

그래서 선택한 것이 [Zerotier](https://www.zerotier.com/)였다. 여러번 써봤지만, 가장 적절한 사용처에 사용할 기회가 생겼다. 먼저 ufw로 Zerotier Network 밖에서 들어오는 연결을 전부 차단시켰다.

```
$ curl -s https://install.zerotier.com | sudo bash

# Setting up Zerotier...

$ sudo ufw default deny incoming
$ sudo ufw default allow outgoing

$ sudo ufw allow from (zerotier_subnet) to any port (your_needed_port)
$ ...
```

![homelab diagram](img/homelab_diagram.png)

[Docker Container는 기본적으로 iptable을 무시한다](https://degreesofzero.com/article/docker-and-firewalls.html). 이것은 Docker-compose 단계에서 (Portainer를 사용했따) Port를 ```127.0.0.1:<port>:<port>``` 또는 ```(zerotier_io):<port>:<port>``` 이런식으로 Forwarding하는 것으로 해결했다. 몇가지 방법이 있었지만, 컨테이너 내부에서 인터넷 연결이 안되는 등의 문제가 발생해 가장 직관적인 방법을 택했다.

![homer dashboard](img/homer_dashboard.png)

이후 Homer를 설치해 Docker Container들을 위한 Dashboard를 구축하였다. Containers간에 통신도 원활했고, 전체적으로 큰 문제가 없었다. 앞으로 더 재밌는 selfhosting app들로 채우고싶어졌다.
