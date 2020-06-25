---
title: 您已從不支援的資料提供者選取資料庫物件
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5721cf340a09c138521e7134a0d19484561eb3a0
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85280976"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>您已從不支援的資料提供者選取資料庫物件

**O/R 設計**工具僅支援 SQL Server 的 .NET Framework Data Provider （ <xref:System.Data.SqlClient> ）。 雖然您可以按一下 [確定]**** 繼續使用來自不支援之資料庫提供者的物件，但是在執行階段可能會發生非預期性行為。

> [!NOTE]
> 只支援使用 .NET Framework Data Provider for SQL Server 的資料連接。

## <a name="options"></a>選項

- 按一下 [確定]**** 以繼續設計對應到使用不受支援之資料庫提供者之連線的實體類別。 如果使用不支援的資料庫提供者，則可能會發生非預期的行為。

- 按一下 [**取消**] 以停止動作。 建立或使用不同的資料連線，以使用 .NET Framework 提供者進行 SQL Server。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
