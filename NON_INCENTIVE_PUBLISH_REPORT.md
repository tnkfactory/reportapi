# 비보상 매체 Report API
## 0. API KEY
   -  TNK 사이트에 연동인증키를 확인하거나 또는  담당자에게 전달 받습니다.

## 1. API URL
  - http(s)://api2.tnkfactory.com/tnk/api/report/m1

## 2. Request Parameters
   - api_key : 연동인증키
   - [app_id : TNK의 매체 APP ID] (생략하면 계정의 모든 앱이 조회됩니다.)
   - [type : 1 - 전면, 3 - 동영상, 4 - 배너), default : 1] (생략하면 전면타입이 조회됩니다.)
   - date : yyyyMMdd
   - timezone : 타임존 숫자 (예 : 9)
  - check_cd : md5([app_id] + date + timezone + api_key)

## 3. result (JSON)
  - data type:
```
{return:number,  
 report:[
     {date:"yyyyMMdd", timezone:number, app_nm:"string", app_id:number, store_id:"string", currency:"string", 
      data:[{hour:number, freq:number, fad:number, imp:number, fclick:number, vend:number,
          click:number, cost:number}, ...]}
     ...]
 }
```

  - columns

|컬럼명|내용|
|:--|:--|
  | date | 날짜 |
  | hour | 시각(24시간기준) |
  | timezone | 타임존 |
  | app_nm | 앱이름 |
  | app_id | APP ID |
  | store_id | 앱패키지명 |
  | currency | 통화 |
  | freq | 전면광고 요청수 |
  | fad | 전면광고 노출수 |
  | imp | 총 노출수 |
  | fclick | 전면 광고 클릭수 |
  | vend | 비디오 시청 완료수 |
  | click | 총 클릭수 |
  | cost | 수익금 |
  | pay_cnt | 실적건수 |
   
  - return code

|응답코드| 내용|
|:--:|:--|
|  0 | succ |
|  1 | no publisher |
|  2 | no campaign |
|  3 | request without valid check code |
|  6 | login id not exist |
|  8 | invalid parameters |

(예)
```
https://api2.tnkfactory.com/tnk/api/report/m1?api_key=xxxx&date=20160910&timezone=-12&check_cd=xxxx[&app_id=8852][&type=1]
```
