---
title: 您已從不支援的資料提供者選取資料庫物件
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 209ab92e3a24733e2ef4b7b912a36ae920ffffdb
ms.sourcegitcommit: 59c48e1e42b48ad25a4e198af670faa4d8dae370
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2019
ms.locfileid: "54204240"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>您已從不支援的資料提供者選取資料庫物件

**O/R Designer**適用於 SQL Server 支援.NET Framework 資料提供者 (<xref:System.Data.SqlClient>)。 雖然您可以按一下 [確定] 繼續使用來自不支援之資料庫提供者的物件，但是在執行階段可能會發生非預期性行為。

> [!NOTE]
> 只支援使用 .NET Framework Data Provider for SQL Server 的資料連接。

## <a name="options"></a>選項

- 按一下 [確定] 以繼續設計對應到使用不受支援之資料庫提供者之連線的實體類別。 如果使用不支援的資料庫提供者，則可能會發生非預期的行為。

- 按一下 **取消**停止動作。 建立或使用不同的資料連接所使用的.NET Framework Provider for SQL Server。

## <a name="see-also"></a>另請參閱

- [O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)
- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)