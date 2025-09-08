# RHEL9 Learning Program

![image](Screenshots/redhat.png)<br>

## 项目概览

**RHEL9学习计划** 是一个全面、深入的 Red Hat Enterprise Linux (RHEL) 系统管理、自动化、安全和性能优化的学习与实践项目。本计划旨在通过系统化的学习路径，帮助用户从RHEL基础知识逐步进阶到高级管理、自动化运维、云原生集成以及架构设计等专家级水平。

## 项目目标

*   **系统化学习：** 提供一个结构化的90天学习路线，覆盖RHEL的各个方面。
*   **实践导向：** 强调动手实践，每个“天”都包含具体的任务和操作步骤。
*   **全面覆盖：** 涵盖RHEL基础、网络、存储、安全、性能、自动化、虚拟化、容器化、云集成、高可用性、故障排除等。
*   **DevOps与云原生：** 融入DevOps理念和云原生技术，适应现代IT运维趋势。
*   **专家级进阶：** 旨在帮助用户达到RHEL架构师或平台工程师的专业水平。

## 核心内容亮点

*   **90天学习路线：** 详细规划了从Day 1到Day 90的每日学习任务和知识点。
*   **自动化实践：** 深入学习Ansible，包括高级Playbook、Roles、Vault以及与Tower/AWX的集成。
*   **安全强化：** 涵盖SELinux、PAM、审计、内核安全、容器安全、零信任网络和供应链安全。
*   **性能优化：** 从系统级到应用级，包括CPU、内存、I/O、网络、JVM和数据库调优。
*   **云集成：** 探索RHEL在AWS、Azure、GCP等主流云平台上的部署与管理。
*   **容器化与虚拟化：** 掌握Podman、Buildah、Kubernetes、OpenShift、KVM、KubeVirt等技术。

## 90 天学习路线


* **学习目标 & 大纲**（说明今天要掌握什么、为什么要学、在生产中的意义。）
* **理论详解**（历史背景、核心原理、设计哲学、对比分析。）
* **实验环境**（详细到命令和截图步骤，新手可以照做。）
* **实验步骤与验证**（命令解释作用、原理、常见错误和排错方法。）
* **案例与扩展**（「架构设计 → 自动化部署 → 问题排查 → 最佳实践」、生产环境批量部署场景。）
* **面试题强化**（学到的内容转化为 表达能力 + 面试能力、给出 3 层次答案（基础版 / 进阶版 / 专家版），）
* **总结与输出成果**（整理成 可复用脚本、配置文件、文档模板。）
* **参考文献与延伸阅读**（官方文档、man page、书籍、社区文章。）


---

## 📅 RHEL 9 专家学习路线（90 天表格版）

### Week 1：系统与基础

| Day | 理论                                                        | 实验                                                    | 输出                                | 面试题                                             |
| --- | --------------------------------------------------------- | ----------------------------------------------------- | --------------------------------- | ----------------------------------------------- |
| 1   | Linux 启动流程：BIOS → GRUB2 → kernel → systemd；systemd target | Kickstart 自动安装 3 台 VM；修改 GRUB 默认启动为 multi-user.target | 提交 kickstart.cfg；截图（安装成功+GRUB 配置） | ① 请描述 Linux 启动过程？ ② systemd 和 SysV init 的区别是什么？ |
| 2   | 文件系统原理：inode、ext4 vs xfs；journaling 日志机制                  | 创建 ext4/xfs/vfat 文件系统；UUID 自动挂载；`tar/rsync` 备份 /home  | 实验报告：《文件系统与挂载》；`df -h` 截图         | ① 为什么生产推荐 UUID 挂载？ ② ext4 和 xfs 的主要区别？          |
| 3   | Linux 权限模型：DAC、ACL、SUID/SGID/SBIT；sudo 原理                 | 批量创建 50 用户；配置 ACL；设置 sudo 最小权限                        | 提交用户批量脚本；总结 sudo 策略               | ① chmod 4755 和 2755 有何区别？ ② 如何限制用户只能执行某些命令？     |
| 4   | 调度与进程管理：CFS 调度器、nice/priority；systemd unit 类型             | 写 hello.service；stress 模拟 CPU 负载；用 renice 调整优先级       | service 文件；日志截图                   | ① load average 是如何计算的？ ② systemd 如何处理服务依赖？      |
| 5   | 包管理：RPM 结构、GPG 签名、DNF 模块流                                 | 搭建本地 YUM 仓库；rpmbuild 打 nginx 包；切换 PHP 版本              | .repo 文件；.rpm 包；实验总结              | ① dnf 模块流解决了什么问题？ ② 如何排查 rpm 缺少依赖？              |
| 6   | 容器基础：cgroups、namespace；Podman 与 Docker 对比                 | 运行 ubi9 容器；挂载 /srv；buildah 构建 nginx 镜像                | Containerfile；镜像 ID；总结文档          | ① 容器为什么比虚拟机启动快？ ② Podman 与 Docker 有何区别？         |
| 7   | 周复盘：整合系统+服务+包管理                                           | 脚本一键部署 Web 服务（用户+nginx+fstab+systemd）                 | 周报：《RHEL9 基础环境构建》                 | ① 如何从零搭建一台企业 Web 服务器？                           |

---



## 项目目录结构

```
RHEL9-Learning-Program/
├── docs/                    # 所有文档的根目录
│   ├── RHEL 9 Virtual Lab.md #RHEL 9 Virtual Lab.md
│   ├── daily_plans/         # 每日优化计划文档（Day_01_... Day_90_...）
│   │   ├── Day_01_Optimized_RHEL_Plan.md
│   │   ├── Day_02_Optimized_RHEL_Plan.md
│   │   └── ...
│   │   └── Day_90_Optimized_RHEL_Plan.md
│   ├── manual_vm_deployment/ # 虚拟机手动部署相关文档
│   │   └── ...
│   └── README.md            # `docs`目录的README，说明文档结构和如何使用
├── ISO/                     # 必备 ISO 镜像、安装程序和工具的集中存储库
│   ├── rhel-9.6-x86_64-dvd.iso
│   ├──README.md
├── Screenshots/             # 存放所有截图
│   └── day0/                # 按日期或主题分类的截图子目录
│       └── ...
├── Scripts/                 # 存放所有脚本文件（PowerShell, Shell脚本等）
│   ├── check-day0.ps1
│   ├── Day0-Provision.ps1
│   └── ...
├── VMs/                     # 存放虚拟机配置文件和磁盘文件
│   ├── desktop9/
│   │   └── ...
│   ├── node9/
│   │   └── ...
│   └── server9/
│       └── ...
├── LICENSE                  # 项目的许可证文件
├── README.md                # 项目主README文件
```

## 如何使用本计划

所有每日学习计划的详细内容都存放在 `docs/daily_plans/` 目录下。您可以按照日期顺序逐一学习和实践。

1.  **克隆仓库：**
    ```bash
    git clone https://github.com/flyxm/RHEL9-Learning-Program.git
    cd RHEL9-Learning-Program
    ```
2.  **浏览文档：**
    *   从 `docs/daily_plans/Day_01_Optimized_RHEL_Plan.md` 开始。
    *   查阅 `docs/README.md` 以了解文档目录的详细结构。

## 先决条件

*   运行RHEL 9的虚拟机或物理机（推荐使用虚拟机，如VMware Workstation, VirtualBox）。
*   具备基本的Linux命令行操作知识。
*   对虚拟化和网络有初步了解。

## 贡献

我们欢迎并鼓励社区贡献！如果您有任何改进建议、发现错误或想添加新的内容，请参阅我们的 [CONTRIBUTING.md](CONTRIBUTING.md) 文件。

## 许可证

本项目采用 [MIT License](LICENSE) 开放源代码。

---

**版权所有 © 2025 [flyxm]**