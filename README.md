# 家庭服务器与网络项目 | harukaze.site

本仓库记录并开源我的家庭网络与服务器最佳实践，包括网络拓扑、反向代理、DDNS、OpenVPN、以及在 192.168.110.51 上基于 Docker 部署的服务：Aria2Pro、FileCodeBox、Home Assistant、Project Zomboid 专用服务器、Sunpanel 导航页。

- 域名：harukaze.site
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
- docs/07-reverse-proxy.md Traefik 反向代理与证书
- docs/08-backup-restore.md 备份与恢复
- docs/09-monitoring.md 监控与日志
- docs/10-troubleshooting.md 故障排查

安全提醒
- 默认不暴露管理面板到公网。公开服务需经反向代理 + TLS + 认证。
- VPN 优先，公网暴露请谨慎，务必开启限流与 Fail2ban。

LICENSE
MIT License

Copyright (c) 2025 harukaze

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.