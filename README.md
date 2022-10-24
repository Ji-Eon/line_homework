<h1 align="center">LW Assignment</h1>


### 실행 Script
- 쉘 스크립트로 바로 도커 이미지 다운 및 빌드가 가능합니다.
```sh
./product_flask.sh
```

- 도커 Container 정지 및 이미지 삭제 합니다.
```sh
./remove_docker.sh
```

- 도커 Volume , Network , File들을 삭제합니다.
```sh
./clean.sh
```

- env 파일!!!
```sh
만약 zip으로 다운로드할때 .env파일이 정상적으로 다운이 안되는 경우가 발생합니다. 
현재 repository와 같은 경로로 .env파일을 꼭 확인하여주시고 없으시면 생성후 repository에 저장된 값을 넣어주시면 됩니다
```
### 개발환경 및 사용 Tools
- MacOS 
- VSCode
- Docker & Docker-Compose
- Flask / Nginx / Postgresql
- Swagger 



### URL Description
### Swagger 
- http://localhost:5000/api-docs
```sh
  Flask서버에서 구현되어있는 API Document를 확인할 수 있으며 API 실행결과까지 확인할 수 있습니다.
```
![ininital](https://github.com/Ji-Eon/line_homework/blob/main/Git-Image/gitimage_1.png?raw=true)
### GET Method : Person 통계정보 전체 가져오기 ####
- http://0.0.0.0:5000/cdm/statistics/person
![ininital](https://github.com/Ji-Eon/line_homework/blob/main/Git-Image/gitimage_2.png?raw=true)


### GET Method : Visit 통계 정보 ###
- http://0.0.0.0:5000/cdm/statistics/visit
![ininital](https://github.com/Ji-Eon/line_homework/blob/main/Git-Image/gitimage_3.png?raw=true)


### Swagger / 함수형 #### 
- 본인의 경우 Class형을 이용하여 Swagger 문서를 할수 있는 점을 보여드리고 싶었습니다
- 현재 Django도 Class형을 이용하여 API를 개발하고 있으며 과제의 편의성과 심사위원님의 확인하실수 있도록 두가지 방법으로 구현하였습니다

### CDM Data 경험 ###
- 본인의 경우 CDM데이터를 이용하여 Node.js를 이용하여 Test Data를 이용하여 Taget Disease를 검색 및 분석한 경험이 있습니다.
![ininital](https://github.com/Ji-Eon/line_homework/blob/main/Git-Image/gitimage_9.png?raw=true)
![ininital](https://github.com/Ji-Eon/line_homework/blob/main/Git-Image/gitimage_10.png?raw=true)
![ininital](https://github.com/Ji-Eon/line_homework/blob/main/Git-Image/gitimage_11.png?raw=true)


### 함수형 Response ####
- Table 명 / 컬럼명 / 검색 id 값 
- 2번문항과 3번 문항은 id 값으로 원하는 값으로 return 할수 있을거라 생각되어 concept_id값을 기준으로 값을 검색해서 가져올수 있도록 개인적으로 설계를 해보았습니다.
- 또한 Pagenation에 경우 검색값이 워낙 많기때문에 함수형에서 render_template를 이용하여 pagenation을 구현하였습니다.
- 또한 concept_id가 워낙 많기 때문에 이와같은 방법과 시간을 고려하여 개발하였습니다.
- 현재 View에 나타난ㄴ 부분은 유의미한 결과값을 확인할수 있는 부분으로 추출할수 있게 3~4개 컬럼값을 가져올수 있도록하였습니다. 향후 전체데이터를 보여주더라도 Front-end에 Dictionary형태로 전달하여 
  pagenation을 구현할수 있습니다.
- 만약 Class형으로 바뀌게된다면 Between , Inner Join 을 이용하여 Pagenation과 관련값을 가져올수 있습니다
- 기존에 이와같은 방법에대해 Node.js로 구현한 경험이 있는데 이와같은 방법으로 시도를 한 기억이 있습니다.

#### Visit Occurrence #####
```sh
  example URL :  http://0.0.0.0:5000/search/visit_occurrence/visit_source_concept_id/0
```
![ininital](https://github.com/Ji-Eon/line_homework/blob/main/Git-Image/gitimage_4.png?raw=true)

#### Condition Occurrence #####
```sh
  example URL :  http://0.0.0.0:5000/search/condition_occurrence/condition_source_concept_id/4112343
```
![ininital](https://github.com/Ji-Eon/line_homework/blob/main/Git-Image/gitimage_5.png?raw=true)

#### Drug Exposure #####
```sh
  example URL :  http://0.0.0.0:5000/search/drug_exposure/drug_concept_id/40213154
```
![ininital](https://github.com/Ji-Eon/line_homework/blob/main/Git-Image/gitimage_6.png?raw=true)

#### Concept #####
```sh
  example URL :   http://0.0.0.0:5000/search/concept/concept_id/360
```
![ininital](https://github.com/Ji-Eon/line_homework/blob/main/Git-Image/gitimage_7.png?raw=true)

#### Death Occurrence #####
```sh
  example URL :  http://0.0.0.0:5000/search/death/death_type_concept_id/32815
```
![ininital](https://github.com/Ji-Eon/line_homework/blob/main/Git-Image/gitimage_8.png?raw=true)




#### DB 검색 및 성능 향상 의견 ####
- CDM 데이터의 경우 상당한 데이터 이기때문에 검색을 하더라도 시간자원이 매우 소요될수밖에 없을거 같습니다. 중간에 DB 연결서버가 끊어지는 현상이 종종 발생되어 클러스터링 키법을 이용하여 서버를 여러개 구성하여 각 서버를 대기할수 있도록하여 서비시 중단없이 지원할수 있도록 하는것이 첫번째 의견입니다. 또한 방대한 데이터 검색을 위해 샤딩을 이용하면 어떨가 싶습니다. 샤딩을 통해 테이블자체를 row단위로 나눠 검색의 성능을 높일수 있을거 같습니다.


# 👤 ** Volunteer Ji-Eon **

- Github: [@Ji-Eon](https://github.com/Ji-Eon)
- 본 Repository는 결과 수신에 따라 Private로 바로 변경하도록하겠습니다.
