# Docker コンテナのシェルの中に入る
docker exec -it {コンテナ名} bash
# docker exec -it my-container-name bash

# mysqldump でバックアップをする
docker exec -it {dbコンテナ名} sh -c 'mysqldump {データベース名} -u {データベースユーザ名} -p{データベースパスワード} 2> /dev/null' > $PWD/db-data/mysql.dump.sql
# docker exec -it my-container-name-db sh -c 'mysqldump wordpress -u admin -ppass 2> /dev/null' > $PWD/db-data/mysql.dump.sql