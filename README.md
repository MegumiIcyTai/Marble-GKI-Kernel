# 适用于Marble（Redmi Note 12 Turbo）的GKI内核

几乎完美的 DroidSpaces 支持

2026/11/04: 
1.已添加IPV6 NAT支持（DroidSpaces 7.0起支持NAT66）
2.已添加macvlan支持（DroidSpaces 7.0起支持macvlan，cli已支持，app内暂无入口）

## 内核构建选项

| 内核构建选项 | 作用                                 |
| ------------ | -------------------------------------- |
| `CONFIG_NAMESPACES`           | 命名空间支持的全局总开关             |
| `CONFIG_UTS_NS`           | 提供 UTS 命名空间，隔离 uname() 视图 |
| `CONFIG_USER_NS`           | 提供 用户命名空间，支持 UID/GID 映射 |
| `CONFIG_NET_NS`           | 提供 网络命名空间，隔离网络协议栈    |
| `CONFIG_CGROUP_DEVICE`           | 提供 cgroup 设备控制器，控制设备访问 |
| `CONFIG_IP6_NF_NAT`           | 为 IPv6 协议栈启用 NAT  功能框架     |
| `CONFIG_IP6_NF_TARGET_MASQUERADE`           | 提供 IPv6 下的 MASQUERADE 目标       |
| `CONFIG_MACVLAN`           | 允许基于 MAC 地址创建虚拟以太网接口  |

## 构建选项

Workflow: Android 内核构建-自定义

| 构建选项                                     | 内容                 |
| ---------------------------------------------- | ---------------------- |
| 内核版本                                     | 5.10                 |
| KernelSU 变体                                | SukiSU               |
| KernelSU / SUSFS 模式                        | 禁用SUSFS            |
| KPM 功能                                     | 开启                 |
| Droidspaces容器支持                          | 678                  |
| 构建产物上传模式                             | 仅上传AnyKernel3.zip |
| 安全补丁级别                                 | 2025-06              |
| 启用 ZRAM 增强算法                           | 开启                 |
| 启用 BBG 防格机                              | 关闭                 |
| 启用 Re-Kernel 驱动                          | 关闭                 |
| 启用 NoMount 挂载元模块                      | 关闭                 |
| 启用网络增强（BBRv3 / IPSet / Qdisc / CIFS） | 关闭                 |
| 应用 CVE-2026-43499 rtmutex 修复链           | 开启                 |
| 启用一加 8E 支持                             | 关闭                 |
| 启用 Droidspaces 容器 NTSync 支持            | 开启                 |
