# Kapacitor for TOS 7

Kapacitor 使用 TICKscript 处理时序数据、检测异常并触发告警。此安装包使用 Kapacitor 1.8.9 官方镜像，支持 x86_64 和 aarch64 TNAS。[Kapacitor 文档](https://docs.influxdata.com/kapacitor/v1/) · [官方镜像](https://hub.docker.com/_/kapacitor)

## 首次使用

1. 在 TOS 安装 Docker Engine 后启动 Kapacitor。使用默认的 HTTP API，地址为 `http://<NAS-IP>:9092`。默认连接无需登录，请用 NAS 防火墙只允许可信客户端访问该端口。
2. 使用 Kapacitor CLI 或 HTTP API 定义并启用一个流任务，指定任务的数据库和保留策略。例如，给任务配置 `metrics.autogen` 后，将 InfluxDB 行协议数据 POST 到 `http://<NAS-IP>:9092/write?db=metrics&rp=autogen`。[快速入门](https://docs.influxdata.com/kapacitor/v1/introduction/getting_started/) · [HTTP API](https://docs.influxdata.com/kapacitor/v1/working/api/)
3. 需要 InfluxDB 批量查询、输出或订阅时，在应用的容器配置中设置 `KAPACITOR_INFLUXDB_0_ENABLED=true`、`KAPACITOR_INFLUXDB_0_URLS_0` 和对应凭据，再重建容器。类型、凭据和订阅模式取决于 InfluxDB 版本。使用 Chronograf 时，可在其连接设置中填入 Kapacitor 地址。[配置参数](https://docs.influxdata.com/kapacitor/v1/administration/configuration/)

## 数据与备份

容器内的 `/var/lib/kapacitor` 对应 TOS 应用数据目录，包含数据库、任务和回放文件。备份前在 TOS 停止应用，再复制 Docker 管理器中显示的宿主挂载目录，并保留原权限。

[安装包与 SHA-256 校验文件](https://github.com/LuYifei-TOS-Apps/tos-kapacitor/releases) · [上游项目](https://github.com/influxdata/kapacitor)
