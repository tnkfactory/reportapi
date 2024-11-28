# 보상형 광고 정산 Report API
## 0. API KEY
   -  TNK 사이트에 연동인증키를 확인하거나 또는  담당자에게 전달 받습니다.

## 1. API URL
  - https://api2.tnkfactory.com/tnk/api/report/b1

## 2. Request Parameters
   - api_key : 연동인증키
   - date : yyyyMMdd
   - check_cd : md5(date + "9" + api_key)

## 3. result (JSON)
  - data type:
```
{return:number,  
 date:"yyyyMMdd"
 report:[
          {
            campn_nm:"string", 
            campn_id:number, 
            currency:"string", 
            cost:number, 
            pay_cnt:number
          }, ...
      ]
}
 ```

  - columns

  |컬럼명 |내용 |
  |:--|:--|
  | date | 날짜|
   |campn_nm | 앱이름|
   |campn_id | Campaign ID|
   |currency | 통화|
   |cost | 광고비|
   |pay_cnt | 전환수|

   
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
https://api2.tnkfactory.com/tnk/api/report/b1?api_key=xxxx&date=20240214&check_cd=xxxx
```
