---
title: 发布服务器属性 - 发布服务器，订阅服务器 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.configdistwizard.pubproperties.subscribers.f1
helpviewer_keywords:
- Publisher Properties dialog box
ms.assetid: 552d2bd6-13f9-4876-b8f1-89adb242ef70
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e65ebcd0849392bf0cbed230d58293b9cea9815b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47613717"
---
# <a name="publisher-properties---publisher-subscribers"></a>发布服务器属性 - 发布服务器，订阅服务器
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  “发布服务器属性”对话框的“订阅服务器”页用于运行早于 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本的发布服务器。 使用此页，可以启用订阅服务器以接收此发布服务器上发布的数据。 启用订阅服务器接收此发布服务器的数据，并不会创建对此发布服务器上的发布的订阅。 若要创建订阅，必须使用新建订阅向导。  
  
## <a name="options"></a>选项  
 **“发布服务器属性”**  
 **“订阅服务器”** 属性网格显示了已启用的从此发布服务器上发布接收数据的订阅服务器。 单击订阅服务器旁边的属性按钮 (**...**) 可以查看和设置其他属性。  
  
 **“添加”**  
 单击 **“添加”** 以添加订阅服务器，然后可单击 **“添加 SQL Server 订阅服务器”** 或 **“添加非 SQL Server 订阅服务器”**。  
  
## <a name="see-also"></a>另请参阅  
 [查看和修改分发服务器和发布服务器属性](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [属性参考（复制）](../../relational-databases/replication/properties-reference-replication.md)   
 [订阅发布](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
