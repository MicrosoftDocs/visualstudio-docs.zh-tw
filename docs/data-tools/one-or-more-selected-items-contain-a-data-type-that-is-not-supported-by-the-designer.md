---
title: 一個或多個選取的項目包含設計工具不支援的資料類型
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 036026d7640dc525538191d2acc347e9ba18b871
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648258"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>一個或多個選取的項目包含設計工具不支援的資料類型

從**伺服器總管**或**資料庫總管**拖曳至**o/r 設計**工具的一個或多個專案包含**O/r 設計**工具不支援的資料類型，例如[CLR 使用者定義類型](/dotnet/framework/data/adonet/sql/clr-user-defined-types)。

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 建立檢視，這個檢視會依據所需的資料表，而且其中只包含受支援的資料型別。

2. 將視圖從**伺服器總管**或**資料庫總管**拖曳到設計工具上。

## <a name="see-also"></a>請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)