# v1g

카카오톡 봇 `v1g` 모듈 명세를 정의합니다.



## 어디에 사용하나요?

**모든 방에 적용할 기능**을 만들 때 이 타입의 모듈을 쓰면 됩니다.



## 어떻게 사용되나요?

```javascript
var v1g = [];
var _ = {};
// ... 생략
let m = new Function(readFile(path))();
if(m) v1g.push(m);
// ... 생략
function response(room, msg, sender, isGroupChat, replier, imageDB)
{
    let i;
    while(i < v1g.length && !v1g[i](
        room, msg, sender, isGroupChat, replier, imageDB, _)) i++;
}
```

이런 비슷한 방법으로 로드/사용됩니다.



## 어떻게 만드나요?

```javascript
let lt = 0;

function response(r, msg, sender, g, replier, d, shared)
{
    if(msg == "안녕하세요")
    {
        var now = Date.now();
        var deltaTime = now - lt;
        if(deltaTime > 1000)
        {
            replier.reply(sender + "님 안녕하세요!");
            lt = now;
        }
        return true;
    }
}

return response;
```

인사 봇 예시입니다. `response`로 쓸 함수를 return해 주세요.

반환값이 `false`이면 모듈을 로드하지 못한 것으로 간주합니다.

