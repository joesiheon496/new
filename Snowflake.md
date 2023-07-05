[해당 사이트 블로그](https://zzsza.github.io/data-engineering/2023/05/28/how-to-use-snowflake/)의 글을 읽으면서 용어 정의

> 데이터 웨어하우스(Data Warehouse): 데이터 웨어하우스란 사용자의 의사 결정에 도움을 주기 위하여 기간시스템의 데이터베이스에 축적된 데이터를 공통의 형식으로 변환해서 관리하는 데이터베이스를 말한다
>> 예: 병원에서 모아놓은 CT 데이터들을 dicom 파일 형식 or nifti 형식으로 제공

## 종류
  - Google Cloud의 BigQuery
  - AWS의 Redshift
### 문제점
위의 2개의 문제점은 특정 클라우드 벤더사에 종속된 환경에서 사용함, 예를 들어 BigQuery는 Google Cloud, Redshift는 AWS에서만 사용

> 벤더:  '벤더'의 일반적인 뜻인 '판매인', '판매업자'를 이르는 말
> 벤더사: 벤더 제품은 보통 자기 것만 호환이 되며 일반적으로 타사 제품과 혼용하여 사용하지 못합니다.
> 독자적인 브랜드를 가지고, 거의 모든 파트를 자체 생산하여 만들어 진 제품을 벤더사 제품
> 반대의 뜻(슈퍼마이크): 주요 부품을 따로 살수 있으며, 그것을 타사의 제품과 혼용하여 사용해도 거의 문제가 없습니다.

- Snowflake는 어떤 곳에 데이터가 저장되어 있어도 활용할 수 있음,

- 멀티 클라우드 환경을 구축한다면 좋은 대안으로 사용할 수 있음

- 데이터 웨어하우스를 구축할 때 고려야해야 하는 점 중 하나는 **Transfer Cost**인데 동일 Region이라고 하면 대부분 비용을 부과하지 않음
  > Transfer Cost: 특정 리소스에 대해 지역 내 데이터 전송 시 인바운드 트래픽과 아웃바운드 트래픽 모두에 대해 요금이 부과됩니다.
    > 단, 벤더사에서 사용하는 모든 Region을 사용할 수 있는 것은 아님. 23년 5월 기준 Snowflake에서 지원하는 서울 Region은 AWS만 존재


  # 아키텍쳐
  
  ![image](https://github.com/joesiheon496/new/assets/56191064/327c00b5-2881-4c26-8555-c002ec92c7d2)

  [이미치 출처](https://www.snowflake.com/en/)

- Snowflake는 총 3개의 Layer로 구성됨
  - Database Storage Layer
    - 데이터를 내부적으로 최적화된 압축된 컬럼 형태로 재구성해 저장
  - Query Processing Layer
    - Virtual Warehouse를 사용해 쿼리를 처리함
    - 각각의 Virtual Warehouse는 독립적이며 서로 영향을 주지 않음
  - Cloud Service Layer
    - 인증, 인프라 관리, 메타데이터 관리, 쿼리 구문 분석 및 최적화, Access Control을 관리
- 쿼리를 실행하는 사람 관점에선 "Virtual Warehouse"라는 것이 있다.

## 비용 발생함

![image](https://github.com/joesiheon496/new/assets/56191064/06a22a06-16b7-4820-b330-6f9a365b03cc)

## SQL 쿼리로 실행

# [Snowflake Python에서 사용법](https://zzsza.github.io/data-engineering/2023/05/29/python-with-snowflake/)
