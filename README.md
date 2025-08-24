# HP Z2 SFF G8 Hackintosh OpenCore EFI

这是一个为 HP Z2 Small Form Factor G8 工作站定制的 macOS Hackintosh OpenCore EFI 配置。

## 🖥️ 硬件规格

- **型号**: HP Z2 Small Form Factor G8
- **处理器**: 6核 Intel Core i5 (CPU ID: EB060800)
- **机型仿冒**: MacPro7,1
- **核显**: Intel UHD 750 (已禁用)
- **网卡**: Intel 以太网
- **无线**: 支持博通无线网卡
- **蓝牙**: 支持博通蓝牙

## 🔧 OpenCore 版本

- **OpenCore**: 0.7.8+
- **配置版本**: 基于 OCC 2.78.0.2

## ✅ 功能状态

### 正常工作
- ✅ CPU 电源管理
- ✅ 以太网 (IntelMausi)
- ✅ 音频 (AppleALC)
- ✅ USB 端口 (定制化配置)
- ✅ 蓝牙 (博通)
- ✅ Wi-Fi (博通)
- ✅ 睡眠/唤醒
- ✅ NVRAM

### 已禁用
- ❌ Intel UHD 750 核显 (已禁用)

## 📁 EFI 结构

```
EFI/
├── BOOT/
│   └── BOOTx64.efi
└── OC/
    ├── ACPI/           # ACPI 补丁
    ├── Drivers/        # UEFI 驱动
    ├── Kexts/         # 内核扩展
    ├── Resources/     # OpenCore 资源文件
    ├── Tools/         # 工具
    └── config.plist   # 主配置文件
```

## 🛠️ 主要 Kexts

- **Lilu.kext** - 基础补丁平台
- **VirtualSMC.kext** - SMC 仿真
- **WhateverGreen.kext** - 显卡补丁
- **AppleALC.kext** - 音频驱动
- **IntelMausi.kext** - 以太网驱动
- **USBToolBox.kext** + **UTBMap.kext** - USB 端口定制
- **BrcmPatchRAM3.kext** - 蓝牙补丁
- **AirportBrcmFixup.kext** - Wi-Fi 补丁
- **RestrictEvents.kext** - 系统事件限制

## 🚀 使用说明

### 安装前准备
1. 下载最新的 macOS 安装程序
2. 准备至少 16GB 的 USB 启动盘
3. 备份原系统重要数据

### 安装步骤
1. 将 EFI 文件夹复制到 USB 启动盘的 EFI 分区
2. 从 USB 启动并安装 macOS
3. 安装完成后将 EFI 复制到硬盘的 EFI 分区

### 安装后优化
- 使用 Hackintool 验证系统状态
- 根据需要调整 config.plist 设置
- 生成独有的序列号和 UUID

## ⚠️ 注意事项

- 本配置专为 HP Z2 SFF G8 优化，其他机型请勿直接使用
- Intel UHD 750 核显已被禁用，需要独立显卡
- USB 端口已根据实际硬件定制，其他机型可能需要重新定制
- 安装前请确保 BIOS 设置正确

## 🔧 BIOS 设置建议

### 禁用
- Secure Boot
- Fast Boot
- Intel VT-d (可选)
- Intel SGX

### 启用
- Intel VT-x
- Above 4G Decoding
- Hyper-Threading
- EHCI/XHCI Hand-off

## 📝 更新日志

- **最新**: 增加 RestrictEvents.kext
- 设置 CPU 类型为 6核Intel Core i5
- 增加缺少的 USB 端口
- 添加 USBToolBox 定制 USB 端口
- 禁用内置 UHD750 核显

## 🤝 贡献

本配置基于社区贡献和测试优化而来。如果您有改进建议或遇到问题，欢迎提交 Issue 或 Pull Request。

## ⚖️ 免责声明

本项目仅供学习和研究使用。Hackintosh 违反 Apple 软件许可协议，请在购买正版 Mac 设备后使用 macOS。使用本配置造成的任何损失作者概不负责。

---

**致谢**: 感谢 Acidanthera 团队的 OpenCore 引导程序以及各位开发者的 Kext 驱动。