---
title: 未使用的值和參數
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce2b0f1e0c0db45c478c3917306683b314da0564
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531868"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>未使用的值指派、變數及參數

此重構適用於：

- C#
- Visual Basic

**內容：** 淡出未使用的參數，並生成未使用的運算式值的警告。 編譯器也會執行資料流程分析，以尋找任何未使用的值指派。 未使用的值指派會淡出，並會顯示包含[快速動作](../quick-actions.md)的燈泡，以移除重複的指派。 包含未知值的未使用變數會顯示[快速動作](../quick-actions.md)建議，以改用 [Discard](/dotnet/csharp/discards)。 (Discard 是應用程式程式碼中刻意未使用的暫存虛擬變數。 可以減少記憶體配置，並使您的程式碼更易於閱讀。)

**何時：** 您具有從未使用過的值賦值、參數或運算式值。

**原因：** 有時很難判斷是否不再使用值賦值、變數或參數。 藉由淡出這些值或產生警告，您就能清楚了解哪些程式碼可以刪除。

## <a name="unused-expression-values-and-parameters-diagnostic"></a>未使用的運算式值和參數診斷

1. 擁有未使用的值指派、變數或參數。
2. 未使用的值分配或參數似乎已淡出。未使用的運算式值將生成警告。

  ![未使用的參數](media/unused-parameter.png)
  ![未使用的值](media/unused-value.png)
  ![未使用的值指派](media/unused-value-assignment.png)
  ![未使用的值 Discard](media/unused-value-discard.png)

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)
- [.NET 開發人員的祕訣](../csharp-developer-productivity.md)
