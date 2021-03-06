---
title: 将服务器配置为运行 Off By Default 策略 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 41c3022d-ab13-443e-ac64-ba1d64584f79
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 82cf55e1fa3fa9bda5a625ef89335a9f81ed5505
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48147877"
---
# <a name="configure-a-server-to-run-the-off-by-default-policy"></a>将服务器配置为运行 Off By Default 策略
  现在有一个名为 Off By Default 的策略。 在本任务中，您将检查服务器是否符合此策略的要求。  
  
### <a name="to-run-the-off-by-default-policy"></a>运行 Off By Default 策略  
  
1.  在对象资源管理器中，右键单击 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，指向“策略”，然后单击“评估”。  
  
2.  在“评估策略”对话框中，可以从另一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例或文件中选择策略。 对于此步骤，仍将“源”设置为 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。  
  
3.  在“策略”部分中，选择 **Off By Default** 策略。  
  
4.  要查看服务器是否符合该策略，请单击“评估”。  
  
5.  如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 符合该策略，则会在“结果”区域中显示带复选标记的绿色圆圈。 如果[!INCLUDE[ssDE](../../includes/ssde-md.md)]不符合该策略，则会显示带 X 的红色圆圈。  
  
6.  在“目标详细信息”区域中，如果发生了错误，你会在“消息”列中看到其他信息。 在“消息”列中，单击“查看”以查看报表，其中包含所检查的每个方面属性的检查结果。  
  
7.  页面底部将显示策略说明，“更多帮助”部分显示为策略配置的超链接。 单击消息超链接可打开在创建策略时指定的网页。  
  
8.  关闭浏览器，然后关闭“结果详细视图”对话框。  
  
9. 如果服务器不符合该策略并且你希望禁用数据库邮件，请在“评估结果”页中单击“应用”。  
  
10. 关闭“结果详细视图”和“评估策略”对话框。  
  
## <a name="next-lesson"></a>下一课  
 [第 2 课：创建并应用命名标准策略](lesson-2-create-and-apply-a-naming-standards-policy.md)  
  
  
