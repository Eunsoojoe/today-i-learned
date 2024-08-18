# SQL-ORM
ORM : app과 DB 연결할 때 SQL이 아닌 개발 언어로 DB에 접근할 수 있는 툴 

ORM은 SQL문법 대신 어플리케이션의 개발언어를 그대로 사용할 수 있게 함으로써, 개발 언어의 일관성과 가독성을 높여준다는 장점을 갖고 있습니다.

## 프로젝트 구성 & 모델링
- startproject
- startapp & INSTALLED_APPS
![alt text](image.png)
- movies/models.py 수정 modeling
- makemigrations, migrate

## dummy data 생성을 위한 custom command
- 폴더, 파일 생성
```movies/
    __init__.py
    models.py
    management/
        __init__.py
        commands/
            __init__.py
            generate.py
    tests.py
    views.py
```
- `python manage.py generate`

## ORM
- django 기본 쉘기능 업그레이드를 위한 라이브러리 설치
- `pip install django-extensions`
- `python manage.py shell`

## SQL
- VSCode 확장프로그램 SQLite 설치
- *.sql 파일 작성
- 우클릭 > Run Query

## MYSQL 설치
- MySQL Community Server 설치
- MySQL WorkVench 설치 및 접속