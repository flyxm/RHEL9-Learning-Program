# ISO 和必备工具信息

此目录作为各种必备 ISO 镜像、安装程序和工具的集中存储库，用于设置和使用 RHEL 9 学习计划环境。

## RHEL 9.6 DVD ISO 信息

*   **RHEL 9.6 x86_64 DVD ISO 下载链接:** `https://developers.redhat.com/content-gateway/file/rhel/Red_Hat_Enterprise_Linux_9.6/rhel-9.6-x86_64-dvd.iso`
    （下载需要 Red Hat 账户）

### RHEL 9.6 版本特性

Red Hat Enterprise Linux 9.6 在多个领域引入了一系列新特性和增强功能，重点关注开发者体验、安全性、虚拟化、自动化、网络和云集成。

主要亮点包括：

*   **开发者增强：** 支持更新版本的编程语言和框架（例如 PHP 8.3、NGINX 1.26），并包含新的核心语言特性和错误修复。
*   **安全改进：** 增强了安全功能，如加密 DNS、改进的 SELinux 策略、升级到 OpenSSL 3.2.2、集成 Landlock 模块以限制应用程序访问系统资源，以及对 DNS over TLS (DoT) 和 WireGuard 的实验性支持。

*   **虚拟化和容器：** 改进了与虚拟化技术（AMD SEV-SNP、Intel TDX）的兼容性，支持 ARM64 主机之间的虚拟机迁移，并更新了容器工具（Podman 5.4、QEMU 9.1.0）。
*   **自动化和管理：** 新增了用于管理 `sudo` 配置、使用 Aide 进行文件跟踪以及使用 `systemd` 控制用户驱动器的系统角色。包含了 OpenTelemetry 集成。
*   **网络：** 进步包括支持高级 LTE 调制解调器以及通过 `nmstate` 工具改进 IPvLAN 支持。
*   **云集成：** 针对云环境，特别是 AWS EC2 进行了优化，增强了内核、ENA 和 NVMe 支持，并启用了 `cloud-init` 进行自动化配置。
*   **通用系统增强：** 各种错误修复、技术改进以及更新的性能/调试工具。
*   **RHEL Lightspeed：** 一项新功能，结合 RHEL 专业知识与 AI，以协助 Linux 专业人员。

### 官方文档

如需详细信息、发行说明和全面的指南，请参阅 Red Hat 官方文档：

*   **RHEL 9.6 发行说明：** [https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html/9.6_release_notes/index](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html/9.6_release_notes/index)
*   **Red Hat Enterprise Linux 文档门户：** [https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9)
*   **Red Hat Enterprise Linux 9.6 新特性 (Red Hat 博客)：** [https://www.redhat.com/en/blog/whats-new-red-hat-enterprise-linux-96](https://www.redhat.com/en/blog/whats-new-red-hat-enterprise-linux-96)

## 必备软件和工具

### 1. VMware Workstation Pro

*   **版本:** 17.5+
*   **来源:** 官网试用或商业许可证。

### 2. Windows 终端 / PowerShell

*   **来源:** 最新版本来自 Microsoft Store。
*   **PowerShell 版本:**
    *   **Major 5.x:** Windows PowerShell (Win10/11 默认)
    *   **Major 7.x:** PowerShell Core / PowerShell 7 (需自行安装)
*   **检查版本:** `$PSVersionTable.PSVersion`

### 2.1. 在 Windows 11 上安装 PowerShell 7.x（PowerShell Core）

**一键 MSI 安装（推荐）**
1.  下载 x64 MSI: [https://github.com/PowerShell/PowerShell/releases/download/v7.5.2/PowerShell-7.5.2-win-x64.msi](https://github.com/PowerShell/PowerShell/releases/download/v7.5.2/PowerShell-7.5.2-win-x64.msi)
2.  双击 → 一路 Next → Install（默认路径 `C:\Program Files\PowerShell\7`）。
3.  打开 开始菜单 → PowerShell 7 或终端输入 `pwsh`。

**查看版本**
```powershell
pwsh --version
# 示例输出：PowerShell 7.5.2
```

**查看完整信息**
```powershell
$PSVersionTable
# 示例输出：
# Name                           Value
# ----                           -----
# PSVersion                      7.5.2
# PSEdition                      Core
# GitCommitId                    7.5.2
# OS                             Microsoft Windows 10.0.26100
# Platform                       Win32NT
# PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0…}
# PSRemotingProtocolVersion      2.3
# SerializationVersion           1.1.0.1
# WSManStackVersion              3.0
```

### 3. Git for Windows

*   **来源:** 最新版本来自 [git-scm.com](https://git-scm.com/)。提供 Git-Bash。

### 4. VS Code

*   **来源:** 最新版本来自 [code.visualstudio.com](https://code.visualstudio.com/)。远程编辑必备。