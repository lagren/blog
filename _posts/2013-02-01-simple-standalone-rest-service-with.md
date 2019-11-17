---
author: Eirik Tenold
date: 2013-02-01T16:17:00Z
modified_time: 2013-02-01T16:17:18.278+01:00
tags:
- REST
- Apache CXF
- Maven
title: Simple standalone REST service with Apache CXF
---

I wanted to create a simple REST service with Apache CXF. The simple steps:

In pom.xml:

{{< highlight xml >}}
<dependency>
    <groupId>org.apache.cxf</groupId>
    <artifactId>cxf-rt-frontend-jaxrs</artifactId>
    <version>2.6.1</version>
</dependency>
<dependency>
    <groupId>org.apache.cxf</groupId>
    <artifactId>cxf-rt-transports-http-jetty</artifactId>
    <version>2.6.1</version>
</dependency>
{{< / highlight >}}

The service implementation:

{{< highlight java >}}
@Path(“/a/”)
public class MyServiceImpl {

    @GET
    @Path(“/b”)
    @Produces(“application/json”)
    public String test() {
        return “42”;
    }
}
{{< / highlight >}}

To start the service as a standalone app:

{{< highlight java >}}
public static void main(String[] args) {
    MyServiceImpl myService = new MyServiceImpl();

    JAXRSServerFactoryBean factoryBean = new JAXRSServerFactoryBean();
    factoryBean.setResourceClasses(MyServiceImpl.class);
    factoryBean.setResourceProvider(MyServiceImpl.class, new SingletonResourceProvider(myService));
    factoryBean.setAddress(“http://localhost:8080/info”);
    Server server = factoryBean.create();
}
{{< / highlight >}}
