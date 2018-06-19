---
title: 選取的連接使用不支援的資料提供者
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 77519a5497c26553e2023862e46f3ba618e4f99f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920931"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>選取的連接使用不支援的資料提供者

當您拖曳項目不使用 SQL server 的.NET Framework Data Provider 時，會出現此訊息**伺服器總管**/**資料庫總管**到[LINQ to SQLVisual Studio 中的工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)。

[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]只支援使用 .NET Framework Provider for SQL Server 的資料連接。 只有與 Microsoft SQL Server 或 Microsoft SQL Server 資料庫檔案的連接才是有效的連接。

若要更正這個錯誤，將只有項目加入資料連接中使用.NET Framework Data Provider for SQL Server 的[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]。

## <a name="see-also"></a>另請參閱

- <xref:System.Data.SqlClient>
- [O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
