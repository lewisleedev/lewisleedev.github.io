---
layout: post
---

Caddy도 Basic Auth를 지원한다. 웹사이트를 일반적으로 접근 불가능하게 만들기 위해서 간단하게 사용할 수 있는 방법중 하나이다. HTTP 프로토콜 자체 Authentication 규격인데, https가 아니라면 인증 정보를 **평문**으로 보내기때문에 좋은 보안수단은 못된다. 유일한 보안수단으로는 더더욱 나쁘다. 실제 Production에서 Basic Auth만을 사용할 일은 없다고 보면 될 것 같다.

먼저 비밀번호 해시값을 만들어낸다. Caddy 내에서 간단하게 만들 수 있다.

```
$ caddy hash-password
$ Enter password: []
$ Confirm password: []
$ JDJhJDE0JE5KNUY2UUg4Lk1SQWxTTzg2ODZqci5FRFEwTTBRZTh4cTJ0a0F5RlE0a2twQ0wzc2hBWUlD
```

해시값을 복사해놓은 후, Caddyfile에 다음과같이 basicauth 블록을 추가한다.

```
# Caddyfile

example.com {
    reverse_proxy: localhost:8080

    basicauth {
        admin(사용자이름) JDJhJDE0JE5KNUY2UUg4Lk1SQWxTTzg2ODZqci5FRFEwTTBRZTh4cTJ0a0F5RlE0a2twQ0wzc2hBWUlD(해시값)
    }
}

```

adapt&reload한 후 웹사이트에 접속하면 인증화면을 볼 수 있다.

![basic auth](img/basicauth.png)

### Read more

[Caddy Official Document](https://caddyserver.com/docs/caddyfile/directives/basicauth)