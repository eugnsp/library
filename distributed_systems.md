# Distributed systems and computer networks <!-- omit in toc -->

## Table of contents <!-- omit in toc -->

- [Introduction and overview](#introduction-and-overview)
- [CDN](#cdn)
- [DNS](#dns)
- [Big storage: file systems](#big-storage-file-systems)
	- [GFS – Google file system](#gfs--google-file-system)
- [Big storage: databases](#big-storage-databases)
	- [NoSQL databases](#nosql-databases)
		- [Redis](#redis)
- [Computation](#computation)
	- [MapReduce](#mapreduce)
	- [Unique ID generation](#unique-id-generation)
- [Distributed systems](#distributed-systems)
	- [Stack Overflow](#stack-overflow)
	- [Twitter](#twitter)
	- [YouTube](#youtube)
	- [Instagram](#instagram)
- [Protocols](#protocols)
	- [TCP](#tcp)
	- [HTTP](#http)
		- [History](#history)
	- [WebSocket](#websocket)
- [Web APIs](#web-apis)

---

## Introduction and overview

:movie_camera:

- T.Berglund. [*Distributed systems in one lesson*](https://www.youtube.com/watch?v=Y6Ev8GIlbxc) – Devoxx Poland (2017)
- D.Malan. [*Scalability*](https://www.youtube.com/watch?v=-W9F__D3oY4) – Harvard CS75: [Building dynamic websites](http://cs75.tv/2012/summer/)gh (2012)
- J.Dean. [*Building software systems at Google and lessons learned*](https://www.youtube.com/watch?v=modXC5IWTJI) –  Stanford (2010)

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

:movie_camera:

- S.Keshav. [Lec. 4: *DNS and CDN*](https://www.youtube.com/watch?v=7-rxE636opw) – CS 436: Distributed Computer Systems (2013)

---

## Big storage: file systems

### GFS – Google file system

:link:

- [*GFS FAQ*](https://pdos.csail.mit.edu/6.824/papers/gfs-faq.txt) – MIT 6.824: [Distributed systems](https://pdos.csail.mit.edu/6.824/) (2020)

:movie_camera:

- R.Morris. [*GFS*](https://www.youtube.com/watch?v=EpIgvowZr00) ([Notes](https://pdos.csail.mit.edu/6.824/notes/l-gfs.txt)) – MIT 6.824: [Distributed systems](https://pdos.csail.mit.edu/6.824/) (2020)

:page_facing_up:

- K.McKusick, S.Quinlan. [*GFS: Evolution on fast-forward*](https://queue.acm.org/detail.cfm?id=1594206) – [ACM Queue **7**](https://doi.org/10.1145/1594204.1594206) (2009)
- S.Ghemawat, H.Gobioff, S.-T. Leung. [*The Google file system*](https://static.googleusercontent.com/media/research.google.com/en//archive/gfs-sosp2003.pdf) – [ACM SIGOPS Operating Systems Review **37**, 29](https://doi.org/10.1145/1165389.945450) (2003)

---

## Big storage: databases

### NoSQL databases

#### Redis

:link:

- [*Redis documentation*](https://redis.io/documentation)
- S.Sanfilippo. [*Redis persistence demystified*](http://oldblog.antirez.com/post/redis-persistence-demystified.html) (2012)

---

## Computation

### MapReduce


### Unique ID generation

:link:

- [*Sharding & IDs at Instagram*](https://instagram-engineering.com/sharding-ids-at-instagram-1cf5a71e5a5c) – Instagram Engineering (2012)

<!-- https://code.flickr.net/2010/02/08/ticket-servers-distributed-unique-primary-keys-on-the-cheap/ -->

---

## Distributed systems

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

### TCP

:link:

- [*Transmission Control Protocol*](https://en.wikipedia.org/wiki/Transmission_Control_Protocol) – Wikipedia

### HTTP

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
