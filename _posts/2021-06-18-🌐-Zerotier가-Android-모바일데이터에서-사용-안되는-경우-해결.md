---
layout: post
---

Zerotier를 항상 쓰고싶었는데, 이상하게 안드로이드(S10e)에서는 제대로 쓸 수가 없었다. 정확히는 Zerotier 네트워크에는 접근 가능했지만, 인터넷 연결이 끊겼다. 무슨 인트라넷/인터넷 혼선 금지도아니고 매우 불편했다. 그러던 중 해결법을 찾았다.

![Zerotier Solution](img/zerotiersolved.png)

> ZeroTier RFC4193 (/128 for each device)

이 설정을 켜주면 된다. IPV6 할당의 문제였던 것 같다. 설정을 켜주자마자 거짓말같이 잘 됐다.