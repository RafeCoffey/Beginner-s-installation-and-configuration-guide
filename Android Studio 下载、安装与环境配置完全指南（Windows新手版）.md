# Android Studio 下载、安装与环境配置完全指南（Windows新手版）

本文提供Windows系统超详细步骤，从下载到环境验证全流程覆盖，结合新手常见问题优化，确保一次成功配置Android Studio、Android SDK和Command Line Tools，避开所有踩坑点。

# 一、准备工作：系统要求与下载前须知

最低系统配置（推荐配置在括号内），确保电脑满足以下条件，避免安装后无法正常运行：

|配置项|最低要求|推荐配置|
|---|---|---|
|操作系统|64位 Windows 10及以上|同最低要求（Windows 11更佳）|
|内存|8GB RAM|16GB RAM（运行模拟器更流畅）|
|存储空间|10GB 可用空间|20GB \+ 可用空间（预留SDK和模拟器空间）|
|屏幕分辨率|1280×800|1920×1080\+（编辑代码更清晰）|
|其他|支持 VT\-x/AMD\-V 虚拟化（用于模拟器）|开启硬件加速（步骤见常见问题）|

# 二、下载 Android Studio（官方渠道，安全无广告）

## 1\. 访问官方网站（优先选中国官网，速度更快）

中国官网（推荐）：https://developer\.android\.google\.cn/studio

全球官网：https://developer\.android\.com/studio（若中国官网访问不畅可选用）

## 2\. 下载安装包（步骤清晰，避免错点）

- 打开官网后，找到绿色的「Download Android Studio」按钮，点击进入下载页面；

- 勾选页面中的「I have read and agree with the above terms and conditions」（同意协议）；

- 点击下方的「Download Android Studio」，系统会自动匹配Windows系统的安装包，开始下载。

# 三、Windows 系统安装步骤（重点！避开C盘和中文路径）

## 1\. 运行安装程序

找到下载完成的安装包（通常在「下载」文件夹，文件名格式：android\-studio\-2025\.2\.1\.xx\-windows\.exe），双击运行。

## 2\. 选择安装类型

弹出安装向导后，推荐选择「Custom（自定义）」安装（新手也可操作），方便修改安装路径，避免占用C盘空间；选择后点击「Next」。

## 3\. 选择安装路径（关键！必看）

- 点击「Browse」，选择非系统盘（如D盘、E盘），建议新建一个「Android」文件夹，再在其中新建「Android Studio」子文件夹；

- 示例路径（推荐）：D:\\Android\\Android Studio（**重点：路径中绝对不能有中文、空格或特殊符号**，否则会导致后续无法启动或编译错误）；

- 路径设置完成后，点击「Next」。

## 4\. 完成安装

- 选择开始菜单文件夹：默认即可，无需修改，点击「Install」，等待安装完成（约5\-10分钟，取决于电脑配置）；

- 安装完成后，**取消勾选「Start Android Studio」**（先不启动，后续配置更稳妥），点击「Finish」。

# 四、首次启动与 SDK 配置（核心步骤，新手必看）

## 1\. 启动 Android Studio

从开始菜单找到「Android Studio」，点击启动（首次启动较慢，耐心等待）。

## 2\. 导入设置

首次安装会弹出「Import Settings」窗口，选择「Do not import settings」（不导入任何设置），点击「OK」。

## 3\. 安装向导 \- 选择安装类型

推荐选择「Standard（标准）安装」（适合新手，无需手动配置组件，系统自动默认最优设置）；

若需自定义安装路径（如SDK不想装在C盘），可选择「Custom」，后续步骤会提示修改SDK路径。

## 4\. 选择 SDK 安装路径（重要！再次避开中文路径）

- 点击「Browse」，选择非系统盘（如D:\\Android\\Sdk），与Android Studio安装路径分开，方便后续管理；

- 再次确认：路径中无中文、空格，点击「Next」。

## 5\. 选择 SDK 组件（必勾选这几项）

保持默认勾选以下组件，无需额外添加，避免冗余：

- Android SDK Platform（最新版本，如35，用于兼容最新Android系统）；

- Android SDK Build\-Tools（最新版本，用于编译项目）；

- Android Emulator（模拟器，用于调试APP，新手必备）；

- **Android SDK Command\-line Tools（必须勾选！）**（后续验证环境和命令行操作需要）。

勾选完成后，点击「Next」。

## 6\. 接受许可协议

勾选「I accept the terms of the license agreements」（同意所有许可协议），点击「Next」→「Finish」，开始下载SDK组件（约5\-30分钟，取决于网络速度，耐心等待）。

## 7\. 进入主界面

组件下载完成后，点击「Finish」，即可进入Android Studio主界面，首次启动会提示「Start a new Android Studio project」（创建新项目），先不创建，先完成环境变量配置。

# 五、配置 Command Line Tools 与环境变量（解决你之前遇到的报错，重点优化）

## 1\. 确认 Command Line Tools 已安装（避免后续验证报错）

- 打开Android Studio，点击左上角「三条横线」（菜单按钮），展开后选择「File」→「Settings」；

- 在弹出的窗口中，依次展开「Appearance \&amp; Behavior」→「System Settings」→「Android SDK」；

- 切换到「SDK Tools」标签页，确认「Android SDK Command\-line Tools \(latest\)」已勾选（若未勾选，勾选后点击「Apply」，等待安装完成）；

- 确认完成后，点击「OK」关闭窗口。

## 2\. 手动创建必要目录（关键！解决sdkmanager命令报错）

Command Line Tools需要特定目录结构才能正常工作，很多新手会忽略这一步，导致后续验证失败，步骤如下：

- 打开你之前设置的SDK安装路径（如D:\\Android\\Sdk）；

- 找到「cmdline\-tools」文件夹（若不存在，手动新建一个，命名为cmdline\-tools，小写，无空格）；

- 在「cmdline\-tools」文件夹内，手动新建一个「latest」文件夹（小写，必须命名为latest）；

- 将「cmdline\-tools」文件夹中所有的文件和文件夹（如bin、lib等），全部移动到「latest」文件夹中；

- 最终正确结构：Sdk/cmdline\-tools/latest/bin/sdkmanager（进入这个路径，能看到sdkmanager\.bat文件即可）。

## 3\. 设置环境变量（分两步，解决JAVA\_HOME和SDK路径报错）

### 第一步：新建系统变量 ANDROID\_HOME（指向SDK路径）

- 打开环境变量设置：两种方法任选一种，都能打开：
        

    - 方法1：Win\+R→输入「sysdm\.cpl」→回车→切换到「高级」标签→点击「环境变量」；

    - 方法2：打开电脑「设置」→「系统」→「关于」→「高级系统设置」→「环境变量」。

- 在弹出的「环境变量」窗口中，找到「系统变量」（下半部分，不是上面的「用户变量」），点击「新建」；

- 变量名：**ANDROID\_HOME**（全大写，下划线，不能错，否则后续命令无法识别）；

- 变量值：粘贴你设置的SDK路径（如D:\\Android\\Sdk）；

- 点击「确定」，保存这个系统变量。

### 第二步：新建系统变量 JAVA\_HOME（解决你之前遇到的「JAVA\_HOME is not set」报错）

Android Studio自带JDK，无需额外下载，直接使用内置JDK即可，步骤如下：

- 找到Android Studio的安装目录（如D:\\Android\\Android Studio）；

- 进入安装目录，找到「jbr」文件夹（这就是内置JDK的位置）；

- 复制「jbr」文件夹的完整路径（如D:\\Android\\Android Studio\\jbr）；

- 回到「系统变量」窗口，再次点击「新建」；

- 变量名：**JAVA\_HOME**（全大写，下划线，不能错）；

- 变量值：粘贴刚才复制的jbr路径（如D:\\Android\\Android Studio\\jbr）；

- 点击「确定」，保存这个系统变量。

### 第三步：编辑系统变量 Path（让系统识别相关命令）

- 在「系统变量」中，找到「Path」变量，选中后点击「编辑」；

- 在弹出的编辑窗口中，点击「新建」，依次添加以下3条路径（每行一个，复制粘贴即可，无需修改）：
        

    - %ANDROID\_HOME%\\platform\-tools

    - %ANDROID\_HOME%\\cmdline\-tools\\latest\\bin

    - %JAVA\_HOME%\\bin

- 添加完成后，点击「确定」，再点击「环境变量」窗口的「确定」、「高级系统设置」窗口的「确定」，**所有窗口都要点击确定，否则设置不生效**。

# 六、验证环境配置（确保所有设置都成功，必做！）

**重点：必须打开新的命令提示符（cmd），旧的窗口会不识别新设置的环境变量！**

## 1\. 打开新的命令提示符

按Win\+R→输入「cmd」→回车，打开一个黑色的命令行窗口（新窗口，不要用之前打开的）。

## 2\. 验证 JDK（确认JAVA\_HOME配置成功）

在命令行中输入以下命令，回车：

java \-version

成功输出示例（版本号可能不同，只要不报错即可）：

openjdk version \&\#34;21\.0\.10\&\#34; 2024\-01\-16 LTS

OpenJDK Runtime Environment \(build 21\.0\.10\+9\-LTS\)

OpenJDK 64\-Bit Server VM \(build 21\.0\.10\+9\-LTS, mixed mode, sharing\)

## 3\. 验证 adb（Android 调试桥，后续调试APP需要）

在命令行中输入以下命令，回车：

adb version

成功输出示例：

Android Debug Bridge version 1\.0\.41

Version 35\.0\.1\-10900879

Installed as D:\\Android\\Sdk\\platform\-tools\\adb\.exe

## 4\. 验证 sdkmanager（Command Line Tools，解决你之前的warning）

在命令行中输入以下命令，回车：

sdkmanager \-\-version

注意：若出现warning（如“无法识别配置文件格式”），无需担心！这是命令行工具版本与SDK版本的小兼容问题，**不影响正常开发**，只要能输出版本号（如9\.0），就说明配置成功。

## 5\. 验证 Android Studio 与 SDK 关联

- 打开Android Studio，点击「File」→「Project Structure」；

- 检查「SDK Location」是否正确指向你的SDK路径（如D:\\Android\\Sdk）；

- 若路径正确，说明关联成功；若不正确，点击「Browse」选择正确路径，点击「OK」保存。

# 七、常见问题与解决方案（新手必看，解决你遇到的所有问题）

## 1\. 验证 sdkmanager 时，报错「JAVA\_HOME is not set」

解决方案：重新检查JAVA\_HOME配置，确保：

- 变量名是「JAVA\_HOME」（全大写，无拼写错误）；

- 变量值是Android Studio安装目录下的「jbr」文件夹路径（如D:\\Android\\Android Studio\\jbr）；

- Path变量中已添加「%JAVA\_HOME%\\bin」；

- 必须打开新的cmd窗口重新验证。

## 2\. 验证 sdkmanager 时，出现warning（无法识别配置文件）

解决方案：无需处理！这不是配置错误，是命令行工具与SDK版本的小兼容问题，不影响Android Studio开发、编译和调试，直接忽略即可。

## 3\. 安装过程中，SDK组件下载缓慢或失败

解决方案：使用国内镜像源（清华大学镜像），步骤如下：

- 打开Android Studio→「File」→「Settings」→「Appearance \&amp; Behavior」→「System Settings」→「Android SDK」；

- 切换到「SDK Update Sites」标签页，点击「Add」；

- 输入镜像地址：https://mirrors\.tuna\.tsinghua\.edu\.cn/android/repository/，点击「OK」；

- 勾选添加的镜像地址，取消勾选其他地址，点击「Apply」，重新下载组件即可。

## 4\. 环境变量设置后，命令仍无法执行

解决方案：

- 检查路径是否正确（重点检查cmdline\-tools的「latest」文件夹是否创建，且文件已移动）；

- 确保打开的是新的cmd窗口（旧窗口不识别新环境变量）；

- 确认环境变量是设置在「系统变量」中，而非「用户变量」（用户变量仅当前用户可用，系统变量全用户可用）。

## 5\. 启动模拟器时，提示「未开启虚拟化」

解决方案：重启电脑，开机时按主板快捷键（如F2、Del，不同主板快捷键不同）进入BIOS，找到「VT\-x/AMD\-V」选项，设置为「Enabled」，保存并重启电脑即可。

# 八、总结与下一步

恭喜！你已成功完成以下配置，可正常开始Android开发：

- ✓ Android Studio 安装完成

- ✓ Android SDK 配置完成

- ✓ Command Line Tools 配置完成

- ✓ 环境变量设置完成

- ✓ 所有验证均通过

## 下一步建议（新手入门）

- 创建第一个项目：打开Android Studio→点击「Start a new Android Studio project」→选择「Empty Views Activity」→跟随向导完成（只需设置项目名称和保存路径，其他默认即可）；

- 熟悉界面：重点了解「Project」窗口（查看项目文件）、「Editor」（编写代码）、「Logcat」（查看调试信息）；

- 运行项目：创建项目后，点击顶部的「Run」按钮，选择模拟器（首次启动模拟器会较慢），等待项目运行成功，即可看到第一个APP界面。

> （注：文档部分内容可能由 AI 生成）
