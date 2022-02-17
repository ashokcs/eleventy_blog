---
title: Worker Microservice from Monolithic code
banner: /img/microservice.jpeg
---

<h2>The most interesting task I have been assigned, is all about the creation of TWO Microservices that were extracted from the Monolithic System.</h2>

Domain: Online Bill Payment / Financial

<strong>Tech Spec: Java, Spring Boot, PostgreSql, Redis, Kafka, Azure</strong>

If there is a redundant work happening in any System, the idea of automation and modularization should be implemented. The same thing happened in the Project Work. I proposed this idea to my team with Proof Of Concept and felt heard, when all the team members and my boss totally welcomed my idea.
With lot more responsibility I took my first step for this little milestone. There are many places in the big monolithic piece of system project calling the External Broker Service for the below needs:

To fetch Bill details

Field 1:  The Company Name and other that the bills were paid for.
Field 2: Paying the Bill through Tightly Integrated Service.
Field 3: Confirmation the Bill Payment.

Apart from this, there were other microservice applications that are calling these network apis from many places straight to the Broker Service. I created the Worker Utility application SErvice that receives Internal http calls from these local services and makes External https calls to External Broker Service.