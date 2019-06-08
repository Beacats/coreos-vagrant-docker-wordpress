# 各種コマンド

## Vagrantを起動
```
vagrant up
```

## VagrantにSSHで接続
```
vagrant ssh
```

## Dockerを起動するために移動
```
cd share/wp
```

## Dockerを起動
```
docker-compose up -d
```

## wp-contentの所有者を変更
```
docker-compose exec -T wordpress chown -R www-data:www-data /var/www/html/wp-content
```

## Dockerを停止
```
docker-compose stop
```

## Dockerを停止＆削除（コンテナ・ネットワーク）
```
docker-compose down
```

## Dockerを停止＆削除（コンテナ・ネットワーク・ボリューム）
```
docker-compose down -v
```

## Dockerコンテナのシェルの中に入る
```
docker exec -it {コンテナ名} bash
```
```
docker exec -it my-container-name bash
```

## mysqldumpでバックアップをする
```
docker exec -it {dbコンテナ名} sh -c 'mysqldump {データベース名} -u {データベースユーザ名} -p{データベースパスワード} 2> /dev/null' > $PWD/db-data/mysql.dump.sql
```
```
docker exec -it my-container-name-db sh -c 'mysqldump wordpress -u admin -ppass 2> /dev/null' > $PWD/db-data/mysql.dump.sql
```