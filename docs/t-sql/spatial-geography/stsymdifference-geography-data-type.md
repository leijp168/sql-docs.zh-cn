---
title: STSymDifference（geography 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STSymDifference (geography Data Type)
- STSymDifference_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STSymDifference (geography Data Type)
ms.assetid: 82bbfa2c-a61b-4f41-9bf8-6f720f363bae
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9767a72fea55abb732da9351c3a9c7fb242e5447
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47825845"
---
# <a name="stsymdifference-geography-data-type"></a>STSymDifference（geography 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  返回一个对象，它表示位于一个 **geography** 实例或另一个 **geography** 实例中的所有点，但不包含同时位于这两个实例中的点。  
  
## <a name="syntax"></a>语法  
  
```  
  
.STSymDifference ( other_geography )  
```  
  
## <a name="arguments"></a>参数  
 other_geography  
 调用 STSymDistance() 的实例以外的另一个 geography 实例。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：geography  
  
 CLR 返回类型：SqlGeography  
  
## <a name="remarks"></a>Remarks  
 如果 geography 实例的空间引用标识符 (SRID) 不匹配，则此方法始终返回 null。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持大于半球的空间实例。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，服务器上可能的结果集已扩展到 FullGlobe 实例。  
  
 只有在输入实例包含圆弧线段时，结果才会包含圆弧线段。  
  
## <a name="examples"></a>示例  
  
### <a name="a-computing-the-symmetric-difference-of-two-polygons"></a>A. 计算两个多边形的余集  
 以下示例使用 `STSymDifference()` 计算两个 `Polygon` 实例的余集。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('POLYGON((-122.351 47.656, -122.341 47.656, -122.341 47.661, -122.351 47.661, -122.351 47.656))', 4326);  
SELECT @g.STSymDifference(@h).ToString();  
```  
  
### <a name="b-computing-the-symmetric-difference-with-fullglobe"></a>B. 计算与 FullGlobe 的余集  
 以下示例计算 `Polygon` 与 `FullGlobe` 的余集。  
  
```
 DECLARE @g geography = 'POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STSymDifference('FULLGLOBE').ToString();
 ```  
  
## <a name="see-also"></a>另请参阅  
 [地理实例上的 OGC 方法](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
