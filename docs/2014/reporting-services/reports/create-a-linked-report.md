---
title: 创建链接报表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 277ee4ff416ad9710eecf501651b5a5143b0fa68
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48210201"
---
# <a name="create-a-linked-report"></a>创建链接报表
  链接报表是提供对现有报表的访问点的报表服务器项。 从概念上说，它与用于运行程序或打开文件的程序快捷方式类似。  
  
 链接报表是从现有报表派生的，保留原始报表的报表定义。 链接报表始终会继承原始报表的报表布局和数据源属性。 所有其他属性和设置都可以与原始报表不同，其中包括安全性、参数、位置、订阅和计划。  
  
 如果希望创建现有报表的其他版本，则可以创建链接报表。 例如，可以使用一个区域销售额报表来为所有销售区域创建区域特定的报表。  
  
 虽然链接报表通常基于参数化报表，但并不一定需要使用参数化报表。 每当您想使用不同的设置部署现有报表时，都可以创建链接报表。  
  
### <a name="to-create-a-linked-report"></a>创建链接报表  
  
1.  在报表管理器中，导航到包含想要链接到的报表的文件夹，然后打开选项菜单并单击 **“创建链接报表”**。  
  
2.  键入新链接报表的名称。 根据需要，可以键入说明。  
  
3.  若要为报表选择不同的文件夹，请单击 **“更改位置”**。 单击要使用的文件夹，或者在 **“位置”** 框中键入文件夹名称。 [!INCLUDE[clickOK](../../../includes/clickok-md.md)] 如果不选择其他文件夹，在当前文件夹 （它所基于的报表存储位置） 中创建链接的报表。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)] 打开链接的报表。  
  
     链接报表的图标与报表服务器管理的其他项不同。 下面的图标表示链接报表：  
  
     ![链接报表图标](../media/hlp-16linked.gif "链接报表图标")  
  
## <a name="see-also"></a>请参阅  
 [打开和关闭报表&#40;报表管理器&#41;](../reports/open-and-close-a-report-report-manager.md)   
 [“新建链接报表”页（报表管理器）](../new-linked-report-page-report-manager.md)   
 [“选择项位置”页（报表管理器）](../choose-item-location-page-report-manager.md)   
 [报表的“常规”属性页（报表管理器）](../general-properties-page-reports-report-manager.md)   
 [Reporting Services 概念 (SSRS)](../reporting-services-concepts-ssrs.md)   
 [报表管理器（SSRS 本机模式）](../report-manager-ssrs-native-mode.md)  
  
  
