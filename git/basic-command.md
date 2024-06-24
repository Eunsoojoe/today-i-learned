# Git command

git은 '분산 버전 관리 시스템'이라고 하며 주목적은 변화된 코드 내용을 확인하기 위함이다. 

[ 전체 흐름 ]
working directory에 있는 파일을 add해서 staging area 무대 위로 올려 사진을 찍고 이를 .git directory에 보관

> git 기본 명령어 정리

## init
- 현재 위치에 `.git` 폴더를 생성

```bash
git init
```

## add
- working directory => stage area
- . : 모든 파일을 staging area에 올려줘

```bash
git add . 
```

## status