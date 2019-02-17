# v1r

카카오톡 봇 `v1r` 모듈 명세를 정의합니다.



## 어디에 사용하나요?

**특정 방에만 적용할 기능**을 만들 때 이 타입의 모듈을 쓰면 됩니다.



## 어떻게 사용되나요?

```javascript
var v1r = {};
var _ = {};
// ... 생략
let m = new Function("shared", readFile(path))(_);
if(m)
{
    let rooms = getRooms(name);
    for(let i = 0; i < rooms.length; i++)
    {
        if(v1r[rooms[i]]) v1r[rooms[i]] = [];
        v1r[rooms[i]].push(m);
    }
}
// ... 생략
function response(room, msg, sender, isGroupChat, replier, imageDB)
{
    let i;
    while(i < v1r[room.trim()].length && !v1r[room.trim()][i](
        room, msg, sender, isGroupChat, replier, imageDB)) i++;
}
```

이런 비슷한 방법으로 로드/사용됩니다.



## 어떻게 만드나요?

```javascript
let lt = {};

function response(room, msg, sender, g, replier, d)
{
    if(msg == "안녕하세요")
    {
        if(!lt[room]) lt[room] = 0;
        var now = Date.now();
        var deltaTime = now - lt[room];
        if(deltaTime > 1000)
        {
            replier.reply(sender + "님 안녕하세요!");
            lt[room] = now;
        }
        return true;
    }
}

return response;
```

인사 봇 예시입니다. `response`로 쓸 함수를 return해 주세요.



return된 값이 `false`이면 모듈을 로드하지 못한 것으로 간주합니다.



return된 함수는 true나 false를 return해야 합니다.

메시지를 처리 완료해서 다른 모듈이 더 처리하지 않기를 원한다면 `true`를,

다른 모듈이 그 메시지를 이어서 처리하게 하려면 `false`를 return하면 됩니다.



`module.json` 파일 예시입니다.

```javascript
{
    "name" : "hello",
    "type" : "v1r",
    "version" : "1.0",
    "filename" : "script.js"
}
```

`script.js`는 위 스크립트 파일 이름 예시입니다.

