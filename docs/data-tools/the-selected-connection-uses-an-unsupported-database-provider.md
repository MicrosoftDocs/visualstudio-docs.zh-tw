---
title: 選取的連接使用不支援的資料提供者
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e6ebdca67dd87f25111ba48c3d9baa346d00e4db
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923807"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>選取的連接使用不支援的資料提供者

當您拖曳項目不使用.NET Framework Data Provider for SQL Server 時，會出現此訊息**伺服器總管**或**資料庫總管**拖曳至[視覺效果中的 LINQ to SQL 工具Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)。

**O/R Designer**支援只使用.NET Framework Provider for SQL Server 的資料連線。 只有與 Microsoft SQL Server 或 Microsoft SQL Server 資料庫檔案的連接才是有效的連接。

若要更正這個錯誤，請從使用.NET Framework Data Provider for SQL Server 的資料連接中加入只有項目**O/R Designer**。

## <a name="see-also"></a>另請參閱

- <xref:System.Data.SqlClient>
- [O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)
- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
