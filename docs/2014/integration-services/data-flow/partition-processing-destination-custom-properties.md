---
title: 分区处理目标自定义属性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 3eac4413-0c90-4b06-8f7e-d0d72f4d869d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9139ff2af92d861f356514e9e78073c3e858ab81
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048587"
---
# <a name="partition-processing-destination-custom-properties"></a>分区处理目标自定义属性
  分区处理目标具有自定义属性和所有数据流组件通用的属性。  
  
 下表介绍分区处理目标的自定义属性。 所有属性均可读/写。  
  
|“属性”|数据类型|Description|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 项目或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]实例的连接字符串。|  
|KeyDuplicate|Integer（枚举）|当 UseDefaultConfiguration 为`False`，一个值，指示如何处理重复键错误。 可能的值为`IgnoreError`(0)， `ReportAndContinue` (1) 和`ReportAndStop`(2)。 此属性的默认值是`IgnoreError`(0)。|  
|KeyErrorAction|Integer（枚举）|当 UseDefaultConfiguration 为`False`，一个值，指示如何处理键错误。 可能的值为 `ConvertToUnknown` (0) 和 `DiscardRecord` (1)。 此属性的默认值是`ConvertToUnknown`(0)。|  
|KeyErrorLimit|Integer|当 UseDefaultConfiguration 为`False`，允许的键错误的上限。|  
|KeyErrorLimitAction|Integer（枚举）|当 UseDefaultConfiguration 时`False`，一个值，指示操作时要采取`KeyErrorLimit`达到。 可能的值为`StopLogging`(1) 和`StopProcessing`(0)。 此属性的默认值是`StopProcessing`(0)。|  
|KeyErrorLogFile|String|当 UseDefaultConfiguration 为`False`，错误日志文件的路径和文件名称。|  
|“KeyNotFound”|Integer（枚举）|当 UseDefaultConfiguration 为`False`，一个值，指示如何处理缺失键错误。 可能的值为`IgnoreError`(0)， `ReportAndContinue` (1) 和`ReportAndStop`(2)。 此属性的默认值是`ReportAndContinue`(1)。|  
|NullKeyConvertedToUnknown|Integer（枚举）|当 UseDefaultConfiguration 为`False`，一个值，指示如何处理 null 键转换为未知值。 可能的值为`IgnoreError`(0)， `ReportAndContinue` (1) 和`ReportAndStop`(2)。 此属性的默认值是`IgnoreError`(0)。|  
|NullKeyNotAllowed|Integer（枚举）|当 UseDefaultConfiguration 为`False`，一个值，指示如何处理不允许 null 值。 可能的值为`IgnoreError`(0)， `ReportAndContinue` (1) 和`ReportAndStop`(2)。 此属性的默认值是`ReportAndContinue`(1)。|  
|ProcessType|Integer（枚举）|转换使用的分区处理的类型。 可能的值为 `ProcessAdd` (1)（增量）、`ProcessFull` (0) 和 `ProcessUpdate` (2)。|  
|UseDefaultConfiguration|Boolean|一个指定转换是否使用默认错误配置的值。 如果此属性为`False`，转换将使用此表，包括 KeyDuplicate 和 KeyErrorAction 等等中列出的错误处理自定义属性的值。|  
  
 分区处理目标的输入和输入列没有自定义属性。  
  
 有关详细信息，请参阅 [Partition Processing Destination](partition-processing-destination.md)。  
  
## <a name="see-also"></a>请参阅  
 [Common Properties](../common-properties.md)  
  
  
