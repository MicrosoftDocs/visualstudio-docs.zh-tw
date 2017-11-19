---
title: "您已選取的資料庫物件不支援的資料庫提供者從 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 05e638be5cc11f66052e5a1f6116e7205b824106
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>您已從不支援的資料提供者選取資料庫物件
O/R 設計工具支援的 SQL Server 的.NET Framework 資料提供者 (<xref:System.Data.SqlClient>)。 雖然您可以按一下**確定** 繼續使用來自不受支援的資料庫提供者的物件，您可能會在執行階段遇到未預期的行為。  
  
> [!NOTE]
>  只支援使用 .NET Framework Data Provider for SQL Server 的資料連接。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 按一下 [確定]。

   您可以繼續設計實體類別對應至使用不支援的資料庫提供者的連接。 如果使用不支援的資料庫提供者，則可能會發生非預期的行為。  
  
     -或-  
  
- 按一下**取消**。

   會停止動作。 請建立或使用 .NET Framework Provider for SQL Server 提供的資料連接。  
  
## <a name="see-also"></a>請參閱
[O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)