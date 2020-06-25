---
title: 隱藏所產生程式碼的程式碼分析違規
ms.date: 05/13/2019
ms.topic: how-to
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 175df8bb4dded4f66508ef405e031178606fd531
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371803"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>如何：隱藏所產生程式碼的程式碼分析警告

產生的程式碼包含由 managed 程式碼編譯器或協力廠商工具加入至專案的程式碼。 您可能想要查看程式碼分析在產生的程式碼中探索到的規則違規。 不過，由於您無法查看及維護包含違規的程式碼，因此您可能不會想要查看它們。

專案的 [程式碼分析] 屬性頁上的 [**從產生的程式碼隱藏結果**] 核取方塊，可讓您選取是否要從協力廠商工具產生的程式碼顯示程式碼分析警告。

> [!NOTE]
> 這個選項不會在表單和範本中出現錯誤和警告時，抑制來自產生的程式碼的程式碼分析錯誤和警告。 您可以同時檢視及維護表單或範本的原始程式碼。

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>若要隱藏專案中產生之程式碼的警告

1. 以滑鼠右鍵按一下**方案總管**中的專案，然後按一下 [**屬性**]。

2. 選擇 [程式**代碼分析**] 索引標籤。

3. 選取 [**隱藏產生的程式碼的結果**] 核取方塊。

> [!IMPORTANT]
> 您只能隱藏舊版分析的警告。 具有此設定的屬性頁已被取代，將在未來的產品版本中移除。 目前，您無法從[分析器](roslyn-analyzers-overview.md)隱藏程式碼分析警告。
