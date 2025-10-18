# TeslaMate Portable for Windows

[English](#english) | [中文](#中文)

---

## 中文

### 这是什么？

这是一个 Windows版 **开箱即用**的 TeslaMate 便携版本，专为懒惰的，或者不熟悉 Docker 或命令行的特斯拉车主打包使用。

我最初打包原因是，能运行Docker的游戏主机等都不方便24*7常年不断电运行，而能常年运行的服务器/云主机等又无法安装Docker，加上teslamate数据迁移非常麻烦，所以把它整个便携化

### 特点

- ✅ **一键运行** - 无需安装 Docker 或任何依赖
- ✅ **完全便携** - 可放在 U 盘中随身携带
- ✅ **资源占用低** - 仅占用约 350MB 内存，CPU 使用率接近 0%
- ✅ **兼容性强** - 支持几乎所有 Windows x64 系统（包括 Windows Server）

### 快速开始

1. **下载并解压** release 中的 ZIP 文件
2. **运行** `run.bat` - 程序将在后台持续运行
3. **等待约 2 分钟**后访问:
   - `http://localhost:3000` - 主界面（初始账号: `admin` / `admin`）
   - `http://localhost:4000` - Teslamate界面
4. **首次使用**: 运行 `tesla_auth` 为 4000 端口添加车辆授权

详细使用说明请参考 [TeslaMate 官方文档](https://docs.teslamate.org)

### 高级选项

- 可自行编辑 `run.bat` ，可添加到开机启动项、转换为 Windows 服务、或加入计划任务等。
- 运行 `run_admin.bat` 打开管理模式（提供 GUI 窗口和 SSH 22 访问，root 无密码）

### ⚠️ 安全提示

1. **网络暴露**: 运行后本机的 3000 和 4000 端口会对网络开放。建议:
   - 在自己信得过的局域网内运行，或者
   - 配置路由器防火墙规则
   
2. **数据安全**: 
   - 所有数据和车辆密钥都存储在本地文件夹中
   - 请妥善保管，切勿丢失
   - **不要在多台机器上同时运行同一份软件**

3. **管理模式风险**: `run_admin.bat` 会开放 SSH 22 端口且 root 无密码，仅在需要高级配置、备份还原等时使用

### 运行原理

```
run.bat → QEMU (最小化特性) → Alpine Linux（最小安装） → Docker → TeslaMate + MCU2
```

- 初始内存占用: ~1GB
- 稳定后内存占用: ~350MB (virtio_balloon 生效后)
- CPU 占用: 接近 0%

### 许可证与致谢

本项目仅是将以下开源项目的源文件打包在一起，**所有版权和许可证归原作者所有**:

- [TeslaMate](https://github.com/teslamate-org/teslamate) - MIT License
- [QEMU](https://www.qemu.org/) - GPL License
- [Alpine Linux](https://alpinelinux.org/) - Various open source licenses
- [Docker](https://www.docker.com/) - Apache License 2.0

本打包项目没有对原项目文件和许可证做任何更改，也不对任何功能、安全性或稳定性负责。

---

## English

### What is this?

A **1-click-ready-to-use** Windows portable version of TeslaMate for lazy folks / Tesla owners unfamiliar with Docker or command-line tools.

(I originally created this package because dockerable gaming PCs can't run 24/7 for continuous monitoring, while servers and cloud hosts that can run 24/7 often can't install Docker. Plus, TeslaMate data migration is quite cumbersome, so I made the entire things portable.)

### Features

- ✅ **One-Click Runs** - No Docker or dependencies installation required
- ✅ **Fully Portable** - Run from USB drive, take it anywhere
- ✅ **Low Resource Usage** - Only ~350MB RAM, near 0% CPU usage
- ✅ **Wide Compatibility** - Works on almost all Windows x64 systems (including Windows Server)

### Quick Start

1. Download and extract the ZIP
2. **Run** `run.bat` - The application will run persistently in the background
3. **Wait ~2 minutes** then access:
   - `http://localhost:3000` - Dashboard (initial credentials: `admin` / `admin`)
   - `http://localhost:4000` - TeslaMate
4. **First-time setup**: Run `tesla_auth` to authorize your vehicle on port 4000

For detailed usage, please refer to [TeslaMate Official Documentation](https://docs.teslamate.org)

### Advanced Options

- Edit `run.bat` as you wish, add to Windows startup, convert to Windows service, or schedule via Task Scheduler, etc.
- Run `run_admin.bat` to enable admin mode (provides GUI window and SSH port 22 access with no root password)

### ⚠️ Security Warnings

1. **Network Exposure**: Ports 3000 and 4000 will be accessible on your network. Recommendations:
   - Run on a trusted LAN only, or
   - Configure router firewall
   
2. **Data Security**: 
   - All data and vehicle tokens are stored in this one local folder!!!
   - Keep it safe
   - **Never run the same copy on multiple machines simultaneously**

3. **Admin Mode Risk**: `run_admin.bat` opens SSH port 22 with no root password - use only when advanced configuration, backup, or restoration is needed

### How It Works

```
run.bat → QEMU (minimal features) → Alpine Linux (minimal install) → Docker → TeslaMate + MCU2
```

- Initial memory: ~1GB
- Stabilized memory: ~350MB (after virtio_balloon kicks in)
- CPU usage: Near 0%

### License & Credits

This project simply packages the source files of the following open-source projects together. **All copyrights and licenses belong to their original authors**:

- [TeslaMate](https://github.com/teslamate-org/teslamate) - MIT License
- [QEMU](https://www.qemu.org/) - GPL License
- [Alpine Linux](https://alpinelinux.org/) - Various open source licenses
- [Docker](https://www.docker.com/) - Apache License 2.0

This packaging project has not modified any original project files or licenses, and assumes no responsibility for any functionality, security, or stability.

---

### Support

- TeslaMate Issues: [teslamate-org/teslamate](https://github.com/teslamate-org/teslamate/issues)
- TeslaMate Documentation: [docs.teslamate.org](https://docs.teslamate.org)

For issues specific to this portable package, please open an issue in this repository.
