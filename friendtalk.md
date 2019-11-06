# 친구톡
친구톡에 관한 API들 묶음  

## 이미지
친구톡을 보내기 위한 사전 이미지업로드용 API  

---

### 이미지 업로드
친구톡용 이미지 업로드 API

```
❗️해당 API는 파일 업로드를 해야 하므로,
`Content-Type: multipart/form-data` 헤더를 사용하여야만 한다.
```

[ HTTP ]  
```HTTP
POST /v1/messages/friendtalk/image
```

[ Request ]  

Value | Type | Desc.
---|---|---
image | File | 업로드할 이미지

- Format

| Value | Type | Desc.  
|---|---|---  
| imageSeq | Int | 이미지 고유 번호
| imageUrl | String | Kakao 이미지 URL
| imageName | String | 이미지 파일명  

---

### 이미지 파일 리스트
현재 등록된 이미지 파일 목록 API

[ HTTP ]  
```HTTP
GET /v1/messages/friendtalk/image
```

[ Response ]  

- Sample
```json
{
    "result": true,
    "list": [
        {
            "imageSeq": 529,
            "imageName": "animals.jpg",
            "imageUrl": "http://mud-kage.kakao.com/dn/bwRYK9/btqx3H1Spvi/kle1K5hNP0plkrr72wM7T0/img_l.jpg"
        },
        {
            "imageSeq": 553,
            "imageName": "puppy.jpg",
            "imageUrl": "http://mud-kage.kakao.com/dn/S7Jqz/btqya5nhugz/kLlxkO7VuClDjwkl3CneGK/img_l.jpg"
        },
        {
            "imageSeq": 555,
            "imageName": "fox.jpg",
            "imageUrl": "http://mud-kage.kakao.com/dn/bLcaNL/btqx7OgIsOH/TvR66vgU7JczOG6mA4JSmK/img_l.jpg"
        }
    ]
}
```

- Format

| Value | Type | Desc.
|---|---|---
| list | Array | Data Object  
| ㄴ imageSeq | Int | 이미지 고유 번호
| ㄴ imageName | String | 이미지 파일명
| ㄴ imageUrl | String | Kakao 이미지 URL

---




### 이미지 삭제
등록된 이미지를 삭제하는 API

[ HTTP ]  
```HTTP
DELETE /v1/messages/friendtalk/image
```

[ Request ]  

- Sample
```json
{
    "imageSeq":582
}
```

| Value | Type | Desc.
|---|---|---
| imageSeq | Int | 이미지 고유 번호

---




## 메시지
친구톡을 실제로 전송처리하는 API  

---

### 친구톡 발송
친구톡을 발송하는 APi

[ HTTP ]  
```HTTP
POST /v1/messages/friendtalk/messages
```

[ Request ]  

- Sample
```json
{
}
```



---

### 친구톡 발송 목록 조회
발송요청한 친구톡 목록 API

[ HTTP ]  
```HTTP
GET /v1/messages/friendtalk/messages
```

[ Query Params ]  

Value | Type | Desc.
---|---|---
page | Int | 목록을 조회할 페이지 ( 기본값 : 0 )
dataPerPage | Int | 페이지당 데이타수 ( 기본값 : 10 )
requestID | String | 요청 ID
plusFriendId | String | 플러스 친구 ID
Period | Array | 기간 배열
ㄴ 0 | String | 시작
ㄴ 1 | String | 종료

[ Sample ]

```Javascript
CallAjax("get", "/messages/friendtalk/messages", {
    "plusFriendId": "@turingccc",
    "Period": ["2019-08-15","2019-09-15"]
}, console.log );
```

```BASH
cURL \
-H "Content-Type: application/json" \
-H "Authorization: Bearer sd9dsjsdlkfldkjvdlkslk" \
https://api.cloudturing.com/v1/messages/friendtalk/messages?page=1&dataPerPage=10&Period%5B%5D=2019-11-04&Period%5B%5D=2019-11-09 
```

[ Response ]  

- Sample
```json
{
    "result": true,
    "data": [
        {
            "requestID": "20191107155700WODs9CSyhZ0",
            "plusFriendId": "@turingccc",
            "recipientCount": 1,
            "requestDate": "2019-11-07T06:57:00.000Z"
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
| ㄴ recipientCount | Int | 메시지를 전송받을 사람수
| ㄴ requestDate | String | 메시지 전송일
| count | Int | 메시지 갯수








---

### 친구톡 발송 취소
예약발송된 친구톡 발송 취소

[ HTTP ]  
```HTTP
DELETE /v1/messages/friendtalk/messages
```

[ Request ]  

- Sample
```json
{
    "requestID":"20191107155700WODs9CSyhZ0"
}
```

| Value | Type | Desc.
|---|---|---
| requestID | String | 요청 ID  



---

### 친구톡 단건 조회
개별 메시지 조회 

[ HTTP ]  
```HTTP
GET /v1/messages/friendtalk/messages/info
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
            "requestID": "20191107155700WODs9CSyhZ0",
            "plusFriendId": "@turingccc",
            "recipientCount": 1,
            "requestDate": "2019-11-07T06:57:00.000Z",
            "isCancelable": false
        },
        "messages": [
            {
                "requestSeq": 1,
                "recipientNo": "01038332464",
                "content": "sdfsdfsdfsdf",
                "buttons": [],
                "messageStatus": "CANCEL",
                "requestDate": "2019-11-07T06:57:00.000Z",
                "resultCode": null,
                "resultCodeName": null
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
