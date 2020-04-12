# Distributed systems and computer networks <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Introduction and overview](#introduction-and-overview)
	- [Metrics and order of magnitude estimations](#metrics-and-order-of-magnitude-estimations)
- [CDN](#cdn)
- [DNS](#dns)
- [Big storage: file systems](#big-storage-file-systems)
	- [GFS (Google file system)](#gfs-google-file-system)
	- [HDFS (Hadoop Distributed File System)](#hdfs-hadoop-distributed-file-system)
- [Big storage: databases](#big-storage-databases)
	- [NoSQL databases](#nosql-databases)
		- [Google BigTable](#google-bigtable)
		- [Redis](#redis)
		- [Memcached](#memcached)
	- [Transaction processing](#transaction-processing)
		- [Two-phase/three-phase commit protocol](#two-phasethree-phase-commit-protocol)
		- [Paxos](#paxos)
- [Computation](#computation)
	- [MapReduce](#mapreduce)
	- [Unique ID generation](#unique-id-generation)
- [Distributed systems](#distributed-systems)
	- [Autocomplete](#autocomplete)
	- [Facebook](#facebook)
	- [Google Maps](#google-maps)
	- [Search](#search)
		- [Google Search](#google-search)
		- [Elasticsearch](#elasticsearch)
		- [Distributed search query execution](#distributed-search-query-execution)
	- [Stack Overflow](#stack-overflow)
	- [Twitter](#twitter)
	- [YouTube](#youtube)
	- [Instagram](#instagram)
- [Protocols](#protocols)
	- [Layer 4 protocols](#layer-4-protocols)
		- [TCP](#tcp)
		- [UDP](#udp)
	- [Layer 7 protocols](#layer-7-protocols)
		- [HTTP](#http)
		- [History](#history)
	- [WebSocket](#websocket)
- [Web APIs](#web-apis)
- [CAP theorem](#cap-theorem)
- [Load balancing](#load-balancing)
	- [Layer 4 load balancing](#layer-4-load-balancing)
	- [Layer 7 load balancing](#layer-7-load-balancing)
- [Blockchain](#blockchain)
- [Distributed graphs](#distributed-graphs)

---

## Introduction and overview

:movie_camera:

- T.Berglund. [*Distributed systems in one lesson*](https://www.youtube.com/watch?v=Y6Ev8GIlbxc) – Devoxx Poland (2017)
- D.Malan. [*Scalability*](https://www.youtube.com/watch?v=-W9F__D3oY4) – Harvard CS75: [Building dynamic websites](http://cs75.tv/2012/summer/)gh (2012)
- J.Dean. [*Building software systems at Google and lessons learned*](https://www.youtube.com/watch?v=modXC5IWTJI) –  Stanford (2010)

### Metrics and order of magnitude estimations

:link:

- S.Ignatchenko. [*The importance of back-of-envelope estimates*](https://accu.org/index.php/journals/2341) – [Overload **137**](https://accu.org/index.php/journals/c370/) (2017)

---

## CDN

:link:

- [*Content delivery network*](https://en.wikipedia.org/wiki/Content_delivery_network) – Wikipedia

:movie_camera:

- S.Keshav. [Lec. 4: *DNS and CDN*](https://www.youtube.com/watch?v=7-rxE636opw&t=2172) – CS 436: Distributed Computer Systems (2013)
- A.Bergman. [*What is a CDN and why developers should care about using one*](https://www.youtube.com/watch?v=farO15_0NUQ) – GOTO (2016)

:page_facing_up:

- J.Dilley et al. [*Globally distributed content delivery*](https://kilthub.cmu.edu/articles/Globally_distributed_content_delivery/6605972) – [IEEE Internet Computing **6**, 50](https://doi.org/10.1109/MIC.2002.1036038) (2002)

---

## DNS

:link:

- [*Domain Name System*](https://en.wikipedia.org/wiki/Domain_Name_System) – Wikipedia
- [*DNS technical reference*](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd197461%28v=ws.10%29) – Microsoft Docs (2017)

:movie_camera:

- S.Keshav. [*DNS and CDN*](https://www.youtube.com/watch?v=7-rxE636opw) – CS 436: Distributed Computer Systems (2013)

---

## Big storage: file systems

### GFS (Google file system)

:link:

- [*GFS FAQ*](https://pdos.csail.mit.edu/6.824/papers/gfs-faq.txt) – MIT 6.824: [Distributed systems](https://pdos.csail.mit.edu/6.824/) (2020)

:movie_camera:

- R.Morris. [*GFS*](https://www.youtube.com/watch?v=EpIgvowZr00) ([Notes](https://pdos.csail.mit.edu/6.824/notes/l-gfs.txt)) – MIT 6.824: [Distributed systems](https://pdos.csail.mit.edu/6.824/) (2020)

:page_facing_up:

- K.McKusick, S.Quinlan. [*GFS: Evolution on fast-forward*](https://queue.acm.org/detail.cfm?id=1594206) – [ACM Queue **7**](https://doi.org/10.1145/1594204.1594206) (2009)
- S.Ghemawat, H.Gobioff, S.-T. Leung. [*The Google file system*](https://static.googleusercontent.com/media/research.google.com/en//archive/gfs-sosp2003.pdf) – [ACM SIGOPS Operating Systems Review **37**, 29](https://doi.org/10.1145/1165389.945450) (2003)

### HDFS (Hadoop Distributed File System)

:page_facing_up:

- K.Shvachko, H.Kuang, S.Radia, R.Chansler. [*The Hadoop distributed file system*](https://storageconference.us/2010/Papers/MSST/Shvachko.pdf) – [IEEE Symposium on Mass Storage Systems and Technologies](https://doi.org/10.1109/MSST.2010.5496972) (2010)

---

## Big storage: databases

### NoSQL databases

:link:

- F.Gessert. [*NoSQL databases: A survey and decision guidance*](https://medium.baqend.com/nosql-databases-a-survey-and-decision-guidance-ea7823a822d) (2016)

:movie_camera:

- M.Fowler. [*Introduction to NoSQL*](https://www.youtube.com/watch?v=qI_g07C_Q5I) – GOTO (2012)

#### Google BigTable

:link:

- [*Bigtable*](https://en.wikipedia.org/wiki/Bigtable) – Wikipedia

:movie_camera:

- J.Dean. [*BigTable: A distributed structured storage system*](https://www.youtube.com/watch?v=2cXBNQClehA) – [CSE Colloquia](https://www.cs.washington.edu/events/colloquia/details?id=437) (2005)

<!-- https://www.youtube.com/watch?v=KaRbKdMInuc -->

:page_facing_up:

- F.Chang et al. [*BigTable: A distributed storage system for structured data*](https://dl.acm.org/doi/pdf/10.1145/1365815.1365816?download=true) – [ACM Transactions on Computer Systems **26**, 4](https://doi.org/10.1145/1365815.1365816) (2008)

#### Redis

:link:

- [*Redis documentation*](https://redis.io/documentation)
- S.Sanfilippo. [*Redis persistence demystified*](http://oldblog.antirez.com/post/redis-persistence-demystified.html) (2012)

#### Memcached

:link:

- [Memcached](https://memcached.org/)

:movie_camera:

- R.Nishtala. [*Scaling Memcache at Facebook*](https://www.youtube.com/watch?v=6phA3IAcEJ8) – NSDI (2013)

### Transaction processing

:link:

:movie_camera:

- R.Barrett. [*Transactions across datacenters*](https://www.youtube.com/watch?v=srOgpXECblk) – Google I/O (2009)

#### Two-phase/three-phase commit protocol

<!-- > In three-phase commit protocol there is never a time when a participant does a commit action that another participant is not anticipating. -->

:link:

- [*Two-phase commit protocol*](https://en.wikipedia.org/wiki/Two-phase_commit_protocol) – Wikipedia

:grey_question:

- [*How does three-phase commit avoid blocking?*](https://stackoverflow.com/q/21424962) – Stack Overflow

#### Paxos

:link:

- [*Paxos*](https://en.wikipedia.org/wiki/Paxos_%28computer_science%29) – Wikipedia

:movie_camera:

- H.Howard. [*Paxos agreement*](https://www.youtube.com/watch?v=s8JqcZtvnsM) – Computerphile (2016)
- C.Colohan. [Lec. 9: *Paxos simplified*](https://www.youtube.com/watch?v=SRsK-ZXTeZ0) – Distributed Systems Design (2017)

<!-- https://www.cs.utexas.edu/users/lorenzo/corsi/cs380d/papers/paper2-1.pdf
https://www.microsoft.com/en-us/research/uploads/prod/2004/01/twophase-revised.pdf
https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/tr-2003-96.pdf
 -->

:grey_question:

- [*Paxos vs two phase commit*](https://stackoverflow.com/q/27304887) – Stack Overflow

---

## Computation

### MapReduce

:link:

- H.Robinson. [*The elephant was a trojan horse: On the death of Map-Reduce at Google*](https://www.the-paper-trail.org/post/2014-06-25-the-elephant-was-a-trojan-horse-on-the-death-of-map-reduce-at-google/) (2014)

:movie_camera:

- B.Brumitt. [*MapReduce used on large data sets*](https://www.youtube.com/watch?v=N8FHXgPJEfQ) – Seattle Conference on Scalability (2007)
- S.Ghemawat, J.Dean, J.Zhao, M.Austern. [*Google MapReduce by Google scientists*](https://www.youtube.com/watch?v=NXCIItzkn3E) – Google Technology RoundTable (2008)
- J.Tedesco. [*MapReduce: Simplified data processing on large clusters*](https://www.youtube.com/watch?v=u8h88oPHDMw) (2012)

:page_facing_up:

- J.Dean, S.Ghemawat. [*MapReduce: Simplified data processing on large clusters*](https://dl.acm.org/doi/pdf/10.1145/1327452.1327492?download=true) – [Communications of the ACM **51**](https://doi.org/10.1145/1327452.1327492) (2008)

### Unique ID generation

:link:

- [*Sharding & IDs at Instagram*](https://instagram-engineering.com/sharding-ids-at-instagram-1cf5a71e5a5c) – Instagram Engineering (2012)
- [*Twitter Snowflake* (retired)](https://github.com/twitter-archive/snowflake/tree/b3f6a3c6ca8e1b6847baa6ff42bf72201e2c2231)

<!-- https://code.flickr.net/2010/02/08/ticket-servers-distributed-unique-primary-keys-on-the-cheap/ -->

:movie_camera:

- C.Colohan. [Lec. 15: *Unique ID*](https://www.youtube.com/watch?v=W6qURtqrldc) – Distributed Systems Design (2019)

---

## Distributed systems

### Autocomplete

:link:

- W.Wahed, T.Han, J.Shenk. [*Building Prefixy*](https://prefixy.github.io/)

### Facebook

:movie_camera:

- H.Fisk. [*Large-scale low-latency storage for the social network*](https://www.youtube.com/watch?v=5RfFhMwRAic) – Data@Scale (2013)

### Google Maps

:movie_camera:

### Search

#### Google Search

:page_facing_up:

- S.Brin, L.Page. [*The anatomy of a large-scale hypertextual Web search engine*](https://snap.stanford.edu/class/cs224w-readings/Brin98Anatomy.pdf) – [Computer Networks and ISDN Systems *30*, 107](https://doi.org/10.1016/S0169-7552(98)00110-X) (1998)
- L.A.Barroso, J.Dean, U.Hölzle. [*Web search for a planet: The Google cluster architecture*](https://static.googleusercontent.com/media/research.google.com/en//archive/googlecluster-ieee.pdf) – [IEEE Micro **23**, 22](https://doi.org/10.1109/MM.2003.1196112) (2003)

#### Elasticsearch

:link:

- C.Gormley, Z.Tong. [*Elasticsearch: The definitive guide*](https://www.elastic.co/guide/en/elasticsearch/guide/current/index.html) (2014–2015)

#### Distributed search query execution

:link:

- Sec.: [*Distributed search execution*](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-search.html) – C.Gormley, Z.Tong. [*Elasticsearch: The definitive guide*](https://www.elastic.co/guide/en/elasticsearch/guide/current/index.html) (2014–2015)

### Stack Overflow

:link:

- [*Stack Overflow: How we do app caching – 2019 edition*](https://nickcraver.com/blog/2019/08/06/stack-overflow-how-we-do-app-caching/) – Stack Overflow blog (2019)
- [*Stack Overflow: The hardware – 2016 edition*](https://nickcraver.com/blog/2016/03/29/stack-overflow-the-hardware-2016-edition/) – Stack Overflow blog (2016)
- [*Stack Overflow: The architecture – 2016 edition*](https://stackoverflow.blog/2016/02/17/stack-overflow-the-architecture-2016-edition/) – Stack Overflow blog (2016)
- [*Stack Overflow: A technical deconstruction*](https://nickcraver.com/blog/2016/02/03/stack-overflow-a-technical-deconstruction/) – Stack Overflow blog (2016)
- [*What it takes to run Stack Overflow*](https://nickcraver.com/blog/2013/11/22/what-it-takes-to-run-stack-overflow/) – Stack Overflow blog (2013)
- [*Stack Exchange Data explorer*](https://data.stackexchange.com/)

:movie_camera:

- O.Coster. [*Stack Overflow behind the scenes – how it’s made*](https://www.youtube.com/watch?v=6lbH_rTQrH0) – Codemotion (2017)
- M.Cecconi. [*High performance architecture of Stack Overflow*](https://www.youtube.com/watch?v=zTRd6CoEEqA) – code.talks (2016)
- M.Cecconi. [*High performance architecture of Stack Overflow*](https://www.youtube.com/watch?v=uNVlQ1yPsto) – JSConf.Asia (2016)
- M.Cecconi. [*The architecture of Stack Overflow*](https://www.youtube.com/watch?v=rkVvxgdY9F8) – Infoshare (2014)
- M.Cecconi. [*The architecture of Stack Overflow*](https://www.youtube.com/watch?v=OGi8FT2j8hE) – code.talks (2013)
- M.Cecconi. [*The architecture of Stack Overflow*](https://www.youtube.com/watch?v=t6kM2EM6so4) – Dev Day (2013)
- S.Hanselman. [*StackExchange*](https://channel9.msdn.com/Events/Ch9Live/MIX11/C9L105) – MIX11 (2011)

### Twitter

:link:

- [*Tutorial: Design and implementation of a simple Twitter clone using PHP and the Redis key-value store*](https://redis.io/topics/twitter-clone)

### YouTube

:movie_camera:

- C.Do. [*YouTube scalability*](https://www.youtube.com/watch?v=w5WVu624fY8) – Seattle Conference on Scalability (2007)

### Instagram

:link:

- [*What powers Instagram: Hundreds of instances, dozens of technologies*](https://instagram-engineering.com/what-powers-instagram-hundreds-of-instances-dozens-of-technologies-adf2e22da2ad) – Instagram Engineering (2011)

:movie_camera:

- L.Guo. [*Scaling Instagram infrastructure*](https://www.youtube.com/watch?v=hnpzNAPiC0E) – QCon (2017)
- P.Hunt. [*How Instagram.com works*](https://www.youtube.com/watch?v=VkTCL6Nqm6Y) – OSCON (2014)
- R.Branson. [*Messaging at scale at Instagram (Async tasks at Instagram)*](https://www.youtube.com/watch?v=E708csv4XgY) – PyCon (2013)

---

## Protocols

### Layer 4 protocols

:link:

- S.Ignatchenko. [*Once again on TCP vs UDP*](https://accu.org/index.php/journals/2180) – [Overload **130**](https://accu.org/index.php/journals/c356/) (2015)

#### TCP

:link:

- [*Transmission Control Protocol*](https://en.wikipedia.org/wiki/Transmission_Control_Protocol) – Wikipedia

#### UDP

### Layer 7 protocols

#### HTTP

:book:

- Sec.: *HTTP* – I.Grigorik. [*High performance browser networking*](https://hpbn.co/)

#### History

:link:

- [*Evolution of HTTP*](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Evolution_of_HTTP) – MDN

### WebSocket

:link:

- [*WebSocket*](https://en.wikipedia.org/wiki/WebSocket) – Wikipedia
- [*When to use a HTTP call instead of a WebSocket (or HTTP 2.0)*](https://blogs.windows.com/windowsdeveloper/2016/03/14/when-to-use-a-http-call-instead-of-a-websocket-or-http-2-0/) – Windows Apps Team (2016)

<!-- https://samsaffron.com/archive/2015/12/29/websockets-caution-required -->

:grey_question:

- [*Does HTTP/2 make websockets obsolete?*](https://stackoverflow.com/q/28582935) – Stack Overflow
- [*WebSockets protocol vs HTTP*](https://stackoverflow.com/q/14703627) – Stack Overflow


<!--

https://developer.mozilla.org/en-US/docs/Web

server-sent events

## Web APIs

https://en.wikipedia.org/wiki/Server-sent_events
https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events#Event_stream_format -->

<!-- https://www.infoq.com/articles/Web-Sockets-Proxy-Servers/ -->

## CAP theorem

> It is impossible for a distributed data store to simultaneously provide more than two out of the following three guarantees: *consistency* (every read receives the most recent write or an error), *availability* (every request receives a non-error response, without the guarantee that it contains the most recent write), and *partition tolerance* (the system continues to operate despite an arbitrary number of messages being dropped or delayed by the network between nodes).

:link:

- H.Robinson. [*The CAP FAQ*](https://github.com/henryr/cap-faq) (2013)

:movie_camera:

- C.Colohan. [Lec. 16: *The CAP theorem*](https://www.youtube.com/watch?v=k-Yaq8AHlFA) – Distributed Systems Design (2019)

## Load balancing

### Layer 4 load balancing

> Layer 4 load balancing operates at the intermediate transport layer (Layer 4), which deals with delivery of messages with no regard to the content of the messages (a load-balancing decision is based on the source and destination IP addresses and ports recorded in the packet header). Nowadays, CPU and memory are sufficiently fast and cheap that the performance advantage for Layer 4 load balancing has become negligible or irrelevant in most situations.

:link:

- [*What is layer 4 load balancing?*](https://www.nginx.com/resources/glossary/layer-4-load-balancing/)

### Layer 7 load balancing

> Layer 7 load balancing operates at the high‑level application layer (Layer 7), which deals with the actual content of each message (a load‑balancing decision is based on the content of the message, like a URL or cookie).

:link:

- [*What is layer 7 load balancing?*](https://www.nginx.com/resources/glossary/layer-7-load-balancing/)

---

## Blockchain

:movie_camera:

- C.Colohan. [Lec. 12: *What is a blockchain*](https://www.youtube.com/watch?v=Jp7T9qtuRIE) – Distributed Systems Design (2018)

## Distributed graphs

<!-- :movie_camera:

- V.S.Mirrokni. [*Distributed graph mining: Theory and practice*](https://www.youtube.com/watch?v=hEvMay48K4E) – KDD (2017) -->
