---
author: Eirik Tenold
date: 2013-04-13T08:07:00Z
modified_time: 2013-04-13T09:35:14.236+02:00
tags:
- Spring Data
- Neo4j
- Spring Data Neo4j
- Graph database
title: Spring Data Neo4j, Neo4jTemplate, and Cypher queries
---

Yesterday, I tried to get [Spring Data Neo4j](http://www.springsource.org/spring-data/neo4j)'s 
[Neo4jTemplate](http://static.springsource.org/spring-data/data-neo4j/docs/current/api/org/springframework/data/neo4j/support/Neo4jTemplate.html) 
to work with a [Neo4j](http://www.neo4j.org/) server via REST. I got an error when I tried to run 
[Cypher queries](http://www.neo4j.org/learn/cypher) over REST. The only thing I got was an exception:

    java.lang.UnsupportedOperationException: null
     at org.neo4j.rest.graphdb.AbstractRemoteDatabase.getNodeManager(AbstractRemoteDatabase.java:136)
     at org.neo4j.rest.graphdb.RestGraphDatabase.getNodeManager(RestGraphDatabase.java:33)
     at org.neo4j.tooling.GlobalGraphOperations.&lt;init&gt;(GlobalGraphOperations.java:39)
     at org.neo4j.tooling.GlobalGraphOperations.at(GlobalGraphOperations.java:51)
     at org.neo4j.cypher.internal.spi.gdsimpl.GDSBackedQueryContext$$anon$1.all(GDSBackedQueryContext.scala:86)
     at org.neo4j.cypher.internal.executionplan.builders.GraphGlobalStartBuilder$$anonfun$createStartPipe$1.apply(GraphGlobalStartBuilder.scala:50)
 
 This was strange, since all other operations seemed to work fine. After a couple of hours worth of debugging, 
 I found the problem; the SpringRestGraphDatabase should be casted to GraphDatabase, not GraphDatabaseService.
 
 This **does not** work:
 
    SpringRestGraphDatabase springRestGraphDatabase = new SpringRestGraphDatabase("http://localhost:7474/db/data");
    Neo4jTemplate neo4jTemplate = new Neo4jTemplate((<i><b>GraphDatabaseService</b></i>) springRestGraphDatabase);
    org.springframework.data.neo4j.conversion.Result&lt;Map&lt;String, Object&gt;&gt; query = neo4jTemplate.query("start n=node(*) return n", null);

This works:

    SpringRestGraphDatabase springRestGraphDatabase = new SpringRestGraphDatabase("http://localhost:7474/db/data");
    Neo4jTemplate neo4jTemplate = new Neo4jTemplate((<i><b>GraphDatabase</b></i>) springRestGraphDatabase);
    org.springframework.data.neo4j.conversion.Result&lt;Map&lt;String, Object&gt;&gt; query = neo4jTemplate.query("start n=node(*) return n", null);