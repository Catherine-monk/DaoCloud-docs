# Redis 缓存服务 Release Notes

本页列出 Redis 缓存服务的 Release Notes，便于您了解各版本的演进路径和特性变化。

## v0.4.0

发布日期：2022-12-25

### API

- **新增** `mcamel-redis` NodePort 端口冲突提前检测。
- **新增** `mcamel-redis` 节点亲和性配置。
- **修复** `mcamel-redis` 单例和集群设置 nodeport 无效的问题。
- **修复** `mcamel-redis` 集群模式下，从节点不可以设置为 0 的问题。

## v0.2.6

发布日期：2022-11-28

### API

- **修复** 更新 Redis 时校验部分字段错误
- **改进** 密码校验调整为 MCamel 低等密码强度
- **改进** 提升哨兵模式的版本依赖，v1.1.1=>v1.2.2，重要变更为支持 k8s 1.25+
- **新增** 支持在 ARM 环境安装主备模式的 Redis 集群
- **新增** sc 扩容提示
- **新增** 返回列表或者详情时的公共字段
- **新增** 增加返回告警列表
- **新增** 校验 Service 注释
- **修复** 服务地址展示错误

## v0.2.2

发布日期：2022-10-26

### API

- **新增** 获取用户列表接口
- **新增** 支持 arm 架构
- **新增** redis 实例全生命周期的管理
- **新增** redis 实例的监控部署
- **新增** 支持 redis 哨兵，单例和集群一键部署
- **新增** 支持 ws 权限隔离
- **新增** 支持在线动态扩容
- **升级** release notes 脚本
