# Elasticsearch 索引服务 Release Notes

本页列出 Elasticsearch 索引服务的 Release Notes，便于您了解各版本的演进路径和特性变化。

## v0.4.0

发布日期：2022-12-25

### API

- **新增** `mcamel-elasticsearch` 获取集群已经分配的 NodePort 列表接口。
- **新增** `mcamel-elasticsearch` 增加状态详情。
- **新增** `mcamel-elasticsearch` 节点亲和性配置。
- **修复** `mcamel-elasticsearch` 修复 kb 不存在时候，删除会失败的 BUG。  
- **修复** `mcamel-elasticsearch` 修复 es exporter 离线失效的问题。  
- **修复** `mcamel-elasticsearch` 修复 es 创建成功后没有返回 ports 信息的 bug。
- **修复** `mcamel-elasticsearch` 查询实例列表和详情时，Kibana 的服务类型不符合预期。
- **优化** `mcamel-elasticsearch` 可以展示公共的 es，纳管之前是不可以删除的。  
- **优化** `mcamel-elasticsearch` 增加健康状态返回。  

## v0.3.6

发布日期：2022-11-28

- **改进** 密码校验调整为 MCamel 中等密码强度
- **改进** 角色可以升级
- **新增** 新增 sc 扩容提示
- **新增** 返回列表或者详情时的公共字段
- **新增** 返回告警
- **新增** 校验 Service 注释
- **修复** 更新实例后，集群使用了错误的镜像，导致集群状态异常
- **修复** 使用 NodePort 时，更新实例报错
- **升级** 中依赖的 eck operator 版本为 2.3.0
- **优化** 在某些版本的 K8s 集群中，默认 FD 不足，无法启动的问题
- **优化** 减小 elasticsearch 容器的运行权限

## v0.3.4

发布日期：2022-10-28

### API

- **新增** 同步 pod 状态到实例详情页
- **优化** workspace 界面逻辑调整
- **优化** 不符合设计规范的样式调整
- **优化** password 获取逻辑调整
- **优化** cpu&内存请求量应该小于限制量逻辑调整
- **优化** 实例版本不允许修改，下拉框应该为文本
- **修复** 更新实例服务设置，确认无反应，无法提交
- **新增** 获取用户列表接口
- **新增** 支持 arm 架构

## v0.3.2

发布日期：2022-9-25

### API

- **新增** 列表页增加分页功能
- **新增** 增加修改配置的功能
- **新增** 增加返回可修改配置项的功能
- **新增** 更改创建实例的限制为集群级别，原来为 namespace 级别
- **新增** 增加监控地址的拼接功能
- **新增** 增加可以修改版本号的功能
- **新增** 修改底层 update 逻辑为 patch 逻辑
- **新增** 将时间戳 api 字段统一调整为 int64
- **新增** 单测覆盖率提升到 43%
- **新增** 对接全局管理增加 workspace 接口
- **新增** 对接 insight 通过 crd 注入 dashboard
- **新增** 更新 release note 脚本，执行 release-process 规范

### 安装

- **新增** 支持 helm 部署 eck-operator
- **新增** 支持 helm 部署 mcamel-elasticsearch 服务

### 文档

- **新增** 第一次文档网站发布
- **新增** 功能说明
- **新增** 产品优势
- **新增** 什么是 Elasticsearch
- **新增** 基本概念
- **新增** 集群容量规划
