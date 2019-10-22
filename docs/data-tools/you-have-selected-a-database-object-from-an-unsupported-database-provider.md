---
title: 您已從不支援的資料提供者選取資料庫物件
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b1dd14c428b90b87e665aa41681b5a9e68eb00e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648013"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>您已從不支援的資料提供者選取資料庫物件

**O/R 設計**工具僅支援 SQL Server （<xref:System.Data.SqlClient>）的 .NET Framework Data Provider。 雖然您可以按一下 [確定] 繼續使用來自不支援之資料庫提供者的物件，但是在執行階段可能會發生非預期性行為。

> [!NOTE]
> 只支援使用 .NET Framework Data Provider for SQL Server 的資料連接。

## <a name="options"></a>選項

- 按一下 [確定] 以繼續設計對應到使用不受支援之資料庫提供者之連線的實體類別。 如果使用不支援的資料庫提供者，則可能會發生非預期的行為。

- 按一下 [**取消**] 以停止動作。 建立或使用不同的資料連線，以使用 .NET Framework 提供者進行 SQL Server。

## <a name="see-also"></a>請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)