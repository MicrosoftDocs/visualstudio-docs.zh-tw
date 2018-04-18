---
title: 一或多個選取的項目包含設計工具不支援的資料類型 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 966adc7a4114c54479c0ad8c52a604e0fb5d3380
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>一個或多個選取的項目包含設計工具不支援的資料類型
從一或多個項目拖曳**伺服器總管**/**資料庫總管**到[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]包含不支援的資料型別[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]，例如[CLR 使用者定義型別](/dotnet/framework/data/adonet/sql/clr-user-defined-types)。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  建立檢視，這個檢視會依據所需的資料表，而且其中只包含受支援的資料型別。  
  
2.  將檢視從**伺服器總管**/**資料庫總管**拖曳至設計工具。  
  
## <a name="see-also"></a>另請參閱
[O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)