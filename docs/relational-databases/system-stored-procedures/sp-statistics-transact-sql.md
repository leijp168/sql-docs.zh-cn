---
title: "sp_statistics (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_statistics_TSQL
- sp_statistics
dev_langs: TSQL
helpviewer_keywords: sp_statistics
ms.assetid: 0bb6495f-258a-47ec-9f74-fd16671d23b8
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: acb1e775a99bb3c296064a65aa9eed7be5d17745
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="spstatistics-transact-sql"></a>sp_statistics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  返回针对指定的表或索引视图的所有索引和统计信息的列表。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_statistics [ @table_name = ] 'table_name'    
     [ , [ @table_owner = ] 'owner' ]   
     [ , [ @table_qualifier = ] 'qualifier' ]   
     [ , [ @index_name = ] 'index_name' ]   
     [ , [ @is_unique = ] 'is_unique' ]  
     [ , [ @accuracy = ] 'accuracy' ]  
```  
  
## <a name="arguments"></a>参数  
 [  **@table_name=** ] *table_name*  
 指定用来返回目录信息的表。 *table_name*是**sysname**，无默认值。 不支持通配符模式匹配。  
  
 [  **@table_owner=** ] *所有者*  
 用于返回目录信息的表的表所有者的名称。 *table_owner*是**sysname**，默认值为 NULL。 不支持通配符模式匹配。 如果*所有者*未指定，则应用基础 DBMS 的默认表的可见性规则。  
  
 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，如果当前用户拥有一个具有指定名称的表，则返回该表的索引。 如果*所有者*未指定当前用户不拥有具有指定的表和*名称*，此过程查找具有指定的表*名称*归数据库所有者。 如果存在这样的表，则返回该表的索引。  
  
 [  **@table_qualifier=** ] *限定符*  
 表限定符的名称。 *限定符*是**sysname**，默认值为 NULL。 各种 DBMS 产品支持三部分命名表 (*限定符***。***所有者***。***名称*)。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，此参数表示数据库名称。 在某些产品中，该列表示表所在的数据库环境的服务器名。  
  
 [  **@index_name=** ] *index_name*  
 是的索引名称。 *index_name*是**sysname**，默认值为 %。 支持通配符模式匹配。  
  
 [  **@is_unique=** ] *is_unique*  
 是是否仅唯一索引 (如果**Y**) 要返回。 *is_unique*是**char （1)**，默认值为**N**。  
  
 [  **@accuracy=** ] *准确性*  
 统计信息的基数和页准确性的级别。 *准确性*是**char （1)**，默认值为**Q**。指定**E**若要确保统计信息更新以便基数和页正确无误。  
  
 值**E** (SQL_ENSURE) 要求的驱动程序，以无条件地检索统计信息。  
  
 值**Q** (SQL_QUICK) 要求要检索基数的驱动程序和页仅当从服务器可迅速获得。 在这种情况下，驱动程序不能保证是最新值。 按照 Open Group 标准编写的应用程序将总是从 ODBC 3.x 兼容驱动程序获得 SQL_QUICK 行为。  
  
## <a name="result-sets"></a>结果集  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_QUALIFIER**|**sysname**|表限定符名称。 该列可以为 NULL。|  
|**TABLE_OWNER**|**sysname**|表所有者名称。 该列始终返回值。|  
|**TABLE_NAME**|**sysname**|表名。 该列始终返回值。|  
|**NON_UNIQUE**|**int**|NOT NULL。<br /><br /> 0 = 唯一<br /><br /> 1 = 不唯一|  
|**INDEX_QUALIFIER**|**sysname**|索引所有者名称。 某些 DBMS 产品允许表所有者之外的用户创建索引。 在[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，此列始终是相同**TABLE_NAME**。|  
|**INDEX_NAME**|**sysname**|索引的名称。 该列始终返回值。|  
|**TYPE**|**int**|此列始终返回值：<br /><br /> 0 = 表的统计信息<br /><br /> 1 = 聚集<br /><br /> 2 = 哈希<br /><br /> 3 = 非聚集|  
|**SEQ_IN_INDEX**|**int**|列在索引中的位置。|  
|**COLUMN_NAME**|**sysname**|每一列的列名称**TABLE_NAME**返回。 该列始终返回值。|  
|**排序规则**|**char （1)**|在排序规则中使用的顺序。 可以是：<br /><br /> A = 升序<br /><br /> D = 降序<br /><br /> NULL = 不适用|  
|**基数**|**int**|表中的行或索引中的唯一值数。|  
|**页**|**int**|若要存储的索引或表的页面数。|  
|**FILTER_CONDITION**|**varchar （128)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不返回值。|  
  
## <a name="return-code-values"></a>返回代码值  
 无  
  
## <a name="remarks"></a>注释  
 以升序按所列显示在结果集中的索引**NON_UNIQUE**，**类型**， **INDEX_NAME**，和**SEQ_IN_INDEX**。  
  
 聚集索引类型引用一个索引，该索引中的表数据按索引的顺序存储。 这对应于[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]聚集索引。  
  
 哈希索引类型接受完全匹配或范围搜索，但模式匹配搜索不使用该索引。  
  
 **sp_statistics**等效于**SQLStatistics** ODBC 中。 返回对结果进行排序的**NON_UNIQUE**，**类型**， **INDEX_QUALIFIER**， **INDEX_NAME**，和**SEQ_IN_索引**。 有关详细信息，请参阅[ODBC API 参考](http://go.microsoft.com/fwlink/?LinkId=68323)。  
  
## <a name="permissions"></a>Permissions  
 需要对架构的 SELECT 权限。  
  
## <a name="example-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>示例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 下面的示例返回有关的信息`DimEmployee`表。  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_statistics DimEmployee;  
```  
  
## <a name="see-also"></a>另请参阅  
 [目录存储的过程 &#40;Transact SQL &#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
