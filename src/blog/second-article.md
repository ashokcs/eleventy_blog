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
Phase #1: (Quick & Immediate Solution)
To the rescue I volunteered the operation to lead and work in field. Application server logs are just fine, except some locks timeout logged here and there. I came up with the idea of increasing the lock time bit more, with below configuration.
innodb_lock_wait_timeout=500
which was 5 seconds of waiting time for the lock to release and acquire it.
Good News!! The issues was temporarily solved. I knew it was not the permanent or Optimized solution. I started digging where is the real issue lies in code. In the Purchase Order (Module A) module flow, we have an option to create payments from bulk PO (Module A). The action dries up the MySql Thread Pool high by repeatedly calling DB read operations for the same Process Order (Module B) resources.
With patience and Step by Step debugging I was able to find and reproduce the issue and I had planned for the fix. Caching to the Rescue.