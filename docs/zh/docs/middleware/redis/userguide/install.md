# 安装 Redis

因为 Redis 分属于 DCE 5.0 的应用层，所以需要先准备一个 DCE 环境。

按照以下步骤安装 Redis。

## 安装 redis-operator

1. 在左侧导航栏点击`容器管理` -> `集群列表`。

    ![集群列表](../images/install01.png)

2. 选择要安装 Redis 的集群，点击集群名称。

    ![点击集群名称](../images/install02.png)

3. 在左侧导航栏点击 `Helm 应用` -> `Helm 模板`，在搜索框中输入 `redis`，敲击回车键，点击 Redis 磁贴卡片。

    ![找到 redis](../images/install03.png)

4. 选择合适版本后，点击`安装`按钮。也可以遵循黑色区域的文字提示，从命令行安装。

    ![选择版本安装](../images/install04.png)

5. 输入合适的名称，选择命名空间和版本后，点击`确定`。也可以在底部配置 YAML 来安装。

    ![点击确定](../images/install05.png)

6. 系统返回 `Helm 应用`列表，屏幕提示创建成功，刷新页面后刚刚创建的应用位于第一个。

    ![查看](../images/install06.png)

## 安装 mcamel-redis

1. 配置仓库。

    ```bash
    helm repo add mcamel-release https://release.daocloud.io/chartrepo/mcamel
    helm repo update
    ```

2. 查看版本。

    ```bash
    helm search repo mcamel-release/mcamel-redis --versions
    NAME                            CHART VERSION   APP VERSION     DESCRIPTION
    mcamel-release/mcamel-redis     0.1.3           0.1.3           A Helm chart for Kubernetes
    ```

3. 安装和升级。

    ```bash
    helm upgrade --install mcamel-redis --create-namespace -n mcamel-system --cleanup-on-fail \
      --set global.mcamel.imageTag=v0.1.3 \
      --set global.imageRegistry=release.daocloud.io \
    mcamel-release/mcamel-redis \
      --version 0.1.3
    ```

    参数说明：

    ```bash
    --set ui.image.tag: 指定前端镜像版本
    --set ghippo.createCrd: 注册 ghippo 路由，默认开启
    --set insight.serviceMonitor.enabled: 开启监控，默认开启
    --set insight.grafanaDashboard.enabled: 开启监控面板，默认开启

    # 全局参数
    --set global.mcamel.imageTag: mcamel-redis 镜像版本
    --set global.imageRegistry: 镜像仓库地址
    ```

## 卸载

卸载时先卸载 mcamel-redis，再删除 redis-operator，释放相关资源。

### 卸载 mcamel-Redis

```bash
helm uninstall mcamel-redis -n mcamel-system
```

### 删除 redis-operator

1. 在 Helm 应用列表中，点击最右侧的 `⋮`，在弹出菜单中选择`删除`。

    ![选择删除](../images/uninstall01.png)

2. 在弹窗中输入要删除的名称，确认无误后，点击`删除`。

    ![点击删除](../images/uninstall02.png)

## 安装参数说明

| 键 | 类型 | 默认值 | 说明 |
|-----|------|---------|-------------|
| apiServer.affinity | object | `{}` |  |
| apiServer.image.pullPolicy | string | `"IfNotPresent"` |  |
| apiServer.image.registry | string | `"release.daocloud.io"` |  |
| apiServer.image.repository | string | `"mcamel/mcamel-redis-apiserver"` |  |
| apiServer.image.tag | string | `"v0.0.1"` |  |
| apiServer.imagePullSecrets | list | `[]` |  |
| apiServer.livenessProbe.enabled | bool | `true` |  |
| apiServer.livenessProbe.failureThreshold | int | `3` |  |
| apiServer.livenessProbe.initialDelaySeconds | int | `30` |  |
| apiServer.livenessProbe.periodSeconds | int | `30` |  |
| apiServer.livenessProbe.scheme | string | `"HTTP"` |  |
| apiServer.livenessProbe.successThreshold | int | `1` |  |
| apiServer.livenessProbe.timeoutSeconds | int | `5` |  |
| apiServer.nodeSelector | object | `{}` |  |
| apiServer.podAnnotations | object | `{}` |  |
| apiServer.podSecurityContext | object | `{}` |  |
| apiServer.readinessProbe.enabled | bool | `true` |  |
| apiServer.readinessProbe.failureThreshold | int | `3` |  |
| apiServer.readinessProbe.initialDelaySeconds | int | `30` |  |
| apiServer.readinessProbe.periodSeconds | int | `30` |  |
| apiServer.readinessProbe.scheme | string | `"HTTP"` |  |
| apiServer.readinessProbe.successThreshold | int | `1` |  |
| apiServer.readinessProbe.timeoutSeconds | int | `5` |  |
| apiServer.replicaCount | int | `1` |  |
| apiServer.resources | object | `{}` |  |
| apiServer.securityContext | object | `{}` |  |
| apiServer.service.grpcPort | int | `8090` |  |
| apiServer.service.grpcProtocol | string | `"TCP"` |  |
| apiServer.service.grpcTargetPort | int | `8090` |  |
| apiServer.service.httpPort | int | `8080` |  |
| apiServer.service.httpProtocol | string | `"TCP"` |  |
| apiServer.service.httpTargetPort | int | `8080` |  |
| apiServer.service.type | string | `"ClusterIP"` |  |
| apiServer.tolerations | list | `[]` |  |
| ghippo.createCrd | bool | `false` |  |
| ghippo.version | string | `"v0.1.3"` |  |
| global.imagePullSecrets | list | `[]` |  |
| global.imageRegistry | string | `""` |  |
| global.mcamel.imageTag | string | `""` |  |
| insight.grafanaDashboard.enabled | bool | `false` |  |
| insight.grafanaDashboard.metadataLabels | string | `"insight"` |  |
| insight.serviceMonitor.enabled | bool | `false` |  |
| insight.serviceMonitor.metadataLabels | string | `"insight"` |  |
| insight.serviceMonitor.name | string | `"mcamel-redis"` |  |
| insight.serviceMonitor.selectorMatchLabels | string | `"redis"` |  |
| ui.affinity | object | `{}` |  |
| ui.enabled | bool | `true` |  |
| ui.image.pullPolicy | string | `"IfNotPresent"` |  |
| ui.image.registry | string | `"release.daocloud.io"` |  |
| ui.image.repository | string | `"mcamel/mcamel-redis-ui"` |  |
| ui.image.tag | string | `"v0.0.1"` |  |
| ui.imagePullSecrets | list | `[]` |  |
| ui.nodeSelector | object | `{}` |  |
| ui.podAnnotations | object | `{}` |  |
| ui.podLabels | object | `{}` |  |
| ui.replicaCount | int | `1` |  |
| ui.resources | object | `{}` |  |
| ui.service.port | int | `80` |  |
| ui.service.type | string | `"ClusterIP"` |  |
| ui.tolerations | list | `[]` |  |
