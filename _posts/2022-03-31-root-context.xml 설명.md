---
title: Spring | root-context.xml
author: 안성윤
date: 2021-03-31 22:50:01 -0500
categories: [Spring, Spring 기초]
tags: [Spring, 환경설정]
---

## root-context.xml 설명

### root-context.xml 설명

#### 전역 설정 파일(root-context.xml)

- 요청과 관계없는 도구들을 이곳에 등록
- beans 태그 사이에 bean 이라는 태그로 등록
- xmlns:xsi는 품질보증서, xml 파일이라고 명시를 해준다 생각하면된다.

#### <bean> 태그 

앞으로 스프링에서 사용할 도구가 있다면 bean 태그로 등록, 내가 new로 만드는 것이 아니라 Spring 에서 singleton으로 생성해준다

#### 스프링의 1번째 특징 - IoC(Inversion of Control, 제어의 역전)

- id : 이름(식별자)
- class : 등록할 도구의 위치

#### 데이터 베이스 연결만 처리하는 도구 : 추가적으로 정보 제공이 필요하다.

- constructor-args : 생성자를 통한 정보 전달(필수)
- property : setter 메소드를 통한 정보 전달(선택)

```xml
<bean id="dataSource" 				         class="org.springframework.jdbc.datasource.DriverManagerDataSource.class">
</bean>
```



#### Spring 에서 기본적으로 제공하는 명령 실행 도구를 등록 - JDBCTemplate

- 필요한 정보 : 연결 도구(dataSource)
- 의존성 주입(DI , Dependency Injection) : 필요하니까 주입하여 사용하도록 요청

```xml
<bean id="jdbcTemplate" class="org.springframework.jdbc.core.JdbcTemplate">
	<property name="dataSource" ref="dataSource"></property>
    위에 있는 dataSource를 가져온다.
</bean>
```

#### DBCP 방식의 연결을 수행하는 도구

- 기존 연결도구 정보 + 관리정보
- maxTotal : 관리할 총 연결의 개수
- maxIdle : 여유분으로 연결해둘 연결의 최대 개수
- minIdle : 여유분으로 연결해둘 연결의 최소 개수
- maxWaitMillis : 연결이 모자를 경우 최대 대기시간

```xml
<bean id="dataSource2" class="org.apache.commons.dbcp2.BasicDataSource">
	<property name="driverClassName" value="oracle.jdbc.OracleDriver"></property>
	<property name="url" value="jdbc:oracle:thin:@localhost:1521:xe"></property>
	<property name="username" value="springuser"></property>
	<property name="password" value="springuser"></property>	
			
	<property name="maxTotal" value="20"></property>		
	<property name="maxIdle" value="10"></property>		
	<property name="maxWaitMillis" value="3000"></property>		
</bean>
```
