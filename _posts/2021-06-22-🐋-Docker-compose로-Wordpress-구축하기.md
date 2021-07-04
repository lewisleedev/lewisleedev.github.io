---
layout: post
---

워드프레스같은건 설치하기 쉬운건 맞지만, 귀찮은 구석이 많다. php설정부터 db, 웹서버 등등 설정해줄 것이 한두개가 아니다. 특히 php부분은 잘못하면 에러도 많이나는 부분이라 더욱 귀찮다.

워드프레스도 역시 Docker-compose로 설치 가능하다.

```
# docker-compose.yml

version: "3.9"
    
services:
  db:
    image: mysql:5.7
    volumes:
      - ./db:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: [비밀번호]
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: [비밀번호]
    
  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    volumes:
      - ./wp/:/var/www/html
    ports:
      - "8000:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: [비밀번호]
      WORDPRESS_DB_NAME: wordpress
```

```
$ ls
$ docker-compose.yml
$ docker-compose up -d
```

localhost:8000으로 접속하면 워드프레스 설정페이지를 볼 수 있다. 보통 Wordpress를 사용하면 Nginx를 많이 사용하게되는데, Docker를 사용하면 복잡하게 php설정을 해줄필요없이 Caddy로 reverse-proxy만 해주면된다.

```
# Caddyfile

example.com {
    localhost:8000
}
```

Wordpress의 간단한 개발이 목적이라면 Docker만큼 편한 툴이 없을 것이다. Production에 사용하는 것은 대체로 추천하지 않는 듯 하다. 큰 문제는 없을 수 있지만, 워드프레스는 그 특성상 내부 파일들이 가변적인데, 이런 가변적인 파일들을 volume으로 넣어야 하는 것이 Docker답지 못하다는 것이다.