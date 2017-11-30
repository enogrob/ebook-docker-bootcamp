```
$ docker image pull mysql &> /dev/null

$ docker image ls mysql
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
mysql               latest              5709795eeffa        2 weeks ago         408MB

$ docker container run -d \
     --name mysql \
     -e MYSQL_ROOT_PASSWORD=wordpress \
     -e MYSQL_DATABASE=wordpress \
     mysql
12e7258d92bc8499cfd3855b29a4938e299d890c2938e1d9d9d0e87d50455700

$ docker container ls
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS               NAMES
12e7258d92bc        mysql               "docker-entrypoint..."   16 seconds ago      Up 15 seconds       3306/tcp            mysql

$ docker container logs mysql
:
2017-11-24T01:07:34.648656Z 0 [Note] Beginning of list of non-natively partitioned tables
2017-11-24T01:07:34.692350Z 0 [Note] End of list of non-natively partitioned tables

$ docker pull wordpress &> /dev/null

$ docker image ls wordpress
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
wordpress           latest              467f492bc127        3 days ago          413MB

$ docker container run -d \
     --name wordpress \
     --link mysql:mysql \
     -p 8080:80 \
     -e WORDPRESS_DB_PASSWORD=wordpress \
     wordpress
60fc59bdcd566452eb35b8471162a2079939066b066f0e4305c8b1051c809be5

$ docker container ls
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                  NAMES
60fc59bdcd56        wordpress           "docker-entrypoint..."   17 seconds ago      Up 15 seconds       0.0.0.0:8080->80/tcp   wordpress
12e7258d92bc        mysql               "docker-entrypoint..."   2 minutes ago       Up 2 minutes        3306/tcp               mysql

$ open http://localhost:8080

$ wget http://localhost:8080 | head
--2017-11-23 23:11:11--  http://localhost:8080/
Resolving localhost... ::1, 127.0.0.1
Connecting to localhost|::1|:8080... connected.
HTTP request sent, awaiting response... 302 Found
:

$ docker container stop wordpress mysql
wordpress
mysql

$ docker container rm wordpress mysql

$ docker container ls -a
CONTAINER ID        IMAGE                           COMMAND                  CREATED             STATUS                      PORTS               NAMES
6ef7a3906e69        agilesquare/oracle-11g:latest   "/bin/sh -c '/usr/..."   14 months ago       Exited (137) 9 months ago                       oracle-11g
2a25fb41cc70        neo4j:latest                    "/docker-entrypoin..."   16 months ago       Exited (143) 6 months ago                       neo4j

$ docker image ls wordpress
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
wordpress           latest              467f492bc127        3 days ago          413MB

$ docker image ls mysql
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
mysql               latest              5709795eeffa        2 weeks ago         408MB

$ docker image rm mysql
Untagged: mysql:latest
Untagged: mysql@sha256:1a2f9361228e9b10b4c77a651b460828514845dc7ac51735b919c2c4aec864b7
Deleted: sha256:5709795eeffac51eca46cf40ab36669aad27e8cb4b0e91876d5e9f7bafad6acb
Deleted: sha256:11843db40baa103faeae734b1c46436389cb7654292fe6274f315ccda43174ba
Deleted: sha256:8dfb45d56346fa24a915ec65cc2a58236ba8af95256147f760a85863c7a472de
Deleted: sha256:9fe266abf02117135607ae16f05a22d06059c7cd380f3196f7bab5468da79deb
Deleted: sha256:3f61cd47a0208b49b75a9556ae2327253d5626cacfa329b7ef957b8b15befaf1
Deleted: sha256:4ca55749a880ef9b44fb5dacc02e92051d7f62d77f2ac94853c218d2d61ab523
Deleted: sha256:771e9c2d19dc601eb01067ce356d14b5cc2ddbc98990898a24d55063a81f1326
Deleted: sha256:3b9481cdbb0de04525113da3e34f855bd9565959c706ed2a4f9626dc06c2b6f5
Deleted: sha256:3544e941e291205aab75a02659e1d5730c7d29ccad3c94c74a664ba6788256d1
Deleted: sha256:58a29363bf92d91660c000fb25bad7cc08efffcff5db8a3736d9e8f725084717

$ docker image rm wordpress
Untagged: wordpress:latest
Untagged: wordpress@sha256:937862438b4f2a6b56193ef2cfd5fe345566e51278be56a04a7dfcdde18c5922
Deleted: sha256:467f492bc127ddf79749ad571139b36844e31df43e483b08e38bee3e4fedb8d1
Deleted: sha256:6a5b166afa50fab89737bebb7bcc86e6c3d7e82b150f71b57a5ee5844f05d8cf
Deleted: sha256:204b1c7d2aaf590e538f2d196ed37f2a6eb673e4e2e224ad8512983357cc6b7b
Deleted: sha256:d8cd630307072abfa99f3b555de243e587386ead8a69e688755410d7fd988d36
Deleted: sha256:b3c2df79e060f83d631648d56135e9d6f55918828cc3e6fb060daf6a815fd971
Deleted: sha256:c92753290874e20c8166dafa39239dca67541c1ccef9aea306cafa4b6eef14d2
Deleted: sha256:825a3784b0b19d3e4cc485cea7ef9815324f3fb17fa9c97dc0dec640206d8fd3
Deleted: sha256:18c8f132306b48fee01b690dfe28e33b3b23b0500724be7ccb5594f8ccec1339
Deleted: sha256:a57b426ddcecee867f0de0cedea80bd7b0c5bffe01b181cd79c36a79f9585edb
Deleted: sha256:6983fba06da0ecf7920f40553b5ee8307321d61d63aca12a5cfc745da1d747ea
Deleted: sha256:40329c9eb08fbef33f9c24e6fca324266cd3c1d79bde8454a3b046b0759d40f4
Deleted: sha256:5e93147fea377b81a73c89f9e6b929befb81f9465b9660d60f405661ac07081a
Deleted: sha256:788d8e258e74d875460bf179546e94be7f3081b08775c2d3b06733ec1a53f5a3
Deleted: sha256:6c8359a93dfbfe468e97743760b66bb98f9284ec03e7d73d51dc304be614cbfa
Deleted: sha256:5586c5f62da6a931a589c43f1a002eb2739231cf87f329d79f9233f138c0c99b
Deleted: sha256:43eed16e8a7330876dac6b6262123ce3fb7cbfcbb65cef10e5a7f7b5bbbaa0ee
Deleted: sha256:2bca0a826a2997cc330060c8406ea5f68ebe9213f9a8326ee031b0ae2d9478dc
Deleted: sha256:1ff075a13fbdc6a5d2461653875342e09388347eda4ef80d71d8a7ae7dd33937
Deleted: sha256:c01c63c6823dd8a296c2134ea94d31121069f1c52f8f8789836bc7ea2e5cdc93
```
