---
title: sp_help_log_shipping_monitor_primary (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_monitor_primary
- sp_help_log_shipping_monitor_primary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_monitor_primary
ms.assetid: d9dfcb8f-1da6-49ca-a2c8-411574915434
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 04e1fb52d74366893ff43deb9fabad9cac7135cc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47843887"
---
# <a name="sphelplogshippingmonitorprimary-transact-sql"></a>sp_help_log_shipping_monitor_primary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  从监视表返回有关主数据库的信息。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_help_log_shipping_monitor_primary  
[ @primary_server = ] 'primary_server',   
[ @primary_database = ] 'primary_database'  
```  
  
## <a name="arguments"></a>参数  
 [ **@primary_server =** ] '*primary_server*'  
 主实例的名称[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]日志传送配置中。 *primary_server*是**sysname**且不能为 NULL。  
  
 [  **@primary_database =** ] '*primary_database*  
 主服务器上的数据库的名称。 *primary_database*是**sysname**，无默认值。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="result-sets"></a>结果集  
  
|列名|Description|  
|-----------------|-----------------|  
|**primary_id**|日志传送配置的主数据库 ID。|  
|**primary_server**|日志传送配置中 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]主实例的名称。|  
|**primary_database**|日志传送配置中主数据库的名称。|  
|**backup_threshold**|备份操作之间的占用时间阈值（分钟），一旦超过此值，就会生成警报。|  
|**threshold_alert**|超过备份阈值时引发的警报。|  
|**threshold_alert_enabled**|确定是否启用备份阈值警报。 1 = 启用；0 = 禁用。|  
|**last_backup_file**|最近一次事务日志备份的绝对路径。|  
|**last_backup_date**|上一次在主数据库上执行事务日志备份操作的时间和日期。|  
|**last_backup_date_utc**|上一次在主数据库上执行事务日志备份操作的时间和日期，使用协调世界时表示。|  
|**history_retention_period**|日志传送历史记录在删除前保留在给定主数据库中的时间（分钟）。|  
  
## <a name="remarks"></a>备注  
 **sp_help_log_shipping_monitor_primary**必须从运行**主**在监视服务器上的数据库。  
  
## <a name="permissions"></a>Permissions  
 只有的成员**sysadmin**固定的服务器角色可以运行此过程。  
  
## <a name="see-also"></a>请参阅  
 [关于日志传送 (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
