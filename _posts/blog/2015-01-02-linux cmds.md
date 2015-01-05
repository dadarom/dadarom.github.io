---
layout: post
title: linux command
description: linux command
categories: collect mysql linux shell
---

##1. linux command

###nets

`iotop` `iostat` `nslookup`

###awk

`
lsof -i:2181|grep TCP|grep LISTEN|grep IPv6|awk '{printf("%d\t%s\n"),$2,$1}'
`

###Replace string

~~~
61s/{targetStr}/{sourceStr}/ `
46,61s/{targetStr}/{sourceStr}/
%s/{targetStr}/{sourceStr}/g
~~~

###Watch

~~~
watch -n  1 -d "sudo  netstat -anp|grep 9092|wc -l "
watch -d 'curl -s http://127.0.0.1:34561/metrics | python -m json.tool '
~~~

###修改权限与属性

`chown` `chgrp` `chmod`

###Disk Useage

`du -sh`
``` df ```

### args

`
jps -m|grep flume2hbase${i}|awk '{print $1}' | xargs kill
`

###grep
` grep -R --include=*.xml  'com.google.protobuf' ./ `

## 2. mysql command

__load data into mysql__

~~~
mysql -u root -p --local-infile mybatis -h localhost -P 3306  -e "LOAD DATA LOCAL INFILE '/home/leo/mysql-data/rt_20141221.data' INTO TABLE nginx_url_referer_day FIELDS TERMINATED BY ',' (host,@var1,url,referer,2xx3xx_body_size,4xx_body_size,5xx_body_size,all_body_size,2xx3xx_response_time,4xx_response_time,5xx_response_time,all_response_time,2xx3xx_count,4xx_count,5xx_count,all_count) set source_time=str_to_date(@var1,'%d/%M/%Y:%H:%i:%s');" >>logs/mainloader.log 2>&1

LOAD DATA INFILE '/home/leo/test.data' INTO TABLE nginx_url_referer_day FIELDS TERMINATED BY ','  (host,@var1,url,referer,2xx3xx_body_size,4xx_body_size,5xx_body_size,all_body_size,2xx3xx_response_time,4xx_response_time,5xx_response_time,all_response_time,2xx3xx_count,4xx_count,5xx_count,all_count)  set source_time=str_to_date(@var1,'%d/%M/%Y:%H:%i:%s');
~~~

##3. linux shell

### 3.1 __Restart Supervisor__

~~~
#!/usr/bin/env bash
id=`/usr/local/jdk1.6.0_38/bin/jps -ml | grep -i supervisor|grep -v grep |awk '{print $1}'`
kill -9 $id
mv /apps/svr/storm-0.9.0.1/conf/storm.yaml /apps/svr/storm-0.9.0.1/conf/storm.yaml.bak
mv /apps/svr/storm-0.9.0.1/conf/storm.yaml.20141015.bak /apps/svr/storm-0.9.0.1/conf/storm.yaml
#cp -r /apps/svr/storm-0.9.0.1/storm-local /apps/svr/storm-0.9.0.1/storm-local-bak
#rm -rf /apps/svr/storm-0.9.0.1/storm-local/*
mv /apps/svr/storm-0.9.0.1/storm-local /apps/svr/storm-0.9.0.1/storm-local-bak
mkdir -p /apps/svr/storm-0.9.0.1/storm-local/
nohup /apps/svr/storm-0.9.0.1/storm supervisor >/dev/null 2>&1 &


#!/usr/bin/env bash
for supervisorIp in `cat /apps/svr/tools/supervisorhosts`;
   do
      echo $supervisorIp
       ssh $supervisorIp "sh /apps/svr/storm-0.9.0.1/conf/supervisor-chang.sh"
       #ssh 192.201.110.39  "echo 2 >  /apps/svr/storm-0.9.0.1/conf/sc.txt"
   done
~~~

### 3.2 __Restart flume process__

~~~
==============start=================================
for i in {1..6}
do
nohup bin/flume-ng agent -n agent-nginx2hbase${i} -c conf/flume2hbase${i} -f conf/flume2hbase${i}/agent-server${i}.conf &
#sleep 20s
done

==============stop=================================
for i in {1..6}
do
pid=`jps -m|grep flume2hbase${i}|awk '{print $1}'`
echo "flume instance ${i} : pid is ${pid}"
if [ ! -z  $pid ]
then
        kill $pid
        sleep 1s
        pid=`jps -m|grep flume2hbase${i}|awk '{print $1}'`
        if [ ! -z $pid ]
        then
                kill -9 $pid
        fi
else
        echo "flume instance ${i} already killed"       
fi
sleep 3s
done
===================================================
~~~



[Lei]:    http://dadarom.github.io  "Lei"
