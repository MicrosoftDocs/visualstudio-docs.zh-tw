---
title: 將 switch 陳述式轉換為 switch 運算式
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cc13cffe8352d9fb57f5bb991c3af615eddb2a14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68740046"
---
# <a name="convert-switch-statement-to-switch-expression"></a>將 switch 陳述式轉換為 switch 運算式

此重構適用於：

- C#

事項 **：** 將[switch 語句](/dotnet/csharp/language-reference/keywords/switch)轉換成 c # 8.0 [switch 運算式](/dotnet/csharp/whats-new/csharp-8#switch-expressions)。

時機 **：** 您想要將語句轉換成 `switch` `switch` 運算式，反之亦然。 

**原因：** 如果您只使用運算式，這種重整功能可讓您輕鬆地從傳統的 `switch` 語句轉換。

## <a name="how-to"></a>操作方式

1. 請在您的專案檔案中，[將語言版本設定為之前版本](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file)，因為 `switch` 運算式現在是新的 C# 8.0 功能。
2. 將游標放在 `switch` 關鍵字中，然後按下**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。
3. 選取 [將 switch 陳述式轉換為運算式]****。

   ![將 switch 陳述式轉換為 switch 運算式](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
