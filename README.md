# hessian-jakarta
This is an unofficial porting of the Java implementation of [Hessian](http://hessian.caucho.com/) to Jakarta EE 10; Jakarta EE 10 requires Java 11+.

It is based on the source code of Hessian version 4.0.66 (actually the latest one), however note that versions 4.0.63 through 4.0.66 have no change in the source code.

Before creating it, I quickly evaluated [some alternatives](https://www.alibabacloud.com/blog/an-introduction-and-comparison-of-several-common-java-serialization-frameworks_597900) but Hessian still seems the best in terms of ease of use.

## Maven
Official Hessian releases are not built by Maven and the official source code does not follow the standard Maven directory layout, however it does provide a POM in the `maven2` folder.  I adapted that POM without changing the directory layout to keep the number of changes as small as possible.  You can run `mvn` build commands in the `maven2` folder.

The artifacts of this project are not available on Maven Central (I deploy them to my company's repo).

## Integration with Spring
If you are using an old version of Spring and you are planning to upgrade it, note that [`HessianServiceExporter`](https://docs.spring.io/spring-framework/docs/5.3.31/javadoc-api/org/springframework/remoting/caucho/HessianServiceExporter.html) was deprecated and then [removed](https://github.com/spring-projects/spring-framework/issues/27422) so now you have to use `HessianServlet` directly.  A working example is available at [hessian-demo](https://github.com/pnavato/hessian-demo).  You can use it also to test this library.
