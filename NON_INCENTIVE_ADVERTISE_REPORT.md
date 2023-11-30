# 비보상형 광고 Report API (사용중지)
## 0. API KEY
   -  TNK 사이트에 연동인증키를 확인하거나 또는  담당자에게 전달 받습니다.

## 1. API URL
  - http(s)://api2.tnkfactory.com/tnk/api/report/c1

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
      data:[{hour:number, imp:number, click:number, conversion:number, cost:number, vdo_start:numnber}, ...]}
     ...]
 }
```

  - columns

|컬럼명| 내용|
|:--:|:--|
 | date | 날짜 |
 | hour | 시각(24시간기준) |
 | timezone | 타임존 |
 | campn_nm | 앱이름 |
 | campn_id | Campaign ID |
 | store_id | 앱패키지명 |
 | currency | 통화 |
 | start_dt | 광고 시작일 |
 | end_dt| 광고 종료일 |
 | imp | 노출수 |
 | click |  광고 클릭수 |
 | vdo_start | 비디오 시청수 |
 | cost | 광고비 |
 | conversion | 전환수 |
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
https://api2.tnkfactory.com/tnk/api/report/c1?api_key=xxxx&date=20160910&timezone=-12&check_cd=xxxx[&cmpn_id=8852]
```
