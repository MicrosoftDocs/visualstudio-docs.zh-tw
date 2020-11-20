---
title: 不支援的資料庫提供者
description: 選取的連接使用不支援的資料庫提供者。 查看此 Visual Studio 物件關聯式設計工具 (O/R 設計工具) 訊息的相關資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 06e08f9a9c28698ae2ee2fecfbcec64c39666c8a
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998343"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>選取的連接使用不支援的資料提供者

當您將不使用 .NET Framework Data Provider SQL Server 的專案從 **伺服器總管** 或 **資料庫總管** 拖曳至 LINQ to SQL [中的 Visual Studio 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)時，會出現此訊息。

**O/R 設計** 工具僅支援使用 .NET Framework 提供者進行 SQL Server 的資料連線。 只有與 Microsoft SQL Server 或 Microsoft SQL Server 資料庫檔案的連接才是有效的連接。

若要更正這個錯誤，請只將使用 .NET Framework Data Provider SQL Server 的資料連線中的專案加入至 **O/R 設計** 工具。

## <a name="see-also"></a>另請參閱

- <xref:System.Data.SqlClient>
- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
