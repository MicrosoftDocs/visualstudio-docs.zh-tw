---
title: 選取的連接使用不支援的資料提供者
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ce72f9d4f93db5d4f96bfe54e6cb0d29f4e0727b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639972"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>選取的連接使用不支援的資料提供者

當您將不使用 .NET Framework Data Provider SQL Server 的專案從**伺服器總管**或**資料庫總管**拖曳至[LINQ to SQL 中的 Visual Studio 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)時，就會出現此訊息。

**O/R 設計**工具僅支援使用 SQL Server 之 .NET Framework 提供者的資料連線。 只有與 Microsoft SQL Server 或 Microsoft SQL Server 資料庫檔案的連接才是有效的連接。

若要更正這個錯誤，請只將使用 .NET Framework Data Provider SQL Server 的資料連線中的專案加入至**O/R 設計**工具。

## <a name="see-also"></a>請參閱

- <xref:System.Data.SqlClient>
- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
