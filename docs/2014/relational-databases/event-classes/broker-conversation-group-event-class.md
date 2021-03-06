---
title: Broker:Conversation Group 事件类 | Microsoft Docs
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
- Broker:Conversation Group event class
ms.assetid: 6595bef6-9d40-42eb-a934-735622dd23fb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d42b2183cb2927ad9c7c477810f1a7fddfbcbb46
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079377"
---
# <a name="brokerconversation-group-event-class"></a>Broker:Conversation Group 事件类
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将生成 **Broker:Conversation Group** 事件。  
  
## <a name="brokerconversation-group-event-class-data-columns"></a>Broker:Conversation Group 事件类的数据列  
  
|数据列|类型|Description|列号|可筛选|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|`nvarchar`|客户端应用程序的名称，该客户端应用程序创建了指向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的连接。 此列由应用程序传递的值填充，而不是由所显示的程序名填充。|10|用户帐户控制|  
|**ClientProcessID**|`int`|由主机分配给正在运行客户端应用程序的进程的 ID。 如果客户端提供了客户端进程 ID，则填充此数据列。|9|用户帐户控制|  
|**DatabaseID**|`int`|由 USE *database* 语句指定的数据库的 ID；如果未对给定实例发出 USE *database* 语句，则为默认数据库的 ID。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 数据列而且服务器可用，则 **ServerName** 将显示数据库名。 可使用 DB_ID 函数来确定数据库的值。|3|用户帐户控制|  
|**EventClass**|`int`|捕获的事件类的类型。 对于 **Broker:Conversation Group** 始终为 **136**。|27|否|  
|**EventSequence**|`int`|此事件的序列号。|51|否|  
|**EventSubClass**|`nvarchar`|事件子类的类型，提供有关每个事件类的进一步信息。 此列可能包含下列值：<br /><br /> **创建**。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 创建新的会话组。<br /><br /> **删除**。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 删除会话组。|21|用户帐户控制|  
|**GUID**|`uniqueidentifier`|此事件描述的会话组的标识符。|54|否|  
|**HostName**|`nvarchar`|正在运行客户端程序的计算机的名称。 如果客户端提供了主机名，则填充此数据列。 若要确定主机名，请使用 HOST_NAME 函数。|8|用户帐户控制|  
|**IsSystem**|`int`|指示事件是发生在系统进程中还是发生在用户进程中。 1 = 系统，0 = 用户。|60|否|  
|**LoginSid**|`image`|已登录用户的安全标识号 (SID)。 服务器中的每个登录名都具有唯一的 SID。|41|用户帐户控制|  
|**NTDomainName**|`nvarchar`|用户所属的 Windows 域。|7|用户帐户控制|  
|**NTUserName**|`nvarchar`|拥有生成此事件的连接的用户的名称。|6|用户帐户控制|  
|**ServerName**|`nvarchar`|所跟踪的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。|26|否|  
|**SPID**|`int`|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 为客户端所关联的进程分配的服务器进程 ID。|12|用户帐户控制|  
|**StartTime**|`datetime`|事件（如果有）的开始时间。|14|用户帐户控制|  
|**TransactionID**|`bigint`|系统为事务分配的 ID。|4|否|  
  
  
