---
layout: post
---

![Nextcloud 화면](img/nextcloud_cron.png)

Nextcloud 서버가 제대로 작동하기 위해서는 Interaction 없이, 또는 Nextcloud의 Performance를 방해하지 않으면서 몇가지 작업을 수행해주어야 한다 (Database clean-up과 같은 작업들이 해당한다). 처음에는 어차피 혼자 쓰는만큼 설정도 귀찮아 기본 제공되는 옵션 중 하나인 AJAX로 Background Job을 설정해두었었는데, 웹페이지에 방문할때마다 실행되는 특성상 몇일 밀릴 수도 있고 해서 그렇게 좋은 방법은 아니었다. 특히 External storage를 써야한다면 Cron을 사용하는 것이 좋다. Webcron을 사용하는 방법도 있는데, Webserver의 제약으로 이또한 좋은 방법이 아니라고 한다.

보통 이런 Background job은 ```cron```을 사용하게되는데, 문제는 Nextcloud official Docker image에는 crontab이 설치가 안돼있다. 설치를 해서 쓸 수도 있겠지만, Host에서 ```docker exec```을 통해 실행하는 것으로 해결했다.

![crontab](img/nextcloud_cron_ascii.gif)

```
*/5 * * * * docker exec -u www-data [nextcloud 컨테이너 이름] php cron.php # Debian(OMV) 기준
```