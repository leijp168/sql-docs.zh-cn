---
title: 指定外部项的路径（报表生成器和 SSRS）| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 4fe513da-f3c5-479c-9fec-8662b91a0d6d
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 7b41acb95312ac9675d711c0c02817e58dfe2106
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48221707"
---
# <a name="specifying-paths-to-external-items-report-builder-and-ssrs"></a>指定外部项的路径（报表生成器和 SSRS）
  在报表项属性中指定钻取报表、子报表和图像文件等引用项的路径，这些引用项在报表定义文件外部并存储在报表服务器上。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
> [!NOTE]  
>  在报表生成器中，项的路径必须指定报表服务器上的项。 不支持项在文件系统上的路径。 仅当连接到项所在的报表服务器时，才能预览使用这些项的报表。  
  
 在操作、子报表或图像的对话框中指定外部项的路径时，可以直接浏览到报表服务器并选择项。 指定钻取报表或子报表的推荐方式是直接浏览到该项并选择它。 使用这种方式，当您指定报表或子报表参数时，将在下拉列表中出现正确的参数名称。 更改项路径以指向不同项时，必须根据需要手动更新正确的参数名称和值。  
  
 在以本机模式配置的报表服务器上，指定钻取报表名称时不需要包括文件扩展名 .rdl。  
  
 而在以 SharePoint 集成模式配置的报表服务器上，则必须包含文件扩展名 .rdl。 路径可以是以下类型之一：  
  
-   **主报表中的项的相对路径。** 例如，../AllSubreports/Subreport1。 在本例中， **..** 表示主报表所在文件夹的上一级文件夹。  
  
    > [!NOTE]  
    >  在报表生成器内运行报表时，不支持相对路径。 若要查看使用外部项的相对路径的报表，请将报表保存到报表服务器，并从那里运行报表。  
  
-   **项的完整路径。**  
  
    -   **在报表服务器上：** 路径将从 **/** 主文件夹开始。 例如，/Reports/AllSubreports/Subreport1。  
  
    -   **在 SharePoint 站点上：** 必须在表达式中指定报表名称，并包含报表项的完整 URL 以及文件扩展名 .rdl。 例如 `="http://server/site/library/folder/Report1.rdl"` 。  
  
## <a name="see-also"></a>请参阅  
 [添加外部图像&#40;报表生成器和 SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md)   
 [添加子报表和参数（报表生成器和 SSRS）](add-a-subreport-and-parameters-report-builder-and-ssrs.md)   
 [在报表中添加钻取操作（报表生成器和 SSRS）](add-a-drillthrough-action-on-a-report-report-builder-and-ssrs.md)  
  
  
