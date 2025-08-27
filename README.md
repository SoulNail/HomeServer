# 家庭服务器与网络项目 | harukaze

本仓库记录并开源我的家庭网络与服务器最佳实践，包括网络拓扑、反向代理、DDNS、OpenVPN、以及在 192.168.110.51 上基于 Docker 部署的服务：Aria2Pro、FileCodeBox、Home Assistant、Project Zomboid 专用服务器、Sunpanel 导航页。

- 域名：harukaze.xxx（暂时不漏）
- DDNS：OpenWrt 上 ddns-go
- 远程访问：OpenVPN（主路由下发一键回家）
- 旁路由：OpenWrt（192.168.110.2）
- 服务器：192.168.110.51（Docker）
- 内网：192.168.110.0/24，由主路由负责
- 光猫：192.168.1.1，主路由 WAN 获得 192.168.1.2

特色
- 真实网络拓扑与实战配置
- 生产可用的 Docker Compose 与配置
- 安全基线与备份恢复脚本
- CI 校验与文档规范

拓扑概览
- 光猫 192.168.1.1
  - 主路由 WAN: 192.168.1.2 -> LAN: 192.168.110.0/24
    - 旁路由 OpenWrt: 192.168.110.2（ddns-go, OpenVPN）
    - 服务器: 192.168.110.51（Docker 与全部服务）
- 远程访问：OpenVPN 拨入 -> 访问内网资源或经反代访问服务

文档导航
- docs/00-overview.md 项目说明
- docs/01-network-topology.md 网络拓扑与地址规划
- docs/02-host-setup.md 服务器初始化
- docs/03-security.md 安全基线
- docs/04-containers.md Docker 与 Compose
- docs/05-domain-ddns.md 域名与 DDNS（ddns-go）
- docs/06-vpn-remote-access.md OpenVPN 一键回家


安全提醒
- 默认不暴露管理面板到公网。公开服务需经反向代理 + TLS + 认证。
- VPN 优先，公网暴露请谨慎，务必开启限流与 Fail2ban。
