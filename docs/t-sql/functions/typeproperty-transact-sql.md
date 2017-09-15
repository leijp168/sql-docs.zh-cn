---
title: "TYPEPROPERTY (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TYPEPROPERTY
- TYPEPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- status information [SQL Server], data types
- data types [SQL Server], status information
- TYPEPROPERTY function
ms.assetid: bc311c80-bac5-46ab-a5c8-68b1c6bbf24a
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9b0cfaf45b7b4f68979691272c90962da42709b2
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="typeproperty-transact-sql"></a>TYPEPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  返回有关数据类型的信息。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
TYPEPROPERTY (type , property)  
```  
  
## <a name="arguments"></a>参数  
 *type*  
 是数据类型的名称。  
  
 *属性*  
 要为数据类型返回的信息类型。 *属性*可以是以下值之一。  
  
|属性|Description|返回的值|  
|--------------|-----------------|--------------------|  
|**AllowsNull**|数据类型允许空值。|1 = True<br /><br /> 0 = False<br /><br /> NULL = 找不到数据类型。|  
|**OwnerId**|类型的所有者。<br /><br /> 注意： 架构所有者不一定是类型所有者。|Nonnull = 类型所有者的数据库用户 ID。<br /><br /> NULL = 不支持的类型，或类型 ID 无效。|  
|**精度**|数据类型的精度。|数字位数或字符个数。<br /><br /> 为-1 = **xml**或大型值数据类型<br /><br /> NULL = 找不到数据类型。|  
|**小数位数**|数据类型的小数位数。|数据类型的小数位的个数。<br /><br /> NULL = 的数据类型不是**数值**或找不到。|  
|**UsesAnsiTrim**|创建数据类型时 ANSI 填充设置为 ON。|1 = True<br /><br /> 0 = False<br /><br /> NULL = 数据类型找不到，或不是二进制数据类型或字符串数据类型。|  
  
## <a name="return-types"></a>返回类型  
 **int**  
  
## <a name="exceptions"></a>异常  
 出现错误时或调用方没有查看对象的权限时，将返回 NULL。  
  
 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，用户只能查看其拥有的安全对象的元数据，或者已对其授予权限的安全对象的元数据。 也就是说，如果用户对该对象没有任何权限，则某些会产生元数据的内置函数（如 TYPEPROPERTY）可能返回 NULL。 有关详细信息，请参阅 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="examples"></a>示例  
  
### <a name="a-identifying-the-owner-of-a-data-type"></a>A. 标识数据类型的所有者  
 以下示例返回数据类型的所有者。  
  
```  
SELECT TYPEPROPERTY(SCHEMA_NAME(schema_id) + '.' + name, 'OwnerId') AS owner_id, name, system_type_id, user_type_id, schema_id  
FROM sys.types;  
```  
  
### <a name="b-returning-the-precision-of-the-tinyint-data-type"></a>B. 返回 tinyint 数据类型的精度  
 以下示例返回 `tinyint` 数据类型的精度或位数。  
  
```  
SELECT TYPEPROPERTY( 'tinyint', 'PRECISION');  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>示例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-returning-the-precision-of-the-tinyint-data-type"></a>C： 返回的 tinyint 数据类型的精度  
 以下示例返回 `tinyint` 数据类型的精度或位数。  
  
```  
SELECT TYPEPROPERTY( 'tinyint', 'PRECISION');  
```  
  
## <a name="see-also"></a>另请参阅  
 [TYPE_ID &#40;Transact SQL &#41;](../../t-sql/functions/type-id-transact-sql.md)   
 [类型 _ 名称 &#40;Transact SQL &#41;](../../t-sql/functions/type-name-transact-sql.md)   
 [COLUMNPROPERTY &#40;Transact SQL &#41;](../../t-sql/functions/columnproperty-transact-sql.md)   
 [元数据函数 &#40;Transact SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECTPROPERTY (Transact-SQL)](../../t-sql/functions/objectproperty-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.types &#40;Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)  
  
  

