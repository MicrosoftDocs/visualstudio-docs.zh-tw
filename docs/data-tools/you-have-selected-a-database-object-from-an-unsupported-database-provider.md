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
ms.openlocfilehash: f3ab7375db8c3adfe769cf1c344937b60695eb25
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>您已從不支援的資料提供者選取資料庫物件

O/R 設計工具支援的 SQL Server 的.NET Framework 資料提供者 (<xref:System.Data.SqlClient>)。 雖然您可以按一下**確定** 繼續使用來自不受支援的資料庫提供者的物件，您可能會在執行階段遇到未預期的行為。

> [!NOTE]
> 只支援使用 .NET Framework Data Provider for SQL Server 的資料連接。

## <a name="to-correct-this-error"></a>更正這個錯誤

- 按一下 [確定 **Deploying Office Solutions**]。

   您可以繼續設計實體類別對應至使用不支援的資料庫提供者的連接。 如果使用不支援的資料庫提供者，則可能會發生非預期的行為。

    -或-

- 按一下**取消**。

   會停止動作。 請建立或使用 .NET Framework Provider for SQL Server 提供的資料連接。

## <a name="see-also"></a>另請參閱

- [O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)