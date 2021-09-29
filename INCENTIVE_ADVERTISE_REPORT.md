# Advertise API
## 0. API KEY
   -  TNK 사이트에 연동인증키를 확인하거나 또는  담당자에게 전달 받습니다.

## 1. API URL
  - http(s)://api2.tnkfactory.com/tnk/api/report/a1

## 2. Request Parameters
   - api_key : 연동인증키
   - [campn_id : Campaign ID] (생략하면 계정의 모든 캠페인 조회됩니다.)
   - date : yyyyMMdd
   - timezone : 타임존 숫자 (예 : 9)
  - check_cd : md5([campn_id] + date + timezone + api_key)

## 3. result (JSON)
  - data type:
```
{return:number,  
 report:[
     {date:"yyyyMMdd", timezone:number, campn_nm:"string", campn_id:number, store_id:"string", currency:"string", 
      data:[{hour:number, cost:number, click:number, pay_cnt:number}, ...]}
     ...]
 }
 ```

  - columns
   - date : 날짜
   - hour : 시각(24시간기준)
   - timezone : 타임존
   - campn_nm : 앱이름
   - campn_id : Campaign ID
   - store_id : 앱패키지명
   - currency : 통화
   - click :  광고 클릭수
   - cost : 광고비
   - pay_cnt : 전환수

   
  - return code
   - 0 : succ
   - 1 : no publisher
   - 2 : no campaign
   - 3 : request without valid check code
   - 6 : login id not exist
   - 8 : invalid parameters

(예)
```
https://api2.tnkfactory.com/tnk/api/report/a1?logn_id=xxxx&date=20190810&timezone=-12&check_cd=xxxx[&cmpn_id=8852]
```
