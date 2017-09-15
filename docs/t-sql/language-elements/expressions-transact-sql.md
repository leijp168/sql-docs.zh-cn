---
title: "表达式 (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Boolean expressions
- expressions [SQL Server], about expressions
- combining expressions
- Transact-SQL expressions
- expressions [SQL Server], combining
- simple expressions [SQL Server]
- complex expressions [SQL Server]
ms.assetid: ee53c5c8-e36c-40f9-8cd1-d933791b98fa
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 826d1ab9f4a0a68d692551ae58a529ab8b7ebfae
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="expressions-transact-sql"></a>表达式（Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  符号和运算符的一种组合，[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]将处理该组合以获得单个数据值。 简单表达式可以是一个常量、变量、列或标量函数。 可以用运算符将两个或更多的简单表达式联接起来组成复杂表达式。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
{ constant | scalar_function | [ table_name. ] column | variable   
    | ( expression ) | ( scalar_subquery )   
    | { unary_operator } expression   
    | expression { binary_operator } expression   
    | ranking_windowed_function | aggregate_windowed_function  
}  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

-- Expression in a SELECT statement  
<expression> ::=   
{  
    constant   
    | scalar_function   
    | column  
    | variable  
    | ( expression  )  
    | { unary_operator } expression   
    | expression { binary_operator } expression   
}  
[ COLLATE Windows_collation_name ]  
  
-- Scalar Expression in a DECLARE, SET, IF…ELSE, or WHILE statement  
<scalar_expression> ::=  
{  
    constant   
    | scalar_function   
    | variable  
    | ( expression  )  
    | (scalar_subquery )  
    | { unary_operator } expression   
    | expression { binary_operator } expression   
}  
[ COLLATE { Windows_collation_name ]  
  
```  
  
## <a name="arguments"></a>参数  
  
|术语|定义|  
|----------|----------------|  
|*常量*|表示单个特定数据值的符号。 有关详细信息，请参阅[常量 &#40;Transact SQL &#41;](../../t-sql/data-types/constants-transact-sql.md).|  
|*scalar_function*|是一套[!INCLUDE[tsql](../../includes/tsql-md.md)]提供特定的服务并返回单个值的语法。 *scalar_function*可以是内置标量函数，如 SUM、 GETDATE 或强制转换函数或标量用户定义函数。|  
|[ *table_name***。** ]|表的名称或别名。|  
|*列*|是一个列的名称。 表达式中只允许列的名称。|  
|*变量*|变量或参数的名称。 有关详细信息，请参阅 [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)。|  
|**(** *表达式***)** |本主题中定义的任意一个有效表达式。 括号是分组运算符，用于确保先运算括号内表达式中的运算符，然后再将结果与别的表达式组合。|  
|**(** *scalar_subquery* **)**|返回一个值的子查询。 例如：<br /><br /> `SELECT MAX(UnitPrice)`<br /><br /> `FROM Products`|  
|{ *unary_operator* }|一元运算符只能用于计算结果数据类型属于数字数据类型类别的表达式。 只有一个数字操作数的运算符：<br /><br /> ＋ 指示正数。<br /><br /> - 指示负数。<br /><br /> ~ 指示一的补数运算符。|  
|{ *binary_operator* }|用于定义如何组合两个表达式以得到一个结果的运算符。 *binary_operator*可以是算术运算符、 赋值运算符 （=）、 一个按位运算符、 比较运算符，一个逻辑运算符、 字符串串联运算符 （+） 或一个一元运算符。 有关运算符的详细信息，请参阅[运算符 &#40;Transact SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md).|  
|*ranking_windowed_function*|任意 [!INCLUDE[tsql](../../includes/tsql-md.md)] 排名函数。 有关详细信息，请参阅[排名函数 &#40;Transact SQL &#41;](../../t-sql/functions/ranking-functions-transact-sql.md).|  
|*aggregate_windowed_function*|任意包含 [!INCLUDE[tsql](../../includes/tsql-md.md)] OVER 子句的聚合函数。 有关详细信息，请参阅[OVER 子句 &#40;Transact SQL &#41;](../../t-sql/queries/select-over-clause-transact-sql.md).|  
  
## <a name="expression-results"></a>表达式结果  
 对于由单个常量、变量、标量函数或列名组成的简单表达式，其数据类型、排序规则、精度、小数位数和值就是它所引用的元素的数据类型、排序规则、精度、小数位数和值。  
  
 用比较运算符或逻辑运算符组合两个表达式时，生成的数据类型为 Boolean，并且值为下列类型之一：TRUE、FALSE 或 UNKNOWN。 Boolean 数据类型的详细信息，请参阅[比较运算符 &#40;Transact SQL &#41;](../../t-sql/language-elements/comparison-operators-transact-sql.md).  
  
 用算术运算符、位运算符或字符串运算符组合两个表达式时，生成的数据类型取决于运算符。  
  
 由多个符号和运算符组成的复杂表达式的计算结果为单值结果。 生成的表达式的数据类型、排序规则、精度和值由进行组合的两个表达式决定，并按每次两个表达式的顺序递延，直到得出最后结果。 表达式中元素组合的顺序由表达式中运算符的优先级决定。  
  
## <a name="remarks"></a>注释  
 两个表达式可以由一个运算符组合起来，只要它们具有该运算符支持的数据类型，并且满足至少下列一个条件：  
  
-   两个表达式有相同的数据类型。  
  
-   优先级低的数据类型可以隐式转换为优先级高的数据类型。  
  
 如果表达式不满足这些条件，则可以使用 CAST 或 CONVERT 函数将优先级低的数据类型显式转化为优先级高的数据类型，或者转换为一种可以隐式转化成优先级高的数据类型的中间数据类型。  
  
 如果没有支持的隐式或显式转换，则两个表达式将无法组合。  
  
 任何计算结果为字符串的表达式的排序规则都应遵循排序规则优先顺序规则。 有关详细信息，请参阅[排序规则优先顺序 &#40;Transact SQL &#41;](../../t-sql/statements/collation-precedence-transact-sql.md).  
  
 如 C 编程语言中或[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]，始终在表达式计算结果为单个结果。 [!INCLUDE[tsql](../../includes/tsql-md.md)] 选择列表中的表达式按以下规则进行变体：分别对结果集中的每一行计算表达式的值。 同一个表达式对结果集内的每一行可能会有不同的值，但该表达式在每一行的值是唯一的。 例如，在 `SELECT` 语句中，对 `ProductID` 的引用以及选择列表中的术语 `1+2` 都是表达式：  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, 1+2  
FROM Production.Product;  
GO  
```  
  
 结果集中的每个行的表达式 `1+2` 的计算结果都为 `3`。 虽然表达式 `ProductID` 在结果集的每一行中产生一个唯一值，但每一行只有一个 `ProductID` 值。  
  
## <a name="see-also"></a>另请参阅  
 [时区 &AMP; #40;Transact SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)   
 [用例 &#40;Transact SQL &#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [强制转换和转换 &#40;Transact SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [将合并 &#40;Transact SQL &#41;](../../t-sql/language-elements/coalesce-transact-sql.md)   
 [数据类型转换 &#40; 数据库引擎 &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)   
 [数据类型优先级 &#40;Transact SQL &#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)   
 [数据类型 (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [内置函数 (Transact-SQL)](~/t-sql/functions/functions.md)   
 [如 &#40;Transact SQL &#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [NULLIF &#40;Transact SQL &#41;](../../t-sql/language-elements/nullif-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [其中 &#40;Transact SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  
