# RHEL 9 虚拟实验室搭建指南

## 目录

*   [为什么虚拟实验室至关重要？](#为什么虚拟实验室至关重要？)
*   [系统要求](#系统要求)
*   [分步指南](#分步指南)
    *   [Step 1: 下载 RHEL 9 ISO（合法免费）](#step-1-下载-rhel-9-iso合法免费)
    *   [Step 2: 安装 VMware Workstation Pro](#step-2-安装-vmware-workstation-pro)
    *   [Step 3: 为 RHEL 9 创建新的虚拟机](#step-3-为-rhel-9-创建新的虚拟机)
    *   [Step 4: 安装 RHEL 9](#step-4-安装-rhel-9)
    *   [Step 5: 安装后配置](#step-5-安装后配置)
    *   [Step 6: 虚拟机快照管理](#step-6-虚拟机快照管理)

本指南旨在为您提供一个全面、分步的方法，帮助您在本地计算机上使用 VMware Workstation Pro 和 Red Hat Enterprise Linux 9 (RHEL 9) 创建一个功能完善的虚拟环境。

## 为什么虚拟实验室至关重要？

创建虚拟实验室环境具有以下几个显著优势：

*   **安全练习：** 您可以在一个隔离的环境中自由地练习操作，而无需担心对实际操作系统造成任何损害。
*   **测试与实验：** 随意尝试各种配置、命令和系统设置。无需害怕对您的生产环境造成永久性损害。
*   **重复学习：** 重复是掌握技能的关键。您可以根据需要多次重复任务，以提高熟练程度和记忆。
*   **模拟真实世界设置：** 虚拟机 (VM) 允许您复制真实世界的企业环境，从而能够模拟复杂的网络配置、多服务器环境等，为实际工作做好准备。

## 系统要求

| Requirement    | Recommended                 |
| :------------- | :-------------------------- |
| RAM            | 8 GB (多虚拟机设置建议 16 GB) |
| Disk Space     | 40+ GB Free                 |
| CPU            | 至少双核                    |
| OS             | Windows/Linux/macOS         |

## 分步指南

### Step 1: 下载 RHEL 9 ISO（合法免费）

合法免费下载 RHEL 9 的步骤如下：

1.  访问 [Red Hat Developer Portal](https://developers.redhat.com/)。
2.  创建一个 [免费的 Red Hat Developer 账户](https://developers.redhat.com/register) 并登录。
3.  导航到下载部分，然后点击“Download RHEL 9 DVD ISO”。
4.  将 ISO 文件保存到本地计算机上的已知位置。

![Red Hat Developer Portal 登录界面](<../Screenshots/virtual-lab/00-virtual-lab.png>)
![下载 RHEL 9 ISO 按钮](<../Screenshots/virtual-lab/01-virtual-lab.png>)

### Step 2: 安装 VMware Workstation Pro

请根据您的操作系统，从 VMware 官方网站下载并安装 VMware Workstation Pro。按照安装向导的指示完成安装。

### Step 3: 为 RHEL 9 创建新的虚拟机

1.  **创建新的虚拟机：**
    *   打开 VMware Workstation Pro，选择“创建新的虚拟机”。
    ![创建新虚拟机向导](<../Screenshots/virtual-lab/02-virtual-lab.png>)

2.  **自定义高级设置：**
    *   选择“自定义(高级)”选项，点击“下一步”。此选项允许您对虚拟机硬件进行更细致的配置。
    ![自定义高级设置选项](<../Screenshots/virtual-lab/03-virtual-lab.png>)

3.  **兼容性选择：**
    *   保持默认选项（通常是最新版本兼容性），点击“下一步”。这确保了虚拟机与当前VMware版本的最佳兼容性。
    ![默认兼容性设置](<../Screenshots/virtual-lab/04-virtual-lab.png>)

4.  **稍后安装操作系统：**
    *   选择“稍后安装操作系统”，点击“下一步”。这样可以先配置虚拟机硬件，再手动引导安装。
    ![稍后安装操作系统选项](<../Screenshots/virtual-lab/05-virtual-lab.png>)

5.  **选择客户机操作系统：**
    *   客户机操作系统选择“Linux”，版本选择“Red Hat Enterprise Linux 9 64位”，点击“下一步”。VMware会根据此选择优化虚拟机设置。
    ![选择 Linux 和 RHEL 9 64位](<../Screenshots/virtual-lab/06-virtual-lab.png>)

6.  **命名虚拟机并选择位置：**
    *   虚拟机名称：`server9`。
    *   位置：`D:\VMs\RHEL9\VMs\server9`（您可以根据您的磁盘空间和组织习惯自定义路径）。点击“下一步”。
    ![命名虚拟机和选择存储位置](<../Screenshots/virtual-lab/07-virtual-lab.png>)

7.  **配置处理器：**
    *   按需选择 CPU 配置（例如，处理器数量和每个处理器的核心数量）。对于大多数实验，2个处理器和1个核心或1个处理器和2个核心已足够。点击“下一步”。
    ![配置处理器数量和核心](<../Screenshots/virtual-lab/08-virtual-lab.png>)

8.  **配置内存：**
    *   按需选择内存配置（例如，建议至少 2GB 或更多，根据您的物理内存和虚拟机数量调整）。点击“下一步”。
    ![配置虚拟机内存大小](<../Screenshots/virtual-lab/09-virtual-lab.png>)

9.  **网络类型：**
    *   选择“使用网络地址转换(NAT)”，点击“下一步”。NAT模式允许虚拟机通过宿主机访问外部网络，且虚拟机在宿主机网络中是隐藏的。
    ![选择 NAT 网络类型](<../Screenshots/virtual-lab/10-virtual-lab.png>)

10. **I/O 控制器类型：**
    *   选择默认选项（通常是 LSI Logic SAS），点击“下一步”。这通常是最佳兼容性和性能的选择。
    ![默认 I/O 控制器类型](<../Screenshots/virtual-lab/11-virtual-lab.png>)

11. **磁盘类型：**
    *   选择默认选项（通常是 NVMe 或 SCSI），点击“下一步”。根据您的需求和宿主机硬件选择。
    ![默认磁盘类型](<../Screenshots/virtual-lab/12-virtual-lab.png>)

12. **选择磁盘：**
    *   选择“创建新虚拟磁盘”，点击“下一步”。这将为虚拟机创建一个新的虚拟硬盘文件。
    ![创建新虚拟磁盘选项](<../Screenshots/virtual-lab/13-virtual-lab.png>)

13. **指定磁盘容量：**
    *   按需指定磁盘容量（例如，建议至少 40GB 以满足 RHEL 9 安装和后续实验需求），选择“将虚拟磁盘存储为单个文件”（便于管理和移动）。点击“下一步”。
    ![指定虚拟磁盘容量和存储方式](<../Screenshots/virtual-lab/14-virtual-lab.png>)

14. **指定磁盘文件：**
    *   选择默认选项（通常是虚拟机名称的 `.vmdk` 文件），点击“下一步”。
    ![默认虚拟磁盘文件路径](<../Screenshots/virtual-lab/15-virtual-lab.png>)

15. **自定义硬件：**
    *   点击“自定义硬件”按钮。
    ![自定义硬件设置](<../Screenshots/virtual-lab/16-virtual-lab.png>)

16. **移除不必要硬件：**
    *   选择“USB控制器”和“声卡”，点击“移除”按钮。这些设备在服务器虚拟机中通常不需要，移除可以减少资源占用和潜在的安全风险。点击“关闭”。
    ![移除 USB 控制器和声卡](<../Screenshots/virtual-lab/17-virtual-lab.png>)

17. **配置 CD/DVD (SATA)：**
    *   选择“新CD/DVD(SATA)”，勾选“使用ISO映像文件”，浏览并选择您下载的 RHEL 9 ISO 文件（`rhel-9.6-x86_64-dvd.iso`）。这将使虚拟机从ISO文件引导安装。点击“关闭”。
    ![配置 CD/DVD 驱动器为 ISO 映像](<../Screenshots/virtual-lab/18-virtual-lab.png>)

18. **完成虚拟机创建：**
    *   点击“完成”按钮。
    ![完成虚拟机创建向导](<../Screenshots/virtual-lab/19-virtual-lab.png>)

### Step 4: 安装 RHEL 9

1.  **启动虚拟机：**
    *   通过单击“开启此虚拟机”图标来启动 VM。数秒后，您将看到 RHEL 9 系统安装界面。
    ![启动虚拟机](<../Screenshots/virtual-lab/20-virtual-lab.png>)

2.  **选择安装选项：**
    *   在界面中，`Test this media & install Red Hat Enterprise Linux 9.6` 和 `Troubleshooting` 分别用于校验光盘完整性后再安装以及启动救援模式。此时，通过键盘的方向键选择 `Install Red Hat Enterprise Linux 9.6` 选项直接安装 Linux 系统。
    ![选择安装 RHEL 9.6 选项](<../Screenshots/virtual-lab/21-virtual-lab.png>)

3.  **加载安装镜像：**
    *   接下来按回车键后，系统将开始加载安装镜像，所需时间大约在 20～30 秒，请耐心等待。
    ![安装程序加载界面](<../Screenshots/virtual-lab/22-virtual-lab.png>)

4.  **选择安装语言：**
    *   选择系统的安装语言，推荐选择“English”（英文），单击“Continue”按钮。使用英文界面有助于后续学习和查找资料。
    ![选择安装语言为 English](<../Screenshots/virtual-lab/23-virtual-lab.png>)

5.  **安装概要界面 (INSTALLATION SUMMARY)：**
    *   这是 Linux 系统安装所需信息的集合之处，该界面包含如下内容：
        *   **LOCALIZATION (本地化):** Keyboard (键盘配置)、Language Support (语言支持)、Time & Date (时间和日期)
        *   **SOFTWARE (软件):** Connect to Red Hat (连接到红帽)、Installation Source (安装源)、Software Selection (软件选择)
        *   **SYSTEM (系统):** Installation Destination (安装目的地)、KDUMP (内核崩溃转储机制)、Network & Host Name (网络和主机名)、Security Profile (安全策略)
        *   **USER SETTINGS (用户设置):** Root Password (管理员帐户)、User Creation (用户帐户)
    ![安装概要界面](<../Screenshots/virtual-lab/24-virtual-lab.png>)

6.  **设置时间和日期：**
    *   单击“Time & Date”按钮，设置系统的时区和时间。在地图上单击中国境内即可显示出上海的当前时间，单击“Done”按钮。
    ![设置时区和时间](<../Screenshots/virtual-lab/25-virtual-lab.png>)

7.  **键盘和语言支持：**
    *   Keyboard 和 Language Support 分别指的是键盘类型和语言支持，这两项默认都是英文的，通常无需修改。单击“Done”按钮。
    ![键盘布局选择](<../Screenshots/virtual-lab/26-virtual-lab.png>)
    ![语言支持选择](<../Screenshots/virtual-lab/27-virtual-lab.png>)

8.  **安装源：**
    *   单击“Installation Source”（指的是系统从哪里获取安装文件）。这里默认是我们的光盘镜像文件，通常无需修改。单击“Done”按钮。
    ![安装源配置](<../Screenshots/virtual-lab/28-virtual-lab.png>)

9.  **软件选择：**
    *   单击“Software Selection”按钮，系统提供 6 种软件基本环境。检查当前模式是默认的 `Server with GUI`（带图形界面的服务器）即可，右侧额外的软件包不要选择，可以在后续学习过程中根据需要安装。单击“Done”按钮。
    ![软件选择界面](<../Screenshots/virtual-lab/29-virtual-lab.png>)

10. **安装目的地：**
    *   单击“Installation Destination”（指的是系统安装到哪个硬盘）。此时仅需确认，通常无需进行任何修改。单击“Done”按钮。
    ![安装目的地选择](<../Screenshots/virtual-lab/30-virtual-lab.png>)

11. **KDUMP 服务配置：**
    *   单击 KDUMP 服务的配置界面。KDUMP 服务用于收集系统内核崩溃数据，但考虑到在实验环境中通常不需要调试内核，建议取消选中 `Enable kdump` 复选框，这可以节省约 160MB 物理内存。随后单击左上角的“Done”按钮。
    ![KDUMP 配置界面](<../Screenshots/virtual-lab/31-virtual-lab.png>)

12. **网络和主机名：**
    *   单击 `NETWORK & HOST NAME` 配置界面。默认网络状态为 ON（开启）。 Host Name（主机名称）修改为 `flyxm.com` 并单击右侧的“Apply”按钮进行确认，这样可以保证后续的命令提示符前缀一致，避免学习上的歧义。也可以手动配置固定 IP，点击 Configure（默认不修改）。单击“Done”按钮。
    ![网络和主机名配置](<../Screenshots/virtual-lab/32-virtual-lab.png>)
    ![网络配置详情](<../Screenshots/virtual-lab/33-virtual-lab.png>) 

13. **安全策略：**
    *   单击 `SECURITY POLICY`。通常在实验环境中暂时不需要配置。单击“Done”按钮。
    ![安全策略配置](<../Screenshots/virtual-lab/34-virtual-lab.png>)

14. **Root 密码设置：**
    *   单击 `Root Password` 按钮，设置管理员（root 用户）的密码。在实验环境中密码强度要求不高，但在生产环境中务必设置足够复杂的密码。
    *   不勾选：`Lock root account` 选项来禁用对系统的 root 访问（通常在实验中保持不勾选）。
    *   勾选：`Allow root SSH login with password` 选项，以 root 用户身份启用对此系统的 SSH 访问（使用密码）。默认情况下，基于密码的 SSH root 访问权限是禁用的，勾选此项可启用。
    *   单击“Done”按钮。
    ![Root 密码设置](<../Screenshots/virtual-lab/35-virtual-lab.png>)

15. **用户创建：**
    *   单击 `User Creation` 按钮，为系统创建一个本地的普通用户。该账户的名字叫 `flyxm`，密码统一设置为 `redhat`。
    ![用户创建界面](<../Screenshots/virtual-lab/36-virtual-lab.png>)

16. **开始安装：**
    *   单击“Begin Installation”按钮，开始 RHEL 9 的安装过程。
    ![开始安装按钮](<../Screenshots/virtual-lab/37-virtual-lab.png>)

17. **安装完成并重启：**
    *   安装过程大约持续十几分钟。一切完成后单击右下角的“Reboot”按钮重启系统，使所有配置参数立即生效。
    ![安装进度和完成界面](<../Screenshots/virtual-lab/38-virtual-lab.png>)
    ![重启系统按钮](<../Screenshots/virtual-lab/39-virtual-lab.png>)

18. **登录用户：**
    *   系统重启后，使用您创建的用户（`flyxm`）或 `root` 用户登录，进入 RHEL 9 的图形界面。
    ![登录界面](<../Screenshots/virtual-lab/40-virtual-lab.png>)
    ![RHEL 9 桌面界面](<../Screenshots/virtual-lab/41-virtual-lab.png>)

### Step 5: 安装后配置

1.  **RHEL 9 系统注册**

    在 RHEL 9 中，“注册订阅”其实就是让系统跟 Red Hat 客户门户（RHSM）打通，只要注册成功，就能用 `dnf`/`yum` 拉取官方仓库、打补丁、装软件。下面给出 2025 年最新、最简单 的两种做法（CLI 一步到位 & GUI 点三下），按场景挑一个即可。

    ---

    #### 一、命令行 30 秒搞定（有网就行）

    1.  **准备**
        *   已有一个 Red Hat 账号（免费 Developer 订阅也行）。
        *   系统能上网（需连 `subscription.rhsm.redhat.com:443`）。

    2.  **一条命令注册 + 自动附加订阅**

        ```bash
        sudo subscription-manager register --username YOUR_REDHAT_USER --password 'YOUR_REDHAT_PW' --auto-attach
        ```

        **附加说明**
        *   `--auto-attach` 会自动把匹配的订阅挂到本机；
        *   若公司网络走代理，先执行

            ```bash
            export https_proxy=http://proxy.example.com:3128
            ```

            再注册即可。

    3.  **验证**

        ```bash
        subscription-manager list --consumed      # 能看到已附加的订阅
		#显示输出
		No consumed subscription pools were found.
		#SCA 下不再要求“附加”任何订阅池，系统直接凭注册身份解锁全部仓库，所以“已消费池”列表自然为空。
		
        sudo dnf repolist                         # 出现 rhel-9-* 系列仓库即成功
		#显示输出
		Updating Subscription Management repositories.
		repo id                                  repo name
		rhel-9-for-x86_64-appstream-rpms         Red Hat Enterprise Linux 9 for x86_64 - AppStream (RPMs)
		rhel-9-for-x86_64-baseos-rpms            Red Hat Enterprise Linux 9 for x86_64 - BaseOS (RPMs)
		# dnf repolist  能看到  rhel-9-for-x86_64-baseos-rpms  /  appstream-rpms 证明仓库已生效，可以正常安装、更新软件
        ```
		SCA 开启后，“无附加订阅”是预期行为，只要 repolist 有仓库，系统就处于合法可用状态。

    ![注册订阅](<../Screenshots/virtual-lab/43-virtual-lab.png>)	

    ---

    #### 二、图形界面 3 步走（GNOME 或 Web 控制台）

    1.  **安装阶段（Anaconda）**

        安装器 → “Connect to Red Hat” → 选 Account 或 Activation Key → 填账号/密码 → 完成安装即注册好。

    2.  **已装完系统**
        *   **GNOME 桌面**

            Activities 搜索 “Red Hat Subscription Manager” → Register → 输账号密码 → Attach 订阅。
        *   **RHEL 9 Web 控制台**

            `https://<本机>:9090` → 登录 →左侧 “Subscriptions” → Register → 选 Account 或 Activation Key → 完成。

    ---

    #### 三、常用后续命令

    *   **手动指定池 ID 附加:** `subscription-manager attach --pool=POOL_ID`
    *   **查看可用池:** `subscription-manager list --available`
    *   **换服务级别:** `subscription-manager service-level --set=self-support`
    *   **注销系统:** `subscription-manager unregister`
    *   **重新注册:** 先 `unregister` 再 `register --auto-attach`

    ---

    #### 四、排坑速查

    *   **401 Unauthorized:** 账号/密码错，或账号未激活邮件验证。
    *   **Attach 失败:** 免费 Developer 订阅只能挂 16 台物理机，超限会失败；登录 [https://access.redhat.com/management](https://access.redhat.com/management) 删除旧系统再试。
    *   **无仓库/空 repolist:** 注册成功但 SCA 未开，手动 `subscription-manager attach --auto` 即可。
    *   **离线环境:** 在能上网的机器生成 Activation Key，把 Key+组织 ID 拷到目标机执行：

        ```bash
        subscription-manager register --activationkey=KEY --org=ORG_ID
        ```

    ---

    **关于 `subscription-manager status` 显示 `Disabled` 的说明：**

    `subscription-manager status` 回显 `Overall Status: Disabled` 是完全正常的，这不是报错，而是告诉你：

    Red Hat 已在你的账号里启用了 Simple Content Access（SCA）模式，传统“订阅计数/强制附加”被关掉了。

    **结果：**

    *   `Overall Status: Disabled` → 传统“订阅是否附加”检查被禁用，系统不会因缺少订阅而变成 Invalid。
    *   `Content Access Mode: Simple Content Access` → 只要系统成功注册到账号，就能直接使用所有仓库，无需手动 attach 任何订阅。
    *   `System Purpose Status: Disabled` → 因为你没给系统设置 Service Level/Usage/Role，SCA 下可忽略。

    **验证仓库是否已可用（最关键）**

    ```bash
    dnf repolist | grep -E "rhel-9|codeready"
    ```

    只要能看到类似

    ```
rhel-9-for-x86_64-baseos-rpms  
rhel-9-for-x86_64-appstream-rpms
    ```

    就证明 内容已解锁，可以放心 `dnf install/update`。

    **一句话总结：**

    SCA 开启后，`subscription-manager status` 显示 `Disabled` 是预期行为；只要注册成功且 `repolist` 有仓库，系统就能正常打补丁装软件，无需再 attach 订阅。

2.  **安装 VMware Tools / `open-vm-tools`：**
    *   为了提高虚拟机性能和集成度（如剪贴板共享、文件拖放、屏幕分辨率自适应），建议安装 VMware Tools。在 RHEL 9 中，推荐安装 `open-vm-tools`。
    ```bash
    sudo dnf install -y open-vm-tools
    sudo systemctl enable --now vmtoolsd
    ```
3.  **更新系统：**
    *   安装完成后，立即更新系统到最新状态，以获取最新的安全补丁和软件包。
    ```bash
    sudo dnf update -y
    ```
4.  **重启系统：**
    *   更新完成后，建议重启系统以确保所有更改生效。
    ```bash
    sudo reboot
    ```

### Step 6: 虚拟机快照管理

虚拟机快照是 VMware Workstation Pro 中一个非常实用的功能，它允许您在特定时间点保存虚拟机的状态。这对于实验、测试和快速回退到已知良好状态非常有用。

1.  **拍摄快照：**
    *   在 VMware Workstation Pro 中，选择您的 RHEL 9 虚拟机。
    *   点击“虚拟机”菜单 -> “快照” -> “拍摄快照”。
    ![拍摄快照菜单](<../Screenshots/virtual-lab/44-virtual-lab.png>)

2.  **填写快照名称及描述信息：**
    *   在弹出的对话框中，为快照输入一个有意义的名称（例如：“RHEL9_Clean_Install”）和描述信息（例如：“RHEL 9 干净安装完成，已注册并更新”）。
    *   点击“拍摄快照”按钮。
    ![填写快照名称和描述](<../Screenshots/virtual-lab/45-virtual-lab.png>)

3.  **查看快照管理器：**
    *   快照拍摄完成后，您可以点击“虚拟机”菜单 -> “快照” -> “快照管理器”来查看、管理和恢复您的快照。
    *   在快照管理器中，您可以选择任何一个快照，然后点击“转到”按钮将虚拟机恢复到该快照时的状态。
    ![查看快照管理器](<../Screenshots/virtual-lab/46-virtual-lab.png>)