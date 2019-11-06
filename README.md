# 꿈많은청년들 : KakaoTalk 알림톡/친구톡 API 문서

## 개요

카카오톡 알림톡/친구톡 API 문서입니다. 꿈많은청년들에서 제공하는 version 1.0 알림톡/친구톡입니다.

```
❗️WARNNING: 본 문서는 향후 v2.0 이 출시되면 단계적으로 Deprecate 될 수 있습니다.
v2.0이 출시되면 다양한 방법을 통해 공지할 계획입니다.
```


---

## 계정 생성
https://cloudturing.com 을 통해서 가입후 영업담당자를 통해 승인을 받습니다.

카카오톡 프로필을 등록후 키를 발급 받습니다.

## Webhook / API 작성 방법
* 통신간에는 특별한 암호화 없이 동작하므로 모든 API는 HTTPS를 이용해서 통신해야만 합니다.
* 기본 주소는 https://api.cloudturing.com/v1 으로 시작하게 됩니다.
* 테스트는 cURL을 이용해 주시기 바랍니다.
* 제공되는 샘플 코드는 현재 cURL만 제공하고 있습니다. 이 부분 양해해 주시기 바랍니다.

---

## API 목록
* [알림톡](./alimtalk.md#알림톡)
    * [메세지](./alimtalk.md#메세지)
        * [알림톡 목록 조회](./alimtalk.md#알림톡-목록-조회)
        * [알림톡 일반 발송](./alimtalk.md#알림톡-일반-발송)
        * [알림톡 전송 취소](./alimtalk.md#알림톡-전송-취소)
        * [알림톡 단건 조회](./alimtalk.md#알림톡-단건-조회)
    * [템플릿](./alimtalk.md#템플릿)
        * [템플릿 리스트 조회](./alimtalk.md#템플릿-리스트-조회)
* [친구톡](#친구톡)
    * [이미지](#이미지)
        * [이미지 업로드](#이미지-업로드)
        * [이미지 파일 리스트](#이미지-파일-리스트)
        * [이미지 삭제](#이미지-삭제)
    * [메시지](#메시지)
        * [친구톡 발송](#친구톡-발송)
        * [친구톡 발송 목록 조회](#친구톡-발송-목록-조회)
        * [친구톡 발송 취소](#친구톡-발송-취소)
        * [친구톡 단건 조회](#친구톡-단건-조회)

---

## API 상세 설명

📣`공통`  
```baseURL : https://api.cloudturing.com/v1  
Default Content-Type : application/json
모든 통신은 `UTF-8` 로 이루어집니다.  
통신시 `Header`에는 `Authorization`를 이용하여 발급된 키를 첨부 하여야 합니다.
```

GET/POST/DELETE :  
`Content-Type : application/json`  
File Upload 의 경우에만   
`Content-Type: multipart/form-data`

---

## 친구톡
친구톡에 관한 API들 묶음  

### 이미지
친구톡을 보내기 위한 사전 이미지업로드용 API  

#### 이미지 업로드
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




#### 이미지 파일 리스트
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





#### 이미지 삭제
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




### 메시지
친구톡을 실제로 전송처리하는 API  

#### 친구톡 발송
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




#### 친구톡 발송 목록 조회
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




#### 친구톡 발송 취소
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




#### 친구톡 단건 조회
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


# Optional

## Button Object
준비중...

Value | Type | Desc.
---|---|---
page | Int | 목록을 조회할 페이지 ( 기본값 : 0 )
dataPerPage | Int | 페이지당 데이타수 ( 기본값 : 10 )
requestID | String | 요청 ID
plusFriendId | String | 플러스 친구 ID
templateCode | String | 템플릿 코드

# Error Code

# Result Code
