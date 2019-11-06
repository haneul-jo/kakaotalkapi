# 친구톡
친구톡에 관한 API들 묶음  

## 이미지
친구톡을 보내기 위한 사전 이미지업로드용 API  

### 이미지 업로드
친구톡용 이미지 업로드 API

[ HTTP ]  
```HTTP
POST /v1/messages/friendtalk/image
```

[ Request ]  

- Sample
```json
{
}
```




### 이미지 파일 리스트
현재 등록된 이미지 파일 목록 API

[ HTTP ]  
```HTTP
GET /v1/messages/friendtalk/image
```

[ Query Params ]  

Value | Type | Desc.
---|---|---
page | Int | 목록을 조회할 페이지 ( 기본값 : 0 )
dataPerPage | Int | 페이지당 데이타수 ( 기본값 : 10 )
requestID | String | 요청 ID
plusFriendId | String | 플러스 친구 ID
templateCode | String | 템플릿 코드





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
}
```




## 메시지
친구톡을 실제로 전송처리하는 API  

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
templateCode | String | 템플릿 코드




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
}
```




### 친구톡 단건 조회
개별 메시지 조회 

[ HTTP ]  
```HTTP
GET /v1/messages/friendtalk/messages/info
```

[ Query Params ]  

Value | Type | Desc.
---|---|---
page | Int | 목록을 조회할 페이지 ( 기본값 : 0 )
dataPerPage | Int | 페이지당 데이타수 ( 기본값 : 10 )
requestID | String | 요청 ID
plusFriendId | String | 플러스 친구 ID
templateCode | String | 템플릿 코드
