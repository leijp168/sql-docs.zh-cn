---
title: "STDistance (geography 数据类型) |Microsoft 文档"
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
- STDistance_TSQL
- STDistance (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDistance method
ms.assetid: 063d8722-e019-4d3d-8fcf-dbf5325823e7
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f79891d789938a6f4615c0e4be9cc3ba5d361f1
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="stdistance-geography-data-type"></a>STDistance（geography 数据类型）
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  返回的点之间的距离最短**geography**实例，并在另一个点**geography**实例。  
  
> [!NOTE]  
>  `STDistance()`返回最短路线**LineString**两个 geography 类型之间。 这与测地距离十分相似。 偏差`STDistance()`从确切测地学距离的常见地球模型上是不能超过。 25%。 这将避免混淆测地类型中长度和距离之间的细微差别。  
  
## <a name="syntax"></a>语法  
  
```  
  
.STDistance ( other_geography )  
```  
  
## <a name="arguments"></a>参数  
 *other_geography*  
 是另一种**geography**从中测量对其调用 stdistance （） 的实例之间的距离的实例。 如果*other_geography*设置为空，stdistance （） 返回 null。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]返回类型： **float**  
  
 CLR 返回类型： **SqlDouble**  
  
## <a name="remarks"></a>注释  
 如果 stdistance （） 方法始终返回 null 的空间引用 Id 为 (Srid) **geography**实例不匹配。  
  
> [!NOTE]  
>  上的方法**geography**计算区域或距离的数据类型将返回基于在方法中使用的实例的 SRID 不同结果。   有关 Srid 的详细信息，请参阅[空间引用标识符 &#40;Srid &#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
## <a name="examples"></a>示例  
 下面的示例查找两个之间的距离**geography**实例。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SET @h = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.STDistance(@h);  
```  
  
## <a name="see-also"></a>另请参阅  
 [地域实例上的 OGC 方法](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
