# Object

## Button Object

```json
{
    "ordering" : Integer,
    "type" : String,
    "name" : String,
    "linkMo" : String,
    "linkPc" : String,
    "schemeIos" : String,
    "schemeAndroid" : String
}
```

Value | Type | Desc.
---|---|---
ordering | Integer | 버튼 순서(1~5)
type | String | 버튼 타입(WL:웹링크, AL:앱링크, DS:배송 조회, BK:봇 키워드, MD:메시지 전달)
name | String | 버튼 이름 (버튼이 있는 경우 필수, 최대 14자)
linkMo | String | 모바일 웹 링크 (WL 타입일 경우 필수 필드, 최대 200자)
linkPc | String | PC 웹 링크 (WL 타입일 경우 선택 필드, 최대 200자)
schemeIos | String | IOS 앱 링크 (AL 타입일 경우 필수 필드, 최대 200자)
schemeAndroid | String | Android 앱 링크 (AL 타입일 경우 필수 필드, 최대 200자)






