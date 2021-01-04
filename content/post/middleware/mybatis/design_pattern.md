---
title: "[Mybatis]1.Mybatis源码中设计模式"
date: 2020-12-31T11:13:47+08:00
lastmod: 2020-12-31T11:13:47+08:00
keywords: ['mybatis']
description: ""
tags: ['java','mybatis','design-pattern']
categories: ['Java']
author: ""
---
# Mybatis源码中设计模式


+ Builder模式：例如SqlSessionFactoryBuilder、XMLConfigBuilder、XMLMapperBuilder、XMLStatementBuilder、CacheBuilder；
+ 工厂模式：例如SqlSessionFactory、ObjectFactory、MapperProxyFactory；
+ 单例模式：例如ErrorContext和LogFactory；
+ 代理模式：Mybatis实现的核心，比如MapperProxy、ConnectionLogger，用的jdk的+ 动态代理；还有executor.loader包使用了cglib或者javassist达到延迟加载的效果；
+ 组合模式：例如SqlNode和各个子类ChooseSqlNode等；
+ 模板方法模式：例如BaseExecutor和SimpleExecutor，还有BaseTypeHandler和所有的子类例如IntegerTypeHandler；
+ 适配器模式：例如Log的Mybatis接口和它对jdbc、log4j等各种日志框架的适配实现；
+ 装饰者模式：例如Cache包中的cache.decorators子包中等各个装饰者的实现；
+迭代器模式：例如迭代器模式PropertyTokenizer；