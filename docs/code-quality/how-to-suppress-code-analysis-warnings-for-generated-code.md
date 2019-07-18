---
title: 隱藏產生的程式碼的程式碼分析的違規
ms.date: 05/13/2019
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a7990f5e9fa1893d8813b1307ab6a0a7fee46be
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65613565"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>作法：隱藏所產生之程式碼的程式碼分析警告

產生的程式碼包含 managed 程式碼編譯器或第三方工具加入至專案的程式碼。 您可能想要查看產生的程式碼可探索程式碼分析規則違規。 不過，因為您無法檢視，並維護包含違規的程式碼，您可能不會想看到它們。

**隱藏所產生的程式碼的結果**專案的程式碼分析屬性頁面] 核取方塊可讓您選取是否要顯示的程式碼從協力廠商工具所產生的程式碼分析警告。

> [!NOTE]
> 這個選項不會在表單和範本中出現錯誤和警告時，抑制來自產生的程式碼的程式碼分析錯誤和警告。 您可以同時檢視及維護表單或範本的原始程式碼。

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>若要隱藏的警告，請在專案中產生程式碼

1. 中的專案上按一下滑鼠右鍵**方案總管**，然後按一下**屬性**。

2. 選擇**程式碼分析**] 索引標籤。

3. 選取 [**隱藏所產生的程式碼的結果**] 核取方塊。

> [!NOTE]
> 您只可以隱藏靜態程式碼分析的警告。 目前，您無法隱藏程式碼分析警告，從[分析器](roslyn-analyzers-overview.md)。