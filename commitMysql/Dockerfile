# 베이스 이미지 (공식 이미지 저장)
FROM mysql:latest

# 초기화 SQL
# /docker-entrypoint-initdb.d
# -> 초기화 스크립트는 이름의 오름차순으로 실행
# -> 최초 컨테이너 실행시 단 한번 만 수행된다
COPY mydb_board.sql /docker-entrypoint-initdb.d/
COPY mydb_career.sql /docker-entrypoint-initdb.d/
COPY mydb_degree.sql /docker-entrypoint-initdb.d/
COPY mydb_family.sql /docker-entrypoint-initdb.d/
COPY mydb_mypage.sql /docker-entrypoint-initdb.d/
COPY mydb_photo.sql /docker-entrypoint-initdb.d/
COPY mydb_profile.sql /docker-entrypoint-initdb.d/
COPY mydb_review.sql /docker-entrypoint-initdb.d/
# COPY mydb_routines.sql/docker-entrypoint-initdb.d/
COPY mydb_user.sql /docker-entrypoint-initdb.d/
COPY mydb_grant.sql /docker-entrypoint-initdb.d/


# 환경 변수
ENV MYSQL_ROOT_PASSWORD=${MYSQL_ROOT_PASSWORD}
ENV MYSQL_DATABASE=${MYSQL_DATABASE}
ENV MYSQL_USER=${MYSQL_USER}
ENV MYSQL_PASSWORD=${MYSQL_PASSWORD}
ENV TZ=%{TZ}

# 타임존 설정
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# 특별한 MySql 설정 필요
# 필요한 경우 설정 파일을 복사
# [복사 위치]
# - /etc/mysql/conf.d <- .cnf 파일을 복사
# - /etc/mysql/my.cnf : MySql 시스템 설정 파일
# - 윈도우 버전에서는 my.ini 

# 포트 노출
EXPOSE 3306

# 서버 실행
CMD ["mysqld"]

# build
# docker build -t mysql-custom .

# run
# docker run -d --name mysql-container -p 13306:3306 --network my-network  --env-file .env -v mysql-data:/var/lib/mysql mysql-custom
# volume이 영향을 줄 수 있으므로 sql접근 권한이 걸릴경우 volume을 삭제하고 다시 만드는 것이 좋다 (오류 해결)

# docker run --name mysql-commit-container -d -p 13306:3306 --env-file .env mysql-commit