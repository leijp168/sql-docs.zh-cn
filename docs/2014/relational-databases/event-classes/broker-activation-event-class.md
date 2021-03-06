---
title: Broker:Activation 事件类 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Activation event class
ms.assetid: 481d5b13-657e-4b51-8783-ccac3595bd45
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 661d6bbd8630865c5c2c3a285431d27b5d5bb83b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48122337"
---
# <a name="brokeractivation-event-class"></a>Broker:Activation 事件类
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 当队列监视器启动激活存储过程或发送 QUEUE_ACTIVATION 通知时，或者当队列监视器所启动的激活存储过程退出时，生成 **Broker:Activation** 事件。  
  
## <a name="brokeractivation-event-class-data-columns"></a>Broker:Activation 事件类的数据列  
  
|数据列|类型|Description|列号|可筛选|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ClientProcessID**|`int`|由主机分配给正在运行客户端应用程序的进程的 ID。 如果客户端提供了客户端进程 ID，则填充此数据列。|9|用户帐户控制|  
|**DatabaseID**|`int`|由 USE *database* 语句指定的数据库的 ID；如果未对给定实例发出 USE *database*语句，则为默认数据库的 ID。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 数据列而且服务器可用，则 **ServerName** 将显示数据库名。 可使用 DB_ID 函数来确定数据库的值。|3|用户帐户控制|  
|**EventClass**|`int`|捕获的事件类的类型。 对于 **Broker:Activation** ，始终为 **163**。|27|否|  
|**EventSequence**|`int`|此事件的序列号。|51|否|  
|**EventSubClass**|`nvarchar`|此事件报告的特定操作。 可以是以下值之一：<br /><br /> **启动**: <br />                [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已启动激活存储过程。<br /><br /> **结束**： 激活存储过程已正常退出。<br /><br /> **中止**： 激活存储过程因错误而退出。|21|否|  
|**HostName**|`nvarchar`|正在运行客户端程序的计算机的名称。 如果客户端提供了主机名，则填充此数据列。 若要确定主机名，请使用 HOST_NAME 函数。|8|用户帐户控制|  
|**IntegerData**|`int`|此队列的活动任务数。|25|否|  
|**IsSystem**|`int`|指示事件是发生在系统进程中还是发生在用户进程中。 1 = 系统，0 = 用户。|60|否|  
|**LoginSid**|`image`|已登录用户的安全标识号 (SID)。 服务器中的每个登录名都具有唯一的 SID。|41|用户帐户控制|  
|**NTDomainName**|`nvarchar`|用户所属的 Windows 域。|7|用户帐户控制|  
|**NTUserName**|`nvarchar`|拥有生成此事件的连接的用户的名称。|6|用户帐户控制|  
|**Exchange Spill**|`int`|与此事件相关联的队列。|22|否|  
|**ServerName**|`nvarchar`|所跟踪的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。|26|否|  
|**SPID**|`int`|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 为客户端所关联的进程分配的服务器进程 ID。|12|用户帐户控制|  
|**StartTime**|`datetime`|事件（如果有）的开始时间。|14|用户帐户控制|  
|**TransactionID**|`bigint`|系统为事务分配的 ID。|4|否|  
  
  
