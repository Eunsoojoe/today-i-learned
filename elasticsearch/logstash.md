
# 실시간 로그파일 읽기
(서버가 계속 돌아가면서 데이터가 만들어지고 있다고 상황 가정)
- logstash download & unzip `wget` `tar -zxvf`
- logstash > pipeline > logfile.conf
    - input, filter, output 정의
        - input : 자동으로 생성된 로그 데이터  파일을 읽어올 위치 정의
        - filter : grok을 통해 비정형데이터를 구조화
             client_ip, timestamp, method, request, version, status_code, bytes
        - output : Elastic에서 출력
- [terminal1] dmf/automation/logstash-generate.py 에서 로그데이터 자동 생성
- [terminal2] `bin/logstash -f pipeline/logfile.conf` 
    - 'logstash야 저 경로에 있는 파일을 읽어줘 ^^'
- localhost:9200 접속
<br><br>
# Kafka Topic 구독
- kafka와 zookeeper 실행
   ```
    # zookeeper 실행
    bin/zookeeper-server-start.sh -daemon config/zookeeper.properties
    # kafka 실행 
    bin/kafka-server-start.sh -daemon config/server.properties
    ```
- [terminal1] api를 활용해 비트코인 정보를 자동으로 수집하는 코드
- [terminal2] logstash > pipeline > bitcoin.conf
    - input : bootstrap server, topic 정의
    - filter : json 데이터를 logstash가 처리할 수 있는 형태로 변환
<br><br>

# django DB와 연결해서 데이터 읽기
- `git clone intsa pjt` `python3 manage.py runserver`
- 가상환경 활성화 후 django server 열기
- `logstash/pipeline/database.conf` 실행
- 게시물 새로 등록하고 업데이트 상황 파악