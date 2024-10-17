(base) [train@trainvm zookeeperless_kafka]$ docker-compose up -d
[+] Running 4/0
 ✔ Container kafka2           Running                                                                                                                                                                    0.0s
 ✔ Container kafka3           Running                                                                                                                                                                    0.0s
 ✔ Container kafka1           Running                                                                                                                                                                    0.0s
 ✔ Container schema_registry  Running      
(base) [train@trainvm zookeeperless_kafka]$ docker exec -it kafka1 bash
root@2ae28e157216:/# /kafka/bin/kafka-topics.sh
root@2ae28e157216:/# /kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --create --topic atscale --replication-factor 1 --partitions 2
Created topic atscale.
root@2ae28e157216:/# /kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --list
__consumer_offsets
_schemas
atscale
root@2ae28e157216:/#
root@2ae28e157216:/# /kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --describe --topic atscale
Topic: atscale  TopicId: lxLkha9pQ2yGx-SCtweeKQ PartitionCount: 2       ReplicationFactor: 1    Configs: segment.bytes=1073741824
        Topic: atscale  Partition: 0    Leader: 2       Replicas: 2     Isr: 2  Elr:    LastKnownElr:
        Topic: atscale  Partition: 1    Leader: 3       Replicas: 3     Isr: 3  Elr:    LastKnownElr:
root@2ae28e157216:/#
root@2ae28e157216:/# /kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --create --topic churn --replication-factor 1 --partitions 3
root@2ae28e157216:/# /kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --list
__consumer_offsets
_schemas
atscale
churn
root@2ae28e157216:/#
root@2ae28e157216:/# curl -O https://raw.githubusercontent.com/erkansirin78/datasets/master/Churn_Modelling.csv
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  659k  100  659k    0     0   896k      0 --:--:-- --:--:-- --:--:--  895k
root@2ae28e157216:/#
root@2ae28e157216:/# cat Churn_Modelling.csv | awk -F',' '{print $1","$0}' | /kafka/bin/kafka-console-producer.sh --topic churn --bootstrap-server localhost:9092 --property "parse.key=true" --property "key.separator=,"
root@2ae28e157216:/#
root@2ae28e157216:/# /kafka/bin/kafka-console-consumer.sh --topic churn --bootstrap-server localhost:9092 --group churn_group --from-beginnin
2,15647311,Hill,608,Spain,Female,41,1,83807.86,1,0,1,112542.58,0
3,15619304,Onio,502,France,Female,42,8,159660.8,3,1,0,113931.57,1
9,15792365,He,501,France,Male,44,4,142051.07,2,0,1,74940.5,0
16,15643966,Goforth,616,Germany,Male,45,3,143129.41,2,0,1,64327.26,0
29,15728693,McWilliams,574,Germany,Female,43,3,141349.43,1,1,1,100187.43,0
32,15706552,Odinakachukwu,533,France,Male,36,7,85311.7,1,0,1,156731.91,0
36,15794171,Lombardo,475,France,Female,45,0,134264.04,1,1,0,27822.99,1
40,15585768,Cameron,582,Germany,Male,41,6,70349.48,2,0,1,178074.04,0
41,15619360,Hsiao,472,Spain,Male,40,4,0,1,1,0,70154.22,0
49,15766205,Yin,550,Germany,Male,38,2,103391.38,1,0,1,90878.13,0
50,15771873,Buccho,776,Germany,Female,37,2,103769.22,2,1,0,194099.12,0
57,15630053,Tsao,656,France,Male,45,5,127864.4,1,1,0,87107.57,0
69,15638424,Glauert,661,Germany,Female,35,5,150725.53,2,0,1,113656.85,0
73,15812518,Palermo,657,Spain,Female,37,0,163607.18,1,0,1,44203.55,0
74,15779052,Ballard,604,Germany,Female,25,5,157780.84,2,1,1,58426.81,0
78,15662085,Read,678,France,Female,32,9,0,1,1,1,148210.64,0
83,15641732,Mills,543,France,Female,36,3,0,2,0,0,26019.59,0
85,15738751,Beit,493,France,Female,46,4,0,2,1,0,1907.66,0
90,15767954,Osborne,635,Germany,Female,28,3,81623.67,2,1,1,156791.36,0
91,15757535,Heap,647,Spain,Female,44,5,0,3,1,1,174205.22,1
97,15738721,Graham,773,Spain,Male,41,9,102827.44,1,0,1,64595.25,0
101,15808582,Fu,665,France,Female,40,6,0,1,1,1,161848.03,0
103,15580146,Hung,738,France,Male,31,9,82674.15,1,1,0,41970.72,0
104,15776605,Bradley,528,Spain,Male,36,7,0,2,1,0,60536.56,0
105,15804919,Dunbabin,670,Spain,Female,65,1,0,1,1,1,177655.68,1
111,15803526,Eremenko,685,Germany,Male,30,3,90536.81,1,0,1,63082.88,0
112,15665790,Rowntree,538,Germany,Male,39,7,108055.1,2,1,0,27231.26,0
114,15591100,Chiemela,675,Spain,Male,36,9,106190.55,1,0,1,22994.32,0
116,15675522,Ko,628,Germany,Female,30,9,132351.29,2,1,1,74169.13,0
root@2ae28e157216:/# /kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --delete --topic atscale
root@2ae28e157216:/#
root@2ae28e157216:/# /kafka/bin/kafka-topics.sh --bootstrap-server localhost:9092 --delete --topic churn










