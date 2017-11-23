---
title: "创建、 更改和删除默认值 |Microsoft 文档"
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: defaults [SMO]
ms.assetid: c30ac3b9-8150-4264-ba4c-c549f44261ab
caps.latest.revision: "46"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e79fad6e2c3e241c665a6869695e56aaed4d9158
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="creating-altering-and-removing-defaults"></a>创建、更改和删除默认值
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]在[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]管理对象 (SMO) 的默认约束都由<xref:Microsoft.SqlServer.Management.Smo.Default>对象。  
  
 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Default> 属性用于设置要插入的值。 此值可以是常量，也可以是返回常量值的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句，例如 GETDATE()。 不能通过使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 方法修改 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 属性。 相反，必须删除并重新创建 <xref:Microsoft.SqlServer.Management.Smo.Default> 对象。  
  
## <a name="example"></a>示例  
 若要使用所提供的任何代码示例，您必须选择创建应用程序所需的编程环境、编程模板和编程语言。 有关详细信息，请参阅[创建 Visual C &#35;Visual Studio.NET 中的 SMO 项目](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。  
  
## <a name="creating-altering-and-removing-a-default-in-visual-basic"></a>在 Visual Basic 中创建、更改和删除默认值  
 此代码示例演示如何创建一个简单文本形式的默认值和另一个 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句形式的默认值。 必须使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> 方法将默认值附加到列，然后使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> 方法将其分离。  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Define a Default object variable by supplying the parent database and the default name 
'in the constructor.
Dim def As [Default]
def = New [Default](db, "Test_Default2")
'Set the TextHeader and TextBody properties that define the default.
def.TextHeader = "CREATE DEFAULT [Test_Default2] AS"
def.TextBody = "GetDate()"
'Create the default on the instance of SQL Server.
def.Create()
'Declare a Column object variable and reference a column in the AdventureWorks2012 database.
Dim col As Column
col = db.Tables("SpecialOffer", "Sales").Columns("StartDate")
'Bind the default to the column.
def.BindToColumn("SpecialOffer", "StartDate", "Sales")
'Unbind the default from the column and remove it from the database.
def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales")
def.Drop()
```
  
## <a name="creating-altering-and-removing-a-default-in-visual-c"></a>在 Visual C# 中创建、更改和删除默认值  
 此代码示例演示如何创建一个简单文本形式的默认值和另一个 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句形式的默认值。 必须使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> 方法将默认值附加到列，然后使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> 方法将其分离。  
  
```csharp  
{  
  
          Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database  db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Default object variable by supplying the parent database and the default name   
            //in the constructor.   
            Default def = new Default(db, "Test_Default2");  
  
            //Set the TextHeader and TextBody properties that define the default.   
            def.TextHeader = "CREATE DEFAULT [Test_Default2] AS";  
            def.TextBody = "GetDate()";  
  
            //Create the default on the instance of SQL Server.   
            def.Create();  
  
            //Bind the default to a column in a table in AdventureWorks2012  
            def.BindToColumn("SpecialOffer", "StartDate", "Sales");  
  
            //Unbind the default from the column and remove it from the database.   
            def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales");  
            def.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-default-in-powershell"></a>在 PowerShell 中创建、更改和删除默认值  
 此代码示例演示如何创建一个简单文本形式的默认值和另一个 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句形式的默认值。 必须使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> 方法将默认值附加到列，然后使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> 方法将其分离。  
  
```powershell   
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
#Define a Default object variable by supplying the parent database and the default name in the constructor.  
$def = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Default `  
-argumentlist $db, "Test_Default2"  
  
#Set the TextHeader and TextBody properties that define the default.   
$def.TextHeader = "CREATE DEFAULT [Test_Default2] AS"  
$def.TextBody = "GetDate()"  
  
#Create the default on the instance of SQL Server.   
$def.Create()  
  
#Bind the default to the column.   
$def.BindToColumn("SpecialOffer", "StartDate", "Sales")  
  
#Unbind the default from the column and remove it from the database.   
$def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales")  
$def.Drop()  
```  
  
## <a name="see-also"></a>另请参阅  
 <xref:Microsoft.SqlServer.Management.Smo.Default>  
  
  