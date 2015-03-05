# log4jdbc-proxy
Customize a method interceptor for log4jdbc ,used for spring jdbc proxy and different way to config .


## Usage ##

 - Add current jar to classpath
 
 - Declare interceptor for  log4jdbc

----------

    <bean id="log4jdbcInterceptor" class="net.sf.log4jdbc.DataSourceSpyInterceptor"/>



 - Declare Log4jdbc proxy
 
 

----------

    <bean id="dataSourceLog4jdbcAutoProxyCreator" class="org.springframework.aop.framework.autoproxy.BeanNameAutoProxyCreator">
		<property name="interceptorNames">
			<list>
				<value>log4jdbcInterceptor</value>
			</list>
		</property>
		<property name="beanNames">
			<list>
				<value>dataSource</value>
			</list>
		</property>
	</bean>  


- Config log4jdbc level


----------

    log4j.logger.jdbc.sqlonly=OFF
    log4j.logger.jdbc.sqltiming=INFO
    log4j.logger.jdbc.audit=OFF
    log4j.logger.jdbc.resultset=OFF
    log4j.logger.jdbc.connection=OFF

