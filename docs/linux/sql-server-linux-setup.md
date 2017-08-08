---
title: "在 Linux 上安装 SQL Server 自 2017 年 1 |Microsoft 文档"
description: "安装、 更新和卸载 Linux 上的 SQL Server。 本主题介绍联机、 脱机和无人参与的方案。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 08/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 565156c3-7256-4e63-aaf0-884522ef2a52
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: c5bd1be5cbe08e9454b1640d9dd58584aa54955f
ms.contentlocale: zh-cn
ms.lasthandoff: 08/02/2017

---
# <a name="installation-guidance-for-sql-server-on-linux"></a>在 Linux 上的 SQL Server 安装指南

本主题说明如何安装、 更新和卸载 Linux 上的 SQL Server 2017。 Red Hat Enterprise Linux (RHEL)、 SUSE Linux 企业服务器 (SLES) 和 Ubuntu 支持 SQL Server 自 2017 年 1 RC2。 此外，还可以作为可在 Linux 或 Docker 为 Windows/mac。 上的 Docker 引擎运行的 Docker 映像

> [!TIP]
> 若要快速开始，跳转到快速入门教程： 之一[RHEL](quickstart-install-connect-red-hat.md)， [SLES](quickstart-install-connect-suse.md)， [Ubuntu](quickstart-install-connect-ubuntu.md)，或[Docker](quickstart-install-connect-docker.md)。

## <a id="supportedplatforms"></a>支持的平台

以下 Linux 平台上支持 SQL Server 2017:

| 平台 | 支持的版本 | 获取
|-----|-----|-----
| **Red Hat Enterprise Linux** | 7.3 | [获取 RHEL 7.3](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation)
| **SUSE Linux Enterprise Server** | v12 SP2 | [获取 SLES v12 SP2](https://www.suse.com/products/server)
| **Ubuntu** | 16.04 | [获取 Ubuntu 16.04](http://www.ubuntu.com/download/server)
| **Docker 引擎** | 1.8+ | [获取 Docker](http://www.docker.com/products/overview)

## <a id="system"></a>系统要求

SQL Server 2017 具有以下适用于 Linux 的系统要求：

|||
|-----|-----|
| **内存** | 3.25 GB |
| **文件系统** | **XFS**或**EXT4** (其他文件系统，如**BTRFS**，不支持) |
| **磁盘空间** | 6 GB |
| **处理器速度** | 2 GHz |
| **处理器核心** | 2 核 |
| **处理器类型** | 仅 x64 兼容 |

> [!NOTE]
> 目前，已测试出 SQL Server 引擎最多可占用 1 TB 内存。

## <a id="platforms"></a> 安装 SQL Server

从命令行中，可以在 Linux 上安装 SQL Server。 有关说明，请参阅以下快速入门教程之一：

- [在 Red Hat Enterprise Linux 上安装](quickstart-install-connect-red-hat.md)
- [在 SUSE Linux Enterprise Server 上安装](quickstart-install-connect-suse.md)
- [在 Ubuntu 上安装](quickstart-install-connect-ubuntu.md)
- [在 Docker 上运行](quickstart-install-connect-ubuntu.md)

## <a id="upgrade"></a>升级 SQL Server

若要升级**mssql server**打包在 Linux 上，请使用以下命令基于你的平台之一：

| 平台 | 包更新命令 |
|-----|-----|
| RHEL | `sudo yum update mssql-server` |
| SLES | `sudo zypper update mssql-server` |
| Ubuntu | `sudo apt-get update`<br/>`sudo apt-get install mssql-server` |

这些命令下载最新的包并将位于的二进制文件`/opt/mssql/`。 用户生成的数据库和系统数据库不受此操作。

## <a id="uninstall"></a>卸载 SQL Server

若要删除**mssql server**打包在 Linux 上，请使用以下命令基于你的平台之一：

| 平台 | 包删除命令 |
|-----|-----|
| RHEL | `sudo yum remove mssql-server` |
| SLES | `sudo zypper remove mssql-server` |
| Ubuntu | `sudo apt-get remove mssql-server` |

删除包不会删除生成的数据库文件。 如果你想要删除的数据库文件，使用以下命令：

```bash
sudo rm -rf /var/opt/mssql/
```

## <a id="unattended"></a>无人参与的安装

可以按以下方式来执行无人参与的安装：

- 按照初始步骤中[快速入门教程](#platforms)来注册存储库和安装 SQL Server。
- 当你运行`mssql-conf setup`，将其设置[环境变量](sql-server-linux-configure-environment-variables.md)并用`-n`（无提示） 选项。

下面的示例将配置的 SQL Server 的开发人员版**MSSQL_PID**环境变量。 它还会接受 EULA (**ACCEPT_EULA**) 和设置的 SA 用户密码 (**MSSQL_SA_PASSWORD**)。 `-n`参数执行悄悄地的安装其中的配置值从环境变量中提取。

```bash
sudo MSSQL_PID=Developer ACCEPT_EULA=Y MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' /opt/mssql/bin/mssql-conf -n setup
```

你还可以创建执行其他操作的脚本。 例如，你可以安装其他 SQL Server 包。

有关的更详细的示例脚本，请参阅下面的示例：

- [Red Hat 无人参与的安装脚本](sample-unattended-install-redhat.md)
- [SUSE 无人参与的安装脚本](sample-unattended-install-suse.md)
- [Ubuntu 无人参与的安装脚本](sample-unattended-install-ubuntu.md)

## <a id="offline"></a>脱机安装

如果你的 Linux 计算机无访问权限到联机存储库中使用[快速入门](#platforms)，你可以直接下载的包文件。 这些包位于 Microsoft 存储库， [https://packages.microsoft.com](https://packages.microsoft.com)。

> [!TIP]
> 如果你成功安装快速入门中的步骤，你不需要下载，或者手动安装以下程序包。 本部分项仅用于脱机方案。

1. **下载你的平台的数据库引擎包**。 包详细信息部分中找到包下载链接[发行说明](sql-server-linux-release-notes.md)。

1. **将下载的包移到你的 Linux 计算机**。 如果一台计算机用于下载的程序包，将包移动到你的 Linux 计算机的一个方法是使用**scp**命令。

1. **安装数据库引擎包**。 使用以下命令基于你的平台之一。 在此示例中的包文件名称替换为你下载的确切名称。

   | 平台 | 包删除命令 |
   |-----|-----|
   | RHEL | `sudo yum localinstall mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `sudo zypper install mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `sudo dpkg -i mssql-server_versionnumber_amd64.deb` |

    > [!NOTE]
    > 您还可以使用安装 RPM 包 （RHEL 和 SLES）`rpm -ivh`命令，但上表中的命令自动安装依赖项如果可从批准存储库。

1. **解决缺少的依赖关系**： 你可能必须在此点缺失的依赖关系。 如果没有，可以跳过此步骤。 在 Ubuntu，如果您有权访问已批准的存储库包含这些依赖关系，最简单的解决方案是使用`apt-get -f install`命令。 此命令还完成 SQL Server 的安装。 若要手动检查依赖关系，请使用以下命令：

   | 平台 | 依赖项列表命令 |
   |-----|-----|
   | RHEL | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | SLES | `rpm -qpR mssql-server_versionnumber.x86_64.rpm` |
   | Ubuntu | `dpkg -I mssql-server_versionnumber_amd64.deb` |

   在解决了缺少依赖关系之后, 尝试再次安装 mssql server 包。

1. **完成 SQL Server 安装程序**。 使用**mssql conf**若要完成 SQL Server 安装程序：

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

## <a name="next-steps"></a>后续步骤

安装完成后，你还可以安装其他可选的 SQL Server 包。

- [SQL Server 命令行工具](sql-server-linux-setup-tools.md)
- [SQL Server 代理](sql-server-linux-setup-sql-agent.md)
- [SQL Server 全文搜索](sql-server-linux-setup-full-text-search.md)
- [SQL Server Integration Services (Ubuntu)](sql-server-linux-setup-ssis.md)

连接到 SQL Server 实例以开始创建和管理数据库。 若要开始，请参阅快速入门教程:

- [在 Red Hat Enterprise Linux 上安装](quickstart-install-connect-red-hat.md)
- [在 SUSE Linux Enterprise Server 上安装](quickstart-install-connect-suse.md)
- [在 Ubuntu 上安装](quickstart-install-connect-ubuntu.md)
- [在 Docker 上运行](quickstart-install-connect-ubuntu.md)
