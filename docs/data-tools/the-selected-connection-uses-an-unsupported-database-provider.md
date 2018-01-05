---
title: "所選的連接使用不支援的資料庫提供者 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: abd7ba49b3a9bb449f4f323deee588c3942d37a4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>選取的連接使用不支援的資料提供者
當您拖曳項目不使用 SQL server 的.NET Framework Data Provider 時，會出現此訊息**伺服器總管**/**資料庫總管**到[LINQ to SQLVisual Studio 中的工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)。  
  
 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]只支援使用 .NET Framework Provider for SQL Server 的資料連接。 只有與 Microsoft SQL Server 或 Microsoft SQL Server 資料庫檔案的連接才是有效的連接。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   只將使用 .NET Framework Data Provider for SQL Server 的資料連接中的項目加入至 [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。  
  
## <a name="see-also"></a>另請參閱
<xref:System.Data.SqlClient>  
[O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
