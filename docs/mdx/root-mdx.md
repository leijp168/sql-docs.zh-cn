---
title: "根 (MDX) |Microsoft 文档"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Root
dev_langs:
- kbMDX
helpviewer_keywords:
- Root function
ms.assetid: f6c42e87-5a52-4e43-9dd1-ca757f2db79c
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9e6eb1b8be0c5ef654ccf07bfce45070cf6bcc14
ms.contentlocale: zh-cn
ms.lasthandoff: 08/02/2017

---
# <a name="root-mdx"></a>Root (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  返回组成的元组**所有**多维数据集、 维度或元组中当前范围内每个属性层次结构中的成员。 有关作用域的详细信息，请参阅[SCOPE 语句 &#40;MDX &#41;](../mdx/mdx-scripting-scope.md).  
  
> [!NOTE]  
>  如果属性层次结构没有**所有**成员、 元组包含该层次结构的默认成员。  
  
## <a name="syntax"></a>语法  
  
```  
  
Cube syntax  
Root ()  
Dimension syntax  
Root( Dimension_Name )  
Tuple syntax  
Root( Tuple_Expression )  
```  
  
## <a name="arguments"></a>参数  
 *Dimension_Name*  
 指定维度名称的有效字符串表达式。  
  
 *Tuple_Expression*  
 返回元组的有效多维表达式 (MDX)。  
  
## <a name="remarks"></a>備註  
 如果指定既不是维度名称，也不是元组表达式，则**根**函数返回包含的元组**所有**成员 (或默认成员如果**所有**成员不存在) 从多维数据集中每个属性层次结构。 成员在元组中的顺序基于多维数据集中定义属性层次结构的顺序。  
  
 如果指定维度名称，则**根**函数返回包含的元组**所有**成员 (或默认成员如果**所有**成员不存在) 基于当前的成员的上下文的指定维中的每个属性层次结构中。 成员在元组中的顺序基于维度中定义属性层次结构的顺序。  
  
> [!NOTE]  
>  如果指定层次结构名称，则**元组**函数会选取从指定的层次结构名称的维度的名称。  
  
 如果指定一个元组表达式，则**根**函数返回包含指定元组的交集的元组和**所有**未显式指定元组中包含所有其他维度特性的成员。  
  
## <a name="examples"></a>示例  
 下面的示例返回元组包含**所有**成员 (或默认值如果**所有**成员不存在) 从 Adventure Works 多维数据集中的每个层次结构。  
  
```  
SELECT Root()ON 0  
FROM [Adventure Works]  
```  
  
 下面的示例返回元组包含**所有**成员 (或默认值如果**所有**成员不存在) 从在 Adventure Works 多维数据集和与这些默认成员相交的度量值维度的指定成员的值与 Date 维度中的每个层次结构。  
  
```  
SELECT Root([Date]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
 下面的示例返回包含指定元组成员的元组 (2001 年 7 月 1 日，连同**所有**成员 (或默认值如果**所有**成员不存在) 从每个非指定层次结构中的日期维度 Adventure Works 多维数据集和值的交集的度量值维度与这些成员的指定成员。  
  
```  
SELECT Root([Date].[July 1, 2001]) ON 0  
FROM [Adventure Works]  
WHERE [Measures].[Order Count]  
```  
  
## <a name="see-also"></a>另请参阅  
 [MDX 函数引用 &#40;MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
