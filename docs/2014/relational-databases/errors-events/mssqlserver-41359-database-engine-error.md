---
title: MSSQLSERVER_41359 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 41359 (Database Engine error)
ms.assetid: 02b717c7-9170-4676-b0f6-4dec9eb5b5d4
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9cfc69b5c7da77f53c6d49d82a70739fb5a7d09c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "37412416"
---
# <a name="mssqlserver41359"></a>MSSQLSERVER_41359
    
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|事件 ID|41359|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED|  
|消息正文|当数据库选项 READ_COMMITTED_SNAPSHOT 设置为 ON 时，使用 COMMITTED 隔离级别访问内存优化表的查询不能访问基于磁盘的表。 使用表提示（例如 WITH (SNAPSHOT)）为内存优化表提供一种支持的隔离级别。|  
  
## <a name="explanation"></a>解释  
 READ_COMMITTED_SNAPSHOT=ON 的数据库不支持同时访问内存优化表和基于磁盘的表的事务。  
  
## <a name="user-action"></a>用户操作  
 将 READ_COMMITTED_SNAPSHOT 设置为 OFF，或使用表级提示（例如 WITH (SNAPSHOT)）为内存优化表提供一个支持的隔离级别。 有关详细信息，请参阅[内存中 OLTP&#40;内存中优化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。  
  
## <a name="see-also"></a>请参阅  
 [内存中 OLTP（内存中优化）](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  