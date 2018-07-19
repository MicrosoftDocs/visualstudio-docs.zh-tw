---
title: 您已從不支援的資料提供者選取資料庫物件
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5b6eef41ebd3ae6fc08029a618cf276e22001235
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37116872"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>您已從不支援的資料提供者選取資料庫物件

**O/R Designer**適用於 SQL Server 支援.NET Framework 資料提供者 (<xref:System.Data.SqlClient>)。 雖然您可以按一下**確定**並繼續使用不支援的資料庫提供者的物件，您可能會在執行階段遇到非預期的行為。

> [!NOTE]
> 只支援使用 .NET Framework Data Provider for SQL Server 的資料連接。

## <a name="to-correct-this-error"></a>更正這個錯誤

- 按一下 [確定 **Deploying Office Solutions**]。

   您可以繼續設計實體類別對應至使用不支援的資料庫提供者的連接。 如果使用不支援的資料庫提供者，則可能會發生非預期的行為。

    -或-

- 按一下 **取消**。

   會停止動作。 請建立或使用 .NET Framework Provider for SQL Server 提供的資料連接。

## <a name="see-also"></a>另請參閱

- [O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL 工具，在 Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)