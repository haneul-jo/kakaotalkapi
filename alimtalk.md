# 알림톡
알림톡에 관한 API들 묶음  

## 메세지
알림톡을 보내는 API에 대한 직접적인 API들

### 알림톡 목록 조회
전송된 알림톡들에 대한 목록 조회

[ HTTP ]  
```HTTP
GET /v1/messages/alimtalk/messages
```

[ Query Params ]  

Value | Type | Desc.
---|---|---
page | Int | 목록을 조회할 페이지 ( 기본값 : 0 )
dataPerPage | Int | 페이지당 데이타수 ( 기본값 : 10 )
requestID | String | 요청 ID
plusFriendId | String | 플러스 친구 ID
templateCode | String | 템플릿 코드

[ Response ]  

- Sample
```json
{
    "result": true,
    "data": [
        {
            "requestID": "20191105181258HkqCOTkIoL0",
            "plusFriendId": "@turingccc",
            "templateCode": "123",
            "recipientCount": 1,
            "requestDate": "2019-11-05T09:12:58.000Z"
        }
    ],
    "count": 1
}
```

- Format

| Value | Type | Desc.
|---|---|---
| data | Array | Data Object  
| ㄴ requestID | String | 요청 ID
| ㄴ plusFriendId | String | 플러스 친구 ID
| ㄴ templateCode | String | 템플릿 코드
| ㄴ recipientCount | Int | 메시지를 전송받을 사람수
| ㄴ requestDate | String | 메시지 전송일
| count | Int | 메시지 갯수


### 알림톡 일반 발송
알림톡을 전송하는 API

[ HTTP ]  
```HTTP
POST /v1/messages/alimtalk/messages
```

[ Request ]  

- Sample
```json
{
}
```





### 알림톡 전송 취소
아직 미발송된 발송 예약 알림톡을 취소하는 API

[ HTTP ]  
```HTTP
DELETE /v1/messages/alimtalk/messages
```

[ Request ]  

- Sample
```json
{
}
```



### 알림톡 단건 조회
조회된 목록에서 개별 단건 조회 API

[ HTTP ]  
```HTTP
GET /v1/messages/alimtalk/messages/info
```

[ Query Params ]  

Value | Type | Desc.
---|---|---
requestID | String | 요청 ID

[ Response ]  

- Sample
```json
{
    "result": true,
    "data": {
        "request": {
            "requestID": "20191105181258HkqCOTkIoL0",
            "plusFriendId": "@turingccc",
            "templateCode": "123",
            "recipientCount": 1,
            "requestDate": "2019-11-05T09:12:58.000Z",
            "isCancelable": false
        },
        "messages": [
            {
                "requestSeq": 1,
                "recipientNo": "01038332464",
                "content": "테스트(test)",
                "buttons": [
                    {
                        "name": "배송 조회",
                        "type": "DS",
                        "linkMo": null,
                        "linkPc": null,
                        "ordering": null,
                        "schemeIos": null,
                        "schemeAndroid": null
                    }
                ],
                "messageStatus": "COMPLETED",
                "requestDate": "2019-11-05T09:12:58.000Z",
                "resultCode": "1000",
                "resultCodeName": "성공"
            }
        ]
    }
}
```

- Format

| Value | Type | Desc.  
|---|---|---  
| data | Object | Data Object  
| ㄴ request | Object | Object  
| -ㄴ requestID | String | 요청 ID  
| -ㄴ plusFriendId | String | 플러스 친구 ID  
| -ㄴ templateCode | String | 템플릿 코드  
| -ㄴ recipientCount | Int | 메시지를 전송받을 사람수  
| -ㄴ requestDate | String | 메시지 전송일  
| -ㄴ isCancelable | Boolean | 취소 가능 여부  
| ㄴ messages | Array | Object  
| -ㄴ requestSeq | Int | 요청 순서
| -ㄴ recipientNo | String | 전화번호
| -ㄴ content | String | 보낸 텍스트
| -ㄴ buttons | Array | Data Array
| --ㄴ buttonsObject | [Button Object](#Button-Object) | 버튼 Object
| -ㄴ messageStatus | String | 메시지 상태
| -ㄴ requestDate | String( Date ) | 전송 요청 시간
| -ㄴ resultCode | String | 결과 코드
| -ㄴ resultCodeName | String | 결과 상태






## 템플릿
알림톡을 보내기전 템플릿을 조회 할 수 있는 API

### 템플릿 리스트 조회
템플릿 리스트를 조회하는 API

[ HTTP ]  
```HTTP
GET /v1/messages/alimtalk/template
```

[ Query Params ]  

Value | Type | Desc.
---|---|---
page | Int | 목록을 조회할 페이지 ( 기본값 : 0 )
dataPerPage | Int | 페이지당 데이타수 ( 기본값 : 10 )
requestID | String | 요청 ID
plusFriendId | String | 플러스 친구 ID
templateCode | String | 템플릿 코드




