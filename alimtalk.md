# 알림톡
알림톡에 관한 API

* [알림톡](#알림톡)
    * [메세지](#메세지)
        * [알림톡 목록 조회](#알림톡-목록-조회)
        * [알림톡 일반 발송](#알림톡-일반-발송)
        * [알림톡 전송 취소](#알림톡-전송-취소)
        * [알림톡 단건 조회](#알림톡-단건-조회)
    * [템플릿](#템플릿)
        * [템플릿 리스트 조회](#템플릿-리스트-조회)
* [Object](./object.md#Object)
    * [Button Object](./object.md#Button-Object)
* Appendix
    * [템플릿 상태 코드](#템플릿-상태-코드)

# 메세지
알림톡을 보내는 API에 대한 직접적인 API들

## 알림톡 목록 조회
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

## 알림톡 일반 발송
알림톡을 전송하는 API

[ HTTP ]  
```HTTP
POST /v1/messages/alimtalk/messages
```

[ Request ]  

- Sample
```json
{
    "plusFriendId":"@turingccc",
    "templateCode":"123",
    "recipientList":[{
        "recipientNo":"01038332464"
    }]
}
```

| Value | Type | Desc.
|---|---|---
| plusFriendId | String | 플러스 친구 ID
| templateCode | String | 템플릿 코드
| recipientList | Array | 수신자 목록
| ㄴ recipientNo | String | 수신자 전화번호

## 알림톡 전송 취소
아직 미발송된 발송 예약 알림톡을 취소하는 API

[ HTTP ]  
```HTTP
DELETE /v1/messages/alimtalk/messages
```

[ Request ]  

- Sample
```json
{
    "requestID":"20191107125900h7w2PraIiX0"
}
```

| Value | Type | Desc.
|---|---|---
| requestID | String | 요청 ID  


## 알림톡 단건 조회
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
| -ㄴ recipientCount | Int | 수신자 사람수  
| -ㄴ requestDate | String | 메시지 전송일  
| -ㄴ isCancelable | Boolean | 취소 가능 여부  
| ㄴ messages | Array | Object  
| -ㄴ requestSeq | Int | 요청 순서
| -ㄴ recipientNo | String | 수신자 전화번호
| -ㄴ content | String | 보낸 텍스트
| -ㄴ buttons | Array | Data Array
| --ㄴ buttonsObject | [Button Object](./object.md#Button-Object) | 버튼 Object
| -ㄴ messageStatus | String | 메시지 상태
| -ㄴ requestDate | Date String | 전송 요청 시간
| -ㄴ resultCode | String | 결과 코드
| -ㄴ resultCodeName | String | 결과 상태

# 템플릿
알림톡을 보내기전 템플릿을 조회 할 수 있는 API

## 템플릿 리스트 조회
템플릿 리스트를 조회하는 API

[ HTTP ]  
```HTTP
GET /v1/messages/alimtalk/template
```

[ Query Params ]  

Value | Type | Desc.
---|---|---
plusFriendId | String | 플러스 친구 ID  
templateCode | String | 템플릿 코드
templateName | String | 템플릿 이름
status | String | [템플릿 상태 코드](#템플릿-상태-코드)

[ Response ]  

- Sample
```json
{
    "result": true,
    "data": [
        {
            "plusFriendId": "@turingccc",
            "statusName": "승인",
            "templateCode": "RESERVE",
            "templateName": "예약",
            "buttons": [
                {
                    "name": "꿈많은청년들",
                    "type": "WL",
                    "linkMo": "https://place.map.kakao.com/1314556653",
                    "linkPc": "https://place.map.kakao.com/1314556653",
                    "ordering": null,
                    "schemeIos": null,
                    "schemeAndroid": null
                }
            ],
            "templateContent": "[#{이름}]님의 예약이 [#{시간}]에 예약되었습니다.",
            "status": "TSC03",
            "createdAt": "2019-08-29T07:58:22.000Z"
        }
    ]
}
```

- Format

| Value | Type | Desc.  
|---|---|---  
| data | Object | Data Object  
| -ㄴ plusFriendId | String | 플러스 친구 ID  
| -ㄴ statusName | String | 템플릿 상태 이름
| -ㄴ templateCode | String | 템플릿 코드  
| -ㄴ templateName | String | 템플릿 명  
| -ㄴ buttons | Array | Data Array
| --ㄴ buttonsObject | [Button Object](./object.md#Button-Object) | 버튼 Object
| -ㄴ templateContent | String | 템플릿 텍스트 내용
| -ㄴ status | String | [템플릿 상태 코드](#템플릿-상태-코드)
| -ㄴ createdAt | Date String | 생성 시간

## 템플릿 상태 코드

Code | 코드명
---|---
TSC01 | 요청
TSC02 | 검수중
TSC03 | 승인
TSC04 | 반려
