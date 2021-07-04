---
layout: post
---

Disqus, Commento같은 많은 댓글 임베드 서비스가 있지만, 댓글창이 아예 없는 블로그들을 많이 보았다. 대개 이메일을 적어두는 선에서 끝나는데, 특이하게 Github Issue를 열라고 알려주는 블로그를 본 적이 있었다. 생각해보면 Github repository로 만들어진 블로그라면, Issue 기능만큼 적절한 의견의 장이 없다. 그렇다고해서 Issue를 링크로 걸기에는 뭔가 아쉬운 점이 많았다.

그러던중 [utterances](https://github.com/utterance/utterances)를 발견했다. Github Issue를 자동으로 만들어주고, 포스트 안에 자동으로 댓글 형식으로 보여준다. 

![utterances](/img/utterances.png)

사용법도 아주 간단하다. 먼저 [utterances Github app](https://github.com/apps/utterances)을 설치해주고, [utterances.es](https://utteranc.es/) 웹사이트에서 필요에 맞게 설정한 후, 마지막 스크립트를 페이지의 원하는 곳에 붙여넣기만 하면된다. Github Pages 기반의 웹사이트에서만 작동한다. 자동으로 Issue를 찾아주고, 없으면 만들어주기때문에 추가적인 설정도 필요없다.