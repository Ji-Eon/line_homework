<h1 align="center">Wanted Assignment</h1>


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

### 개발환경 및 사용 Tools
- MacOS 
- VSCode
- Docker & Docker-Compose
- Flask / Nginx / Postgresql
- Swagger 


### .env File
- Postgresql DB Settings Value
- Folder Path


### URL Description
### Swagger 
- http://localhost:5000/api-docs
```sh
  Flask서버에서 구현되어있는 API Document를 확인할 수 있으며 API 실행결과까지 확인할 수 있습니다.
```
![ininital](https://github.com/Ji-Eon/Wanted_Assignment/blob/main/Git-Image/image_1.png?raw=true)
### GET Method : CompanyList 전체 가져오기 ####
- http://localhost:5000/wanted/companylist


### GET Method : Company Name / Tag 검색 ###
```sh
 Name / Tag 를 두개 Class로 나누어서 구현하였습니다.
```
- http://localhost:5000/wanted/search/name/name_type/value
- name_type [ company_ko,company_en,company_ja ], name_tpye은 정확히 입력해 주어야 합니다.
```sh
 회사 이름으로 검색할수 있도록 한 / 영 / 일 부분과 검색값을 넣어주면 관련된 회사명 검색하여 return 해 줍니다.
```
![ininital](https://raw.githubusercontent.com/Ji-Eon/Wanted_Assignment/ed0747c7592d181d309f2a7591a42791d2274c88/Git-Image/image_2.png)

- http://localhost:5000/wanted/search/tag/tag_type/value
- tag_type [ tag_ko,tag_en,tag_ja  ], tag_type 정확히 입력해 주어야 합니다.
```sh
태그 이름으로 검색할수 있도록 한 / 영 / 일 부분과 검색값을 넣어주면 관련된 회사Tag를 검색하여 return 해 줍니다.
```
![ininital](https://raw.githubusercontent.com/Ji-Eon/Wanted_Assignment/ed0747c7592d181d309f2a7591a42791d2274c88/Git-Image/image_3.png)

### DELETE Method : 회사 Tag정보 삭제 ###
```sh
 Method는 Delete로 최종 반영값은 Update를 이용하여 해당내용을 삭제할 수 있도록 로직을 구현하였습니다.
```
- http://localhost:5000/wanted/tag/delete/tag_type/value
- tag_type [ tag_ko,tag_en,tag_ja ]
- value : 검색값
![ininital](https://raw.githubusercontent.com/Ji-Eon/Wanted_Assignment/ed0747c7592d181d309f2a7591a42791d2274c88/Git-Image/image_4.png)

### Update Method : 회사 Tag정보 업데이트 ###
```sh
 회사 Tag값을 검색하여 변경값을 업데이트 합니다.
```
- http://localhost:5000/wanted/tag/put/tag_type/tag_value/update_value
- tag_type [tag_ko,tag_en,tag_ja]
- tag_vlae: 검색값
- update_value: 변경값
![ininital](https://raw.githubusercontent.com/Ji-Eon/Wanted_Assignment/ed0747c7592d181d309f2a7591a42791d2274c88/Git-Image/image_5.png)

# 👤 ** Volunteer Ji-Eon **

- Github: [@Ji-Eon](https://github.com/Ji-Eon)
