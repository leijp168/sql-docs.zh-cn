---
title: "删除数据库对象 |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- deleting database objects
ms.assetid: dbb94fdf-c85b-477b-8e84-f830d259bade
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7bcd4f3254cfd6b648411ae6fb9c364fa7017913
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-3-1---deleting-database-objects"></a>Lesson 3-1-删除数据库对象
若要删除在本教程中创建的所有对象，您只需删除数据库即可。 但是，在本主题中，您将完成下列步骤执行与教程中每项操作相反的操作。  
  
### <a name="removing-permissions-and-objects"></a>删除权限和对象  
  
1.  在删除对象之前，请确保使用正确的数据库：  
  
    ```  
    USE TestData;  
    GO  
    ```  
  
2.  使用 `REVOKE` 语句删除 `Mary` 对存储过程的执行权限：  
  
    ```  
    REVOKE EXECUTE ON pr_Names FROM Mary;  
    GO  
  
    ```  
  
3.  使用 `DROP` 语句删除 `Mary` 对 `TestData` 数据库的访问权限：  
  
    ```  
    DROP USER Mary;  
    GO  
  
    ```  
  
4.  使用 `DROP` 语句删除 `Mary` 对此 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]实例的访问权限。  
  
    ```  
    DROP LOGIN [<computer_name>\Mary];  
    GO  
  
    ```  
  
5.  使用 `DROP` 语句删除存储过程 `pr_Names`：  
  
    ```  
    DROP PROC pr_Names;  
    GO  
  
    ```  
  
6.  使用 `DROP` 语句删除视图 `vw_Names`：  
  
    ```  
    DROP View vw_Names;  
    GO  
  
    ```  
  
7.  使用 `DELETE` 语句删除 `Products` 表中的所有行：  
  
    ```  
    DELETE FROM Products;  
    GO  
  
    ```  
  
8.  使用 `DROP` 语句删除 `Products` 表：  
  
    ```  
    DROP Table Products;  
    GO  
  
    ```  
  
9. 正使用 `TestData` 数据库时，无法删除该数据库；因此，请首先将上下文切换到其他数据库，再使用 `DROP` 语句删除 `TestData` 数据库：  
  
    ```  
    USE MASTER;  
    GO  
    DROP DATABASE TestData;  
    GO  
  
    ```  
  
“编写 [!INCLUDE[tsql](../includes/tsql-md.md)] 语句”教程到此结束。 请记住，本教程只是简要概述，它并未介绍所用语句的所有选项。 设计和创建有效的数据库结构以及配置对数据的安全访问，需要比本教程中显示的数据库更复杂的数据库。  
  
## <a name="return-to-sql-server-tools-portal"></a>返回到 SQL Server 工具入门  
[教程：编写 Transact-SQL 语句](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
## <a name="see-also"></a>另请参阅  
[REVOKE (Transact-SQL)](../t-sql/statements/revoke-transact-sql.md)  
[DROP USER (Transact-SQL)](../t-sql/statements/drop-user-transact-sql.md)  
[DROP LOGIN (Transact-SQL)](../t-sql/statements/drop-login-transact-sql.md)  
[DROP PROCEDURE (Transact-SQL)](../t-sql/statements/drop-procedure-transact-sql.md)  
[DROP VIEW (Transact-SQL)](../t-sql/statements/drop-view-transact-sql.md)  
[DELETE (Transact-SQL)](../t-sql/statements/delete-transact-sql.md)  
[DROP TABLE (Transact-SQL)](../t-sql/statements/drop-table-transact-sql.md)  
[DROP DATABASE (Transact SQL)](../t-sql/statements/drop-database-transact-sql.md)  
  
  
  
