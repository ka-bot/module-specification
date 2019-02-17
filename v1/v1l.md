# v1l

카카오톡 봇 `v1l` 모듈 명세를 정의합니다.



## 어디에 사용하나요?

**다른 모듈이 사용할 라이브러리**를 만들 때 이 타입의 모듈을 쓰면 됩니다.



## 어떻게 사용되나요?

```javascript
var v1l = {};
var _ = {};
// ... 생략
let m = new Function("shared", readFile(path))(_);
if(m)
{
    v1l[name] = m;
}
// ... 생략
```

이런 비슷한 방법으로 로드됩니다.



## 어떻게 만드나요?

```javascript
let lt = {};

function send_ok(id)
{
    if(!lt[id]) lt[id] = 0;
    var now = Date.now();
    var deltaTime = now - lt[room];
    if(deltaTime > 1000)
    {
        lt[id] = now;
        return true;
    }
}

return response;
```

인사 봇에 쓸 라이브러리 모듈 예입니다.



return된 값이 `false`이면 모듈을 로드하지 못한 것으로 간주합니다.



다른 모듈이 사용할 수 있게 함수나 객체를 return해 주세요.



`module.json` 파일 예시입니다.

```javascript
{
    "name" : "hello",
    "type" : "v1l",
    "version" : "1.0",
    "filename" : "script.js"
}
```

`script.js`는 위 스크립트 파일 이름 예시입니다.

