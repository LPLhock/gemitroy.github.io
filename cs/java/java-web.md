# Java Web

### Java Servlet structure 

```text
appname
--WEB-INF 
----web.xml 
----classes 
----lib 
--index.html 
```

### Web.xml

```text
<web-app>
    <context-param>
        <param-name>country</>
        <param-value>china</>
    <servlet>
        <param-name></>
        <param-value></>
```

context-param &gt; listener &gt; filter &gt; servlet

getServletContext\(\).getInitParameter\("country"\) -&gt; china



