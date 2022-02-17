---
title: Cloud Service Performance Improvement
banner: /img/cloud.jpeg
---

<h2>Dead slowness in a critical Financial Monolithic system. </h2>

As I completed more than dozens of Performance improvement operations successfully in my apps hosted in Cloud Data Center. 
<u>Tech Spec: Java, Spring Boot, MySql, Redis, Kafka, AWS.</u>

The Grand Issue:
Customers are king!!, We have an entire Data Center started facing slowness occasionally. The slowness issue started piling up over a period of time. One fine day, later became worst day as many of the customers reported slowness.

Phase by phase solution:
Phase #1: (Quick and also Immediate Solution, but not cost effective.)
To the rescue our team from the incident, I volunteered the operation to lead and work on the field. Application server logs were just fine, except some deadlock and timeout logged in some places. I came up with the idea of increasing the lock timout value a bit more, with below configuration.

innodb_lock_wait_timeout=500

Meaning the 5 seconds of waiting time of the lock to release.

Good News!! The issues was temporarily resolved for most of the requests . I knew it was not the proper fix and a permanent or Optimized solution. I started analysing where is the real issue lies in code. In the Purchase Order (AKA PO) in Module A module flow, we have an option to create Payment entity from bulk PO in Module A. The action made the up the MySql Thread Pool dry high by repeatedly calling Data Base read operations for the same Process Order (Module B) resources.
With lot of patience and Step by Step analysing and debugging I was able to find and reproduce the issue and I had planned for the fix. Caching to the Rescue.

Yes I cached most of the data in api callls, that permanently solved the issues. 