---
title: "sys.pdw_replicated_table_cache_state (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 07/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
author: ronortloff
ms.author: rortloff;barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 700ebe6ee06ebbcccf9c1388cb3a4f8015a26669
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwreplicatedtablecachestate-transact-sql"></a>sys.pdw_replicated_table_cache_state (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

  返回与通过复制的表关联的缓存的状态**object_id**。  
  
|列名|数据类型|Description|范围|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|表对象 ID。 请参阅[sys.objects &#40;Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).<br /><br /> **object_id**是此视图的密钥。||  
|state|**nvarchar （40)**|此表复制的表缓存状态。|未就绪，就绪|  
  
## <a name="example"></a>示例
此示例将联接 sys.pdw_replicated_table_cache_state 与 sys.tables 检索表名称和复制的表缓存的状态。

```sql
SELECT t.[name], p.[object_id], p.[state]
  FROM sys.pdw_replicated_table_cache_state p 
  JOIN sys.tables t ON t.object_id = p.object_id
```



## <a name="next-steps"></a>后续步骤  
 对于 SQL 数据仓库和并行数据仓库的所有目录视图的列表，请参阅[SQL 数据仓库和并行数据仓库目录视图](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)。   
  