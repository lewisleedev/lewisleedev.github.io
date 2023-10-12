---
layout: post
---

비전공자로 시작했지만 개발자가 되겠다고 다짐을 하게 된 후부터 어느 분야에 집중해야할지 조금의 어려움을 겪기 시작했다. 분명히 마음은 개발자가 목표인데, 취미로 시작하다보니, 또 뭔갈 시작한다면 완벽히 시작하고싶다는 마음에 온갖 일을 다 벌려놓게되고, 결국 프로젝트도 중구난방, 실력도 중구난방이다.

그래도 방학기간동안에라도 어느 한 분야를 정말 제대로 배워보자는 마음에 [UNIX and Linux System Administration Handbook](https://www.amazon.com/dp/0134277554/ref=cm_sw_em_r_mt_dp_WYV88V0K0MYS85W459HS)를 읽기 시작했다. 읽기시작하던 중 재미있는 구절을 보게 되었다.

> For text editing, we strongly recommend learning vi(now seen more commonly in its enhanced form, vim) which is standard on all systems ...(중략)... Alternatively, GNU's nano is a simple and low-impact "starter editor" that has on-screen prompts. Use it discreetly; professional administratiors may be visibly distressed if they witness a peer running nano.

Homelabbing을 하다보면 하루에도 수십번 config를 만지고, 새 파일을 쓰게되고 고치게되는데, 처음 시작할 때만 해도 nano를 썼던 기억이 났다. [nano를 쓰지 말라는 건 오래 봐왔지만,](https://github.com/skilstak/nano) 이미 IDE가 익숙한 상태에서 Vi를 배울 필요성을 굳이 배우지 못했었다.

지금은 VSCode에 Neovim Extension을 사용하고있다. Nano로 할 수 있는걸 vim으로 모두 할 수 있도록 배우는데에 걸린 시간은 10분남짓이었지만, 손에 익으면 익을수록 왜 Vi를 추천하는지 알 수 있었다.

WSL에서 Neovim Extension을 사용하려면 Extension 설정에서 WSL 옵션을 체크하고 Linux(WSL)의 Neovim path를 설정해주어야한다.

```
sudo apt-get install neovim # Debian

# neovim_path = /usr/bin/neovim
```