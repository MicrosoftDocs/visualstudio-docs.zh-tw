---
title: 隱藏所產生程式碼的程式碼分析違規
ms.date: 05/13/2019
description: 瞭解如何隱藏所產生程式碼的程式碼分析警告。 瞭解如何防止 Visual Studio 顯示有關產生之程式碼的舊版分析警告。
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a149511b447f1f21d180eaf526ebc3d991c95997
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859940"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>如何：隱藏所產生程式碼的程式碼分析警告

產生的程式碼包含由 managed 程式碼編譯器或協力廠商工具新增至專案的程式碼。 您可能會想要查看程式碼分析在產生的程式碼中發現的規則違規。 不過，由於您無法查看和維護包含違規的程式碼，因此您可能不會想要查看它們。

專案的 [程式碼分析] 屬性頁上的 [ **隱藏來自產生的程式碼的結果** ] 核取方塊，可讓您選擇是否要從協力廠商工具產生的程式碼中顯示程式碼分析警告。

> [!NOTE]
> 這個選項不會在表單和範本中出現錯誤和警告時，抑制來自產生的程式碼的程式碼分析錯誤和警告。 您可以同時檢視及維護表單或範本的原始程式碼。

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>隱藏專案中產生之程式碼的警告

1. 在 **方案總管** 中的專案上按一下滑鼠右鍵，然後按一下 [ **屬性**]。

2. 選擇 [程式 **代碼分析** ] 索引標籤。

3. 選取 [ **從產生的程式碼隱藏結果** ] 核取方塊。

> [!IMPORTANT]
> 您只能隱藏來自舊版分析的警告。 具有此設定的屬性頁面已被取代，並將在未來的產品版本中移除。 目前，您無法從 [分析器](roslyn-analyzers-overview.md)隱藏程式碼分析警告。
