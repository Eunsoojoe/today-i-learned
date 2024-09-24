# ElasticSearch 검색 시스템 
- 비정형 데이터도 색인 및 검색이 가능
- 기본적으로 HTTP를 통해 데이터 검색 -> json 형태의 구조로 반환
- RESTful API를 활용(*같은 URL 앞에 다양한 형태의 명령어 사용)
- 불변성 O = 과거의 정보 기록 X

## ElasticSearch Cloud
- [Elastic Cloud](https://www.elastic.co/kr/cloud/)에서 `Create Deployment` 
- 만들어진 `Deployment` - `Dev Tools`
<br>


## 로컬에서 ElasticSearch 구축
[관련 문서](https://www.elastic.co/guide/en/elasticsearch/reference/current/mapping-types.html)
- VsCode로 Ubuntu 열기 
- elasticsearch, kibana download
    - wget '복사한 다운로드 링크' 및 `tar -zxvf`

- terminal 2개 띄우고 elasticsearch와 kibana를 현재경로로 설정
- elasticsearch 서버 실행 `bin

- kibana 실행 `bin` -> localhost:5601 접석
- kibana & elasticsearch 연결
- create user -> admin / admin1234 (superuser)
- 데이터 모델링 = 매핑 = 스키마 정의
- 형태소 분석을 할 수 있는 데이터형은 'keyword'가 아닌 'text'
- keyword는 모두가 다 일치해야 함. 
- text는 분석기를 통해 나눠진 토큰과 일치하면 검색됨.

