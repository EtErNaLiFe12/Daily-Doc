## File search

command + shift + f 전체 찾기

shift + shift 파일 찾기

## spring boot - maria db 연동

spring.datasource.driverClassName=org.mariadb.jdbc.Driver
spring.datasource.url=jdbc:mariadb://127.0.0.1:3306/test (본인 컴퓨터 주소 입력)
spring.datasource.username=아이디 입력
spring.datasource.password=비밀번호 입력

### spring boot - mapper & controller 만들시

https://kjh95.tistory.com/346

---
## react native - spring boot server 연동

https://react.vlpt.us/integrate-api/01-basic.html

---
## 형태

- react native <--> server <--> database

## basic spring boot jpa 만드는것(db + server 연동한 상태에서)

https://goddaehee.tistory.com/209

### jpa reference

https://megazonedsg.github.io/tutorial-jpa/

---

## How to make RestFul api

1. docker container 생성(image 생성 등)

2. db 연동(DBeaver)

3. server db 연동(application.yml 정의)

4. jpa setting

- in application.yml

5. jpa 형태

- Client <--> DTO/VO <--> Controller <--> Service <--> Repository <--> Domain(entity) <--> Server

6. entity 생성

- Make an entity class that mapping with table

7. Repository 생성

- Extends with JpaRepository

8. Service 생성

- Make the Service Class for using JpaRepository interface
- define function that have to rollback, and commit as service unit for itself.

9. Controller 생성

- define when responsing the data as same as json without uisng view page


