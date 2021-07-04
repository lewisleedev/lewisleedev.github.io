---
layout: post
---

보안을 생각해보면, [code-server](https://github.com/cdr/code-server)같은 물건을 서버에 직접 설치하는건 최악이다. Terminal에 접근할 수 있고, 서버 내의 모든 파일에 접근을 할 수 있게된다.

가장 좋은 방법은 아예 외부 접근을 차단하는 방법이지만, 군대에서 코딩하는게 목적이었던 나에게는 일단 불가능했다. 그래서 한동안은 비밀번호 보안만 되어있는 상태로 사용했다. 물론 https같은 기본적인 설정은 했지만, key 인증도 모자랄판에, 메인 서버에 접근할 수 있는 창구에 비밀번호만 걸어두면 다른 보안이 무슨 소용인가 싶었다. 그래서 진작에 했었어야하는 접근이지만, Docker로 설치하기로 했다.

컨테이너는 [linuxserver.io](https://www.linuxserver.io/)에서 만든 [linuxserver/code-server](https://hub.docker.com/r/linuxserver/code-server)를 사용하였다. 몇몇 다른 컨테이너들도 있었는데, 업데이트도 주기적으로 되고 문서화도 잘 되어있어서 선택했다. Documentation에 있는 docker-compose로 간단하게 만들 수 있었다.

```
---
version: "2.1"
services:
  code-server:
    image: ghcr.io/linuxserver/code-server
    container_name: code-server
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Asia/Seoul
      - PASSWORD=password #optional
      - HASHED_PASSWORD= #optional
      - SUDO_PASSWORD=password #optional
      - SUDO_PASSWORD_HASH= #optional
      - PROXY_DOMAIN=code-server.my.domain #optional
    volumes:
      - /path/to/appdata/config:/config
    ports:
      - 8443:8443
    restart: unless-stopped
```

PUID랑 PGID, 비밀번호랑 도메인정도만 바꿔주면 바로 nginx나 caddy로 reverse-proxy를 8443 포트에 설정해서 외부에서 접속/사용할 수 있다.  Password는 평문으로 하지 않고 Hash를 해줬다. 

```
printf "passwordtohash" | sha256sum | cut -d' ' -f1
```

![codeserver](/img/codeserverdocker.png)

잘 된다.


