---
title: 所選的連接使用不支援的資料庫提供者 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0a242cfb937d53be8a9acb61d9523c28544eef8f
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662058"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>選取的連接使用不支援的資料提供者
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您拖曳項目不使用.NET Framework Data Provider for SQL Server 時，會出現此訊息**伺服器總管**/**資料庫總管**拖曳至[LINQ to SQL在 Visual Studio 中的工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)。  
  
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]只支援使用 .NET Framework Provider for SQL Server 的資料連接。 只有與 Microsoft SQL Server 或 Microsoft SQL Server 資料庫檔案的連接才是有效的連接。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   只將使用 .NET Framework Data Provider for SQL Server 的資料連接中的項目加入至 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Data.SqlClient>   
 [.NET framework 資料提供者](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [逐步解說：建立 LINQ to SQL 類別 （O-R 設計工具）](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)