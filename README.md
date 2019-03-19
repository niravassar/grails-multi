# grails-multi

This multi project build shows how `assemble` with gradle 5 and grails 4 rest-api (created from the rest-api profile) app does not work in a muti-project environment.
This affects several of the existing guides we have such as grails-vue-combined and react-view-combined because it relies on gradle
to bundle the front end and backend project into a runnable jar. 

This works

- start in grails-multi/
- `cd grails-four-rest-api`
- `gradlew assemble`
- `java -jar build\libs\grails-four-rest-api-0.1.jar`

This fails

- start in grails-multi
- `gradlew grails-four-rest-api:assemble`
- `java -jar server\build\libs\grails-four-rest-api-0.1.jar`

*ERROR*

```
2019-03-19 11:43:03.180 ERROR --- [nio-8080-exec-1] .a.c.c.C.[.[.[.[grailsDispatcherServlet] : Servlet.service() for servlet [grailsDispatcherServlet] in context with path [
] threw exception [Could not resolve view with name 'index' in servlet with name 'grailsDispatcherServlet'] with root cause

javax.servlet.ServletException: Could not resolve view with name 'index' in servlet with name 'grailsDispatcherServlet'
        at org.springframework.web.servlet.DispatcherServlet.render(DispatcherServlet.java:1350)
        at org.springframework.web.servlet.DispatcherServlet.processDispatchResult(DispatcherServlet.java:1116)
        at org.springframework.web.servlet.DispatcherServlet.doDispatch(DispatcherServlet.java:1055)
        at org.springframework.web.servlet.DispatcherServlet.doService(DispatcherServlet.java:942)
        at org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:1005)
        at org.springframework.web.servlet.FrameworkServlet.doGet(FrameworkServlet.java:897)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:634)
        at org.springframework.web.servlet.FrameworkServlet.service(FrameworkServlet.java:882)
        at javax.servlet.http.HttpServlet.service(HttpServlet.java:741)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:231)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:166)
        at org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:53)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:193)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:166)
        at org.springframework.boot.actuate.web.trace.servlet.HttpTraceFilter.doFilterInternal(HttpTraceFilter.java:90)
        at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:193)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:166)
        at org.grails.web.servlet.mvc.GrailsWebRequestFilter.doFilterInternal(GrailsWebRequestFilter.java:77)
        at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:193)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:166)
        at org.grails.web.filters.HiddenHttpMethodFilter.doFilterInternal(HiddenHttpMethodFilter.java:67)
        at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:193)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:166)
        at org.springframework.web.filter.CharacterEncodingFilter.doFilterInternal(CharacterEncodingFilter.java:200)
        at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:193)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:166)
        at org.springframework.boot.actuate.metrics.web.servlet.WebMvcMetricsFilter.filterAndRecordMetrics(WebMvcMetricsFilter.java:117)
        at org.springframework.boot.actuate.metrics.web.servlet.WebMvcMetricsFilter.doFilterInternal(WebMvcMetricsFilter.java:106)
        at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:193)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:166)
        at org.springframework.web.filter.CorsFilter.doFilterInternal(CorsFilter.java:96)
        at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:107)
        at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:193)
        at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:166)
        at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:200)
        at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:96)
        at org.apache.catalina.authenticator.AuthenticatorBase.invoke(AuthenticatorBase.java:490)
        at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:139)
        at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:92)
        at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:74)
        at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:343)
        at org.apache.coyote.http11.Http11Processor.service(Http11Processor.java:408)
        at org.apache.coyote.AbstractProcessorLight.process(AbstractProcessorLight.java:66)
        at org.apache.coyote.AbstractProtocol$ConnectionHandler.process(AbstractProtocol.java:834)
        at org.apache.tomcat.util.net.NioEndpoint$SocketProcessor.doRun(NioEndpoint.java:1415)
        at org.apache.tomcat.util.net.SocketProcessorBase.run(SocketProcessorBase.java:49)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
        at org.apache.tomcat.util.threads.TaskThread$WrappingRunnable.run(TaskThread.java:61)
        at java.lang.Thread.run(Thread.java:745)

2019-03-19 11:43:03.265 ERROR --- [nio-8080-exec-1] .a.c.c.C.[.[.[.[grailsDispatcherServlet] : Servlet.service() for servlet [grailsDispatcherServlet] threw exception

javax.servlet.ServletException: Could not resolve view with name '/error' in servlet with name 'grailsDispatcherServlet'
        at org.springframework.web.servlet.DispatcherServlet.render(DispatcherServlet.java:1350)
        at org.springframework.web.servlet.DispatcherServlet.processDispatchResult(DispatcherServlet.java:1116)
        at org.springframework.web.servlet.DispatcherServlet.doDispatch(DispatcherServlet.java:1055)
        at org.springframework.web.servlet.DispatcherServlet.doService(DispatcherServlet.java:942)
        at org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:1005)
        at org.springframework.web.servlet.Frame
```
