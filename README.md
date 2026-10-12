<div align="center">

# 适用于Marble（Redmi Note 12 Turbo）的GKI内核

几乎完美的DroidSpaces支持

## 已添加以下内核构建选项
```
enable_config CONFIG_USER_NS
enable_config CONFIG_NAMESPACES
enable_config CONFIG_NET_NS
enable_config CONFIG_UTS_NS
enable_config CONFIG_CGROUP_DEVICE
```

## 推荐构建配置

| 构建选项                      | 内容                      | 建议                                |
| ------------------------- | ----------------------- | --------------------------------- |
| 内核版本                      | 5.10                    | 必须                                |
| 安全补丁级别                    | 2025-05<br>或<br>2025-06 | 更新的版本在Marble上可以进系统，但闪屏，可能需要清除Data |
| Droidspaces<br>容器支持       | 678                     | 345可以进入系统但是会自动重启，应该是槽位覆盖厂商配置导致的   |
| KPM                       | 开启                      |                                   |
| NTSync支持                  | 开启                      |                                   |
| ZRAM增强算法                  | 开启                      |                                   |
| BBG防格机                    | 关闭                      | 稳定性问题                             |
| Re-Kernel驱动               | 关闭                      | 稳定性问题                             |
| CVE-2026-43499 rtmutex 修复 | 开启                      | 必须                                |
| 禁用 SUSFS                  | 开启                      | 必须                                |


# 以下是原项目说明
### 🏮 2026 🐎 Happy New Year! 🏮

**自动化构建 GKI 内核 | 集成 KernelSU + SUSFS**

[![Release](https://img.shields.io/github/v/release/zzh20188/GKI_KernelSU_SUSFS?label=Release&style=flat-square&logo=github&logoColor=white&color=2ea44f)](https://github.com/zzh20188/GKI_KernelSU_SUSFS/releases)
[![Coolapk](https://img.shields.io/badge/Follow-Coolapk-3DDC84?style=flat-square&logo=android&logoColor=white)](http://www.coolapk.com/u/11253396)
[![KernelSU](https://img.shields.io/badge/KernelSU-Supported-5AA300?style=flat-square)](https://kernelsu.org/)
[![SUSFS](https://img.shields.io/badge/SUSFS-Integrated-E67E22?style=flat-square)](https://gitlab.com/simonpunk/susfs4ksu)

[**English**](README-EN.md) | 简体中文

---

</div>

## 🚀 快速导航

- 📖 [文档](https://github.com/zzh20188/GKI_KernelSU_SUSFS/wiki)
- 📥 [下载](https://github.com/zzh20188/GKI_KernelSU_SUSFS/releases)
- 🔰 [教程](https://zzh20188.github.io/GKI_KernelSU_SUSFS/guide.html)

---

## 最近更新

1. 并行工作流磁盘清理，增加整体速度
2. 修复拉取源码、仓库、工具概率失败的问题
3. 同步上游SUSFS更新，兼容不被支持的GKI版本
4. 翻新网页UI风格
5. RELEASE 新上传 SUSFS补丁，对应 **上游的 `50_add_susfs_in_gki-内核版本.patch`和其他文件**（除了 `10_enable_susfs_for_ksu.patch`，它已被 sukisu 内置），可替代使用，不会产生SUSFS侧的报错，不会构建内核则不需要,通常在源码目录拉取sukisu然后执行本补丁，就可运行构建脚本或bash命令进行了，省略很多步骤
6. 新增 **NoMount 挂载元模块**（构建时可选开关）：在内核 `fs/` 层集成 [maxsteeel/NoMount](https://github.com/maxsteeel/nomount)，提供无需传统挂载点的模块挂载方案，可与任意 KSU 变体及 SUSFS 共存。开启后需自行刷入配套的 NoMount 模块使用
7. 新增 **网络增强**（构建时可选开关，默认关闭）：BBRv3 等网络功能增强

## ⚠️ 兼容性提醒

> **注意：** 目前不支持一加 ColorOS 14、15，刷入后可能需要清除数据开机。
>
> **SUKISU最新版:** 已经恢复构建，但不兼容6.12
>
> 增加了老版本SukiSU的构建，若使用老版本内核最好搭配同样版本的管理器，老版本完全使用以前的SUKISU和SUSFS代码，因此不包含最近的特性或bug
> 
> <img width="296" height="152" alt="image" src="https://github.com/user-attachments/assets/e60316c3-c760-4178-a4c8-b94d0ef0b5b2" />



---

## 📚 文档与指南

详细说明请查阅 [**GitHub Wiki（中英双语）**](https://github.com/zzh20188/GKI_KernelSU_SUSFS/wiki)

Wiki 涵盖内容：
- [**🔰 教程**](https://zzh20188.github.io/GKI_KernelSU_SUSFS/guide.html)
- 📥 下载/刷入内核
- 💡 使用技巧 Tips
- 🆘 救砖指南
- 📊 内核版本兼容性说明
- 🧩 [**进阶功能文档**](docs/advanced-features.md)：GhostLock 安全修复、Droidspaces 容器支持、自定义提交配置、伪装 `/proc/config.gz`

---

## 🛠️ 安装后推荐

### 📦 模块推荐

<table>
<tr>
<th>模块名称</th>
<th>仓库</th>
<th>频道</th>
</tr>
<tr>
<td><b>LSPosed-Irena</b></td>
<td><a href="https://github.com/re-zero001/LSPosed-Irena">GitHub</a></td>
<td><a href="https://t.me/lsposed_irena">Telegram</a></td>
</tr>
<tr>
<td><b>Zygisk Next</b></td>
<td><a href="https://github.com/Dr-TSNG/ZygiskNext">GitHub</a></td>
<td rowspan="2"><a href="https://t.me/real5ec1cff">Telegram</a></td>
</tr>
<tr>
<td><b>TrickyStore</b></td>
<td><a href="https://github.com/5ec1cff/TrickyStore">GitHub</a></td>
</tr>
</table>

### 🔧 Xposed 模块

| 模块 | 说明 |
|:---:|:---|
| **FuseFixer** | [Unicode零宽修复模块](https://t.me/real5ec1cff/268) |

### App

| 名称 | 说明 |
|:---:|:---|
| **Scene** | [官网](https://omarea.com/#/) |
---

<div align="center">

**更多内容持续更新中...**

⭐ 如果这个项目对你有帮助，请点个 Star 支持一下！

</div>
