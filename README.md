# docker-compose

```bash
docker-compose build  #  构建镜像
docker-compose up -d  #  启动镜像
```
> *注意* : 需要把docker本身内存设置为6GB
>> Mac配置docker内存：Docker Destop --> 设置 --> Resources --> Memory 然后Apply&Restart

执行```docker-compose up -d```后，如果顺利将可以看到Flink Web UI (http://127.0.0.1:8081)、Kibana (http://127.0.0.1:5601)、 Elasticsearch (http://127.0.0.1:9200)


# 注册 debezium 的数组源
命令：
```bash
curl -i -X DELETE -H "Accept:application/json" -H "Content-Type:application/json" http://localhost:8083/connectors/mysql-source-ec
curl -i -X DELETE -H "Accept:application/json" -H "Content-Type:application/json" http://localhost:8083/connectors/mysql-source-crm
curl -i -X DELETE -H "Accept:application/json" -H "Content-Type:application/json" http://localhost:8083/connectors/mongodb-source-crawler
curl -i -X POST -H "Accept:application/json" -H "Content-Type:application/json" http://localhost:8083/connectors/ -d @register-ec.json
curl -i -X POST -H "Accept:application/json" -H "Content-Type:application/json" http://localhost:8083/connectors/ -d @register-crm.json
curl -i -X POST -H "Accept:application/json" -H "Content-Type:application/json" http://localhost:8083/connectors/ -d @register-crawler-mongodb.json
curl -i -X GET -H "Accept:application/json" -H "Content-Type:application/json" http://localhost:8083/connectors
```
>curl -i -X DELETE 的时候可能返回404，是正常的，表示要删除的文件不存在

## docker 容器常规操作
```bash
>> docker-compose build #构建镜像
>> docekr-compose up -d #启动集群
>> docker-compose ps #查看集群运行状态
>> docker-compose restart xx #如未指定xx容器，将全部重启，同理操作还有stop(停止)、start(启动)
>> docker-compose stop mysql && docker-compose up -d #当mysql更改了配置compose.yaml配置文件后，重新启动
```

# 至此flink+elasticsearch+mongo+kafka+mysql集群搭建完成


