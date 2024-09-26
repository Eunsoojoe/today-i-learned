# ElasticSearch | Mapping
### Mapping 
- mapping = 스키마 정의 `PUT /{index명}`
```Json
PUT /movie
{
  "mappings": {
    "properties": {
      "title":{
        "type": "text"
      },
      "content": {
        "type": "text"
      }
    }
  }
}

GET /movie
```


###  Add Document
새로운 doc 추가  `POST /{index}/_doc`
```json
POST /movie/_doc
{
  "title": "title2",
  "content":"content2"
}

# 모든 데이터 조회
GET /movie/_search

# mapping 정보 확인
# meta data
GET /movie

# index close, open, delete
POST /movie/_close
POST /movie/_open
DELETE /movie
```
#### 정의되지 않은 필드를 추가하면?
```JSON
# 정의되지 않은 필드를 보내는 경우
# 자기가 알아서 정의
POST /movie/_doc
{
  "title": "스파이더맨",
  "content": "우리의 이웃",
  "year": 2024,
  "rating": 5
}

# 데이터 타입이 일치하지 않는 경우
POST /movie/_doc
{
  "title": "스파이더맨2",
  "content": "우리의 이웃2",
  "year": 2025,
  "rating": good
}
```
---

### Add Mapping
`PUT /{index}/_mapping`
```JSON
PUT /movie/_mapping
{
  "properties": {
    "year": {
      "type": "integer"
    }
  }
}
```

### 재색인(reindex)
#### 인덱스 전체 복제
```JSON
POST _reindex 
{
  "source": {"index": "movie"},
  "dest": {"index": "movie.v2"}
}

GET /movie.v2/_search
```

#### 인덱스 복제 (특정 필드만)
```JSON
POST _reindex
{
  "source": {
    "index": "movie",
    "_source": ["title", "content"]
  },
  "dest": {
    "index": "movie.v3"
  }
}
GET /movie.v3/_search
```