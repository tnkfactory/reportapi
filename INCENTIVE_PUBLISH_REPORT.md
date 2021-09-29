# Publisher API
## 0. API KEY
   -  TNK 사이트에 연동인증키를 확인하거나 또는  담당자에게 전달 받습니다.

## 1. API URL
  - http(s)://api2.tnkfactory.com/tnk/api/report/p1

## 2. Request Parameters
   - api_key : 연동인증키
   - [app_id : TNK 매체 APP ID] (생략가능 - 지정하지 않으면 계정의 모든 앱이 조회됩니다.)
   - date : yyyyMMdd
   - timezone : 타임존 숫자 (예 : 9)
  - check_cd : md5([app_id] + date + timezone + api_key)

## 3. result (JSON)
  - data type:
 ```
{return:number,  
 report:[
     {date:"yyyyMMdd", timezone:number, app_nm:"string", app_id:number, store_id:"string", currency:"string", 
      data:[{hour:number, imp:number, click:number, pay_cnt:number, cost:number}, ...]}
     ...]
 }
```
  - columns
 ```
  date : 날짜
  hour : 시각(24시간기준)
  timezone : 타임존
  app_nm : 앱이름
  app_id : APP ID
  store_id : 앱패키지명
  currency : 통화
  imp : 노출수
  click : 클릭수
  pay_cnt : 실적수
  cost :수익금
```
   
  - return code
```
 0 : succ
 1 : no publisher
 2 : no campaign
 3 : request without valid check code
 6 : login id not exist
 8 : invalid parameters
```

(예)
```
https://api2.tnkfactory.com/tnk/api/report/p1?api_key=xxxx&date=20160910&timezone=-12&check_cd=xxxx[&app_id=8852]
```
