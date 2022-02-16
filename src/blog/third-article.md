---
title: Worker Microservice from Monolithic code
banner: /img/microservice.jpeg
---

<h2>This story is all about the creation of TWO Microservices that were extracted from the Monolithic System.</h2>

Domain: Online Bill Payment / Financial

<strong>Tech Spec: Java, Spring Boot, PostgreSql, Redis, Kafka, Azure</strong>

Whenever there is a repetitive work happening in any System, the idea of modularization should be implemented. The same thing happened in the project that I have been working on. I proposed this idea to my team with POC and felt heard, when the team and my boss appreciated my idea.

Happily took my first step for this little milestone. There are many places in the monolithic system project calling the External Broker Service for the below needs:

To fetch Bill details

Company details that the bills were paid for.
Paying the Bill through Integrated service.
Confirming the Bill Payment.
Also there are other microservices that are calling these apis from many places directly to the Broker Service. I created the Worker/External Utility service that receives Internal http calls from these local services and makes External https calls to External Broker Service.