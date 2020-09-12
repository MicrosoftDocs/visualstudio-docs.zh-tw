---
title: 不支援的資料類型
description: 一個或多個選取的項目包含設計工具不支援的資料類型
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 167146b9a7938e5498e8db023602b2e13f74379c
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2020
ms.locfileid: "90034074"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>一個或多個選取的項目包含設計工具不支援的資料類型

從 **伺服器總管** 或 **資料庫總管** 拖曳至 **o/r 設計** 工具的一或多個專案包含 **o/r 設計**工具不支援的資料類型，例如 [CLR 使用者定義類型](/dotnet/framework/data/adonet/sql/clr-user-defined-types)。

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 建立檢視，這個檢視會依據所需的資料表，而且其中只包含受支援的資料型別。

2. 從 **伺服器總管** 或 **資料庫總管** 將視圖拖曳至設計工具。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
