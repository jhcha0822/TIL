# JSON

### 필요성

형식이 없고 구조화되어 있지 않은 데이터를 해석하기 쉽지 않다.

- SGML(태그)
    - HTML: how to design
    - XML: 데이터를 표현 --> JSON

JSON과 XML은 서버로부터 데이터를 받기 위한 양식

> 아래 내용은 일부 W3 Schools.com 에서 발췌

``` JSON
{"employees":[
  { "firstName":"John", "lastName":"Doe" },
  { "firstName":"Anna", "lastName":"Smith" },
  { "firstName":"Peter", "lastName":"Jones" }
]}
```

```XML
<employees>
  <employee>
    <firstName>John</firstName> <lastName>Doe</lastName>
  </employee>
  <employee>
    <firstName>Anna</firstName> <lastName>Smith</lastName>
  </employee>
  <employee>
    <firstName>Peter</firstName> <lastName>Jones</lastName>
  </employee>
</employees>
```

    공통점
    - self describing (human readable)
    - 구조적 (values within values)
    - 여러 프로그래밍 언어로 파싱 가능
    - XMLHttpRequest로 패치될 수 있음

    차이점
    - JSON은 end tag를 사용하지 않음
    - JSON이 더 짧음
    - JSON이 읽고 쓰기 더 쉬움
    - JSON은 배열 사용 가능

    - XML은 XML parser를 사용해야 하나,
    - JSON은 standard JavaScript function을 이용해 파싱 가능

## JSON

> JavaScript Object Noation

JSON: JavaScript의 object(객체) 표기법으로 이루어져 있음. 데이터 표현 문자열로 key와 value의 쌍으로 구성됨

```JSON
{
    "key" : value
}
```

순수 문자열이지만 객체를 표현하기 위한 구문으로 구조화 되어 있으므로 이 기종 간 데이터를 받기 위한 용도로 활용됨

### JSON 내장객체

자바스크립트를 포함한 일반적인 프로그래밍 언어에서 JSON은 문자열로 처리되어야 하나, 자바스크립트의 경우 JSON 내장 객체를 이용하면 문자열을 객체로 변환해 준다.

JSON 문자열을 JS객체로 변환해주는 메서드는 ```JSON.parse()``` 메서드이다.

또한 이 반대의 기능을 하는 JS객체를 JSON 문자열로 변환해주는 기능은 ```JSON.stringify()``` 메서드이다.