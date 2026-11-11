**中文版介绍：** [跳转](#星瀚学堂)

**English intro:**  [GOTO](#Milky-Institute)

# Milky Institute

## Project Overview:

Milky Institute is a production-grade online education project built on a microservice architecture, focusing on non-academic vocational skills training for adults. It consists of two parts: the student portal and the admin portal. Key services within the project include Learning Service, Coupon Service, and Lesson Recommendation AI Agent. This project is an improved implementation of "Tianji Academy". This repository contains the backend codebase.

## Tech Stack:

SpringCloud, SSM, Redis/Redisson, RabbitMQ, MySQL (sharding by database and table), XXL-Job, Spring AI etc.

## Project Responsibilities (Core Features)

🆕 **Completed:**

1. Implemented the Learning Service, achieving resume-play functionality using Redis-based write request merging and DelayQueue. Optimized high-concurrency database write operations, controlling errors within 15 seconds.
2. Developed Coupon Management functionality: generated redemption codes using bitwise weighted sum algorithm and asynchronous threads during coupon distribution, and validated redemption status via BitMap. Ensured readability, non-redeemability, anti-brute-force protection, and high efficiency of redemption codes.
3. Built Coupon Collection functionality: resolved concurrency security issues using optimistic locking and Redisson distributed locks, fixed lock invalidation caused by transaction boundary issues, and addressed transaction failure via AspectJ dynamic proxy.
4. Implemented encapsulation of generic distributed locks based on AOP, custom annotations, Factory Pattern, and Strategy Pattern.
5. Developed Coupon Usage functionality: queried all available coupons, performed preliminary screening, detailed screening, and permutation-combination calculations to generate all valid coupon combinations. Calculated discount details for each combination in parallel using CompletableFuture, and finally filtered out the optimal solution according to predefined rules.

⏳ **Development Plan**

1. Design and implement the Q&A and Comment Module: record Q&A/comment information based on user-selected anonymity settings, generate corresponding points, and push data to the Points System via RabbitMQ.
2. Build and implement the Like Service: receive like requests from the frontend, store like records and counts, and send MQ messages via scheduled tasks to notify business parties of like count updates.
3. Implement and optimize the Check-in Function: store check-in records using BitMap data structure, and push check-in information and points to the Points Service via MQ.
4. Develop Points Ranking functionality: store real-time monthly ranking data using Redis Zset. Persist historical rankings to MySQL (with database and table sharding) via XXL-Job sharding tasks, calculating table names using MybatisPlus dynamic table name feature.
5. Complete the LangChain Agent Module.

## Project Progress

Based on the basic version of "Sky Academy", some features are yet to be implemented.

Completion status is as follows:

| Microservice Name |  Function Description  |   Completion Status    |
| :---------------: | :--------------------: | :--------------------: |
|     tj-parent     |     Parent Project     | ✅ Completed       |
|      tj-api       |    Feign Extraction    | 🆕 Completed (Improved) |
|     tj-common     |     Common Project     | 🆕 Completed (Improved) |
|    tj-message     |     Message Center     | ✅ Completed       |
|    tj-gateway     |        Gateway         | 🆕 Completed (Improved) |
|      tj-auth      | Authentication Service | 🆕 Completed (Improved) |
|      tj-user      |      User Service      | ✅ Completed       |
|      tj-pay       |    Payment Service     | ✅ Completed       |
|     tj-course     |     Course Service     | 🆕 Completed (Improved) |
|      tj-exam      |      Exam Service      | ⏳ In Development    |
|     tj-search     |     Search Service     | ✅ Completed       |
|     tj-trade      |    Trading Service     | 🆕 Completed (Improved) |
|    tj-learning    |    Learning Service    | 🆕 Completed (New)    |
|   tj-promotion    |   Promotion Service    | 🆕 Completed (New)    |
|     tj-media      |     Media Service      | ✅ Completed       |
|      tj-data      |      Data Service      | ⏳ In Development    |
|     tj-remark     |     Review Service     | ⏳ In Development    |
|     tj-agent      |    LangChain Agent     | ⏳ In Development    |

## Project Domain List

|         Name         |                      Domain                      | Account & Password | Port  |
| :------------------: | :----------------------------------------------: | :----------------: | :---: |
|  Git Private Server  |     [git.tianji.com](https://git.tianji.com)     |    tjxt/123321     | 10880 |
|      Jenkins CI      | [jenkins.tianji.com](https://jenkins.tianji.com) |      root/123      | 18080 |
|       RabbitMQ       |      [mq.tianji.com](https://mq.tianji.com)      |    tjxt/123321     | 15672 |
|    Nacos Console     |   [nacos.tianji.com](https://nacos.tianji.com)   |    nacos/nacos     | 8848  |
|   XXL-Job Console    |  [xxljob.tianji.com](https://xxljob.tianji.com)  |    admin/123456    | 8880  |
|  ES Kibana Console   |      [es.tianji.com](https://es.tianji.com)      |         -          | 5601  |
| Microservice Gateway |     [api.tianji.com](https://api.tianji.com)     |         -          | 10010 |
|    Student Portal    |     [www.tianji.com](https://www.tianji.com)     |         -          | 18081 |
|     Admin Portal     |  [manage.tianji.com](https://manage.tianji.com)  |         -          |       |

## Project Operation & Maintenance Process

Submit code to Gogs --> Notify Jenkins --> Jenkins pulls code --> Automatic build --> Automatic deployment --> Automatic testing (script-based)







# 星瀚学堂

## 项目简介：

星瀚学堂是一个基于微服务架构的生产级在线教育项目，面向成年人的非学历职业技能培训。分为学生端和管理端两部分。项目中主要包含有学习服务、优惠券服务、课程推荐AI Agent等。是“天机学堂”的进一步实现和改进版。本仓库为后端仓库

## 技术栈：

SpringCloud Alibaba、SSM、Redis/Redisson、RabbitMQ、Mysql分库分表、XXL-Job、Spring AI等

## 项目负责（核心功能）

🆕 已完成：

1. 负责实现学习服务，基于Redis合并写请求和DelayQueue实现断点续播功能，优化高并发的数据库写业务，使误差控制在15秒内。
2. 负责优惠券管理功能，发放优惠券时利用按位加权求和算法和异步线程生成兑换码，并利用BitMap验证兑换码是否已经兑换。保证了兑换码的可读性、不可重兑、防爆刷和高效性。
3. 负责优惠券的领取功能，利用乐观锁和分布式锁Redisson解决并发安全问题，解决事务边界原因导致的锁失效问题，通过aspectj动态代理解决事务失效问题。
4. 负责实现通用分布式锁的封装，基于AOP、自定义注解、工厂模式和策略模式实现。
5. 负责优惠券的使用，通过查询所有可用优惠券，经过初筛、细筛、排列组合计算出所有可用优惠券组合，并基于CompleteableFuture并行计算每种组合的优惠明细，最后按照规则筛选出最优解。



⏳ 开发计划

1. 设计并实现问答评论模块，根据用户选择的匿名与否，记录问答或者评论信息，并产生对应的积分，通过RabbitMQ推送给积分系统。
2. 点赞服务的搭建与实现，用户前端发送点赞请求到达点赞服务，点赞服务负责存储点赞记录与点赞数量，并通过定时任务发送MQ消息通知业务方更新点赞数量。
3. 签到功能实现与优化，基于BitMap数据结构存储签到记录，通过MQ推送签到信息及积分到积分服务。
4. 积分排行榜功能实现，利用Redis的Zset存储本月实时排行榜数据。通过XXL-Job分片任务持久化历史榜单到Mysql数据库中，Mysql采用的是分库分表，利用MybatisPlus的动态表名来计算表名。
5. 完成langchain智能体模块。

## 项目进度

基于“天机学堂”基础版本，一些功能没做

相关微服务及1.0.0版本的完成状态如下：

| 微服务名称   | 功能描述        | 完成状态        |
| ------------ | --------------- | --------------- |
| tj-parent    | 父工程          | ✅ 已完成        |
| tj-api       | feign抽取       | 🆕已完成（完善） |
| tj-common    | 通用工程        | 🆕已完成（完善） |
| tj-message   | 消息中心        | ✅ 已完成        |
| tj-gateway   | 网关            | 🆕已完成（完善） |
| tj-auth      | 权限服务        | 🆕已完成（完善） |
| tj-user      | 用户服务        | ✅ 已完成        |
| tj-pay       | 支付服务        | ✅ 已完成        |
| tj-course    | 课程服务        | 🆕已完成（完善） |
| tj-exam      | 考试服务        | ⏳ 开发中        |
| tj-search    | 搜索服务        | ✅ 已完成        |
| tj-trade     | 交易服务        | 🆕已完成（完善） |
| tj-learning  | 学习服务        | 🆕已完成（新增） |
| tj-promotion | 促销服务        | 🆕已完成（新增） |
| tj-media     | 媒资服务        | ✅ 已完成        |
| tj-data      | 数据服务        | ⏳ 开发中        |
| tj-remark    | 评价服务        | ⏳ 开发中        |
| tj-agent     | langchain智能体 | ⏳ 开发中        |


## 项目域名列表

| 名称             | 域名               | 账号密码     | 端口  |
| ---------------- | ------------------ | ------------ | ----- |
| Git私服          | git.tianji.com     | tjxt/123321  | 10880 |
| Jenkins持续集成  | jenkins.tianji.com | root/123     | 18080 |
| RabbitMQ         | mq.tianji.com      | tjxt/123321  | 15672 |
| Nacos控制台      | nacos.tianji.com   | nacos/nacos  | 8848  |
| xxl-job控制台    | xxljob.tianji.com  | admin/123456 | 8880  |
| ES的Kibana控制台 | es.tianji.com      | -            | 5601  |
| 微服务网关       | api.tianji.com     | -            | 10010 |
| 用户端入口       | www.tianji.com     | -            | 18081 |
| 管理端入口       | manage.tianji.com  | -            |       |

## 项目运维流程

提交代码到gogs-->通知jenkins-->jenkins拉取代码-->自动构建-->自动部署-->自动测试（基于脚本）
