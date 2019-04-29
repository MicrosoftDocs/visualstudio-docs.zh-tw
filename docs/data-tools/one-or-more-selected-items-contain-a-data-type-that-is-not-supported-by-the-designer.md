---
title: 一個或多個選取的項目包含設計工具不支援的資料類型
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 12ec2ed7dc2a12556fcb6eeeddbe2d0745ae7f72
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566364"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>一個或多個選取的項目包含設計工具不支援的資料類型

從一或多個項目拖曳**伺服器總管**或是**資料庫總管**拖曳至**O/R 設計工具**包含不支援的資料型別**O/R 設計師**，例如[CLR 使用者定義型別](/dotnet/framework/data/adonet/sql/clr-user-defined-types)。

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 建立檢視，這個檢視會依據所需的資料表，而且其中只包含受支援的資料型別。

2. 將檢視從**伺服器總管**或是**資料庫總管**拖曳至設計工具。

## <a name="see-also"></a>另請參閱

- [O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)
- [Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)