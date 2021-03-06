---
title: 引用 ADO 库中的 Visual c + + 应用程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual C++ application[ADO]
- ADO, libraries
ms.assetid: d3ea12ec-bca8-48c3-af57-ce14576108c9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 772dbc55fdeb3b038399a3740be472497666e4da
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51290783"
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>在 Visual C++ 应用程序中引用 ADO 库
若要使用 ADO 的 Visual c + + 应用程序中的最新版本，使用以下`#import`指令：  
  
```cpp
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 若要使用 ADO MD 或 ADOX，必须导入*msadomd.dll*或*msadox.dll*，通过使用上面的语法。  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 若要使用任何早期版本的 ADO，替换*msado15.dll*上述其中一个以下类型库。  
  
-   *msado27.tlb*，ADO 2.7 类型库  
  
-   *msado26.tlb*，ADO 2.6 类型库  
  
-   *msado25.tlb*，ADO 2.5 类型库  
  
-   *msado21.tlb*，ADO 2.1 类型库  
  
-   *msado20.tlb*，ADO 2.0 类型库
