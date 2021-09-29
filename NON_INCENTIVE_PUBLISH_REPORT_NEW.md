# NON-INCENTIVE PUBLISH API (NEW)
## 0. API KEY
   -  TNK 사이트에 연동인증키를 확인하거나 또는  담당자에게 전달 받습니다.

## 1. API URL
  - http(s)://pub.tnkad.net/pub/api/report/m1

## 2. Request Parameters
   - api_key : 연동인증키
   - [app_id : TNK의 매체 APP ID(INVENTORY_ID)] (생략하면 계정의 모든 앱이 조회됩니다.)
   - date : yyyyMMdd
   - timezone : 타임존 숫자 (예 : 9)
  - check_cd : md5([app_id] + date + timezone + api_key)

## 3. result (JSON)
  - data type:
```
{return : 0 (number)
 report:[
     {date:"yyyyMMdd", timezone:number, app_nm:"string", app_id:number, currency:"string", 
      data:[{hour:number, imp:number, click:number, cost:number}, ...]}
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
| currency | 통화 |
| imp | 노출수 |
| click | 클릭수 |
| cost | 수익금 |
   
  - return code

|응답코드| 내용|
|:--:|:--|
|  0 | succ |
|  1 | no publisher |
|  2 | wrong apikey |
|  3 | invalid parameters |
|  4 | request without valid check code |

(예)
```
https://pub.tnkad.net/pub/api/report/m1?api_key=xxx&date=20210924&timezone=9&check_cd=xxx[&app_id=8]
```
