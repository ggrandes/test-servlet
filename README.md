# test-servlet

Simple Test Servlet, always returns OK, for running in a servlet container like Tomcat. Open Source Java project under Apache License v2.0

### Current Stable Version is [2.0.0](https://search.maven.org/#search|ga|1|g%3Aorg.javastack%20a%3Atest-servlet-jakarta)

---

## DOC

#### Installation:

* Place `test-servlet-jakarta-x.x.x.jar` in `tomcat/lib/` (for global monitoring of all context)

#### Configuration:

```xml
<!-- tomcat/conf/web.xml or WEB-INF/web.xml -->
<servlet>
    <servlet-name>TestServlet</servlet-name>
    <servlet-class>org.javastack.test.TestServlet</servlet-class>
    <load-on-startup>100</load-on-startup>
</servlet>
<servlet-mapping>
    <servlet-name>TestServlet</servlet-name>
    <url-pattern>/test</url-pattern>
</servlet-mapping>
```

Optional config for context fail its startup if any servlet that has `load-on-startup >= 0` fails its own startup.

```xml
<!-- tomcat/conf/context.xml or META-INF/context.xml -->
<?xml version='1.0' encoding='ISO-8859-1'?>
<Context failCtxIfServletStartFails="true">
    ...
</Context>
```

#### Simple Test:

```bash
curl -i http://localhost:8080/test
```

###### Output will be like:

```text
HTTP/1.1 200 OK
Pragma: no-cache
Cache-Control: private, no-cache, no-store, must-revalidate
Content-Type: text/plain;charset=ISO-8859-1
Content-Length: 4

OK
```

---

## MAVEN

###### jakarta.servlet (tomcat 10+)

    <dependency>
        <groupId>org.javastack</groupId>
        <artifactId>test-servlet-jakarta</artifactId>
        <version>2.0.0</version>
    </dependency>

###### javax.servlet (tomcat 7, 8.5, 9)

    <dependency>
        <groupId>org.javastack</groupId>
        <artifactId>test-servlet</artifactId>
        <version>1.0.0</version>
    </dependency>

---
Inspired in [Tomcat Context failCtxIfServletStartFails](https://tomcat.apache.org/tomcat-11.0-doc/config/context.html#Common_Attributes), this code is Java-minimalistic version.
