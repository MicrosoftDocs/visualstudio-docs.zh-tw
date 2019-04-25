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
ms.openlocfilehash: 2d0875f9a298af24575cc05008713cbb6c3e2ead
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789728"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>未使用的值指派、變數及參數

此重構適用於：

- C#
- Visual Basic

**功能：** 淡化未使用的參數，並為未使用的運算式值產生警告。 編譯器也會執行資料流程分析，以尋找任何未使用的值指派。 未使用的值指派會淡出，並會顯示包含[快速動作](../quick-actions.md)的燈泡，以移除重複的指派。 包含未知值的未使用變數會顯示[快速動作](../quick-actions.md)建議，以改用 [Discard](/dotnet/csharp/discards)。 (Discard 是應用程式程式碼中刻意未使用的暫存虛擬變數。 可以減少記憶體配置，並使您的程式碼更易於閱讀。)

**時機：** 您擁有從未使用的值指派、參數或運算式值。

**原因：** 有時候很難分辨值指派、變數或參數是否已不再使用。 藉由淡出這些值或產生警告，您就能清楚了解哪些程式碼可以刪除。

## <a name="unused-expression-values-and-parameters-diagnostic"></a>未使用的運算式值和參數診斷

1. 擁有未使用的值指派、變數或參數。
2. 未使用的值指派或參數會以淡出顯示。未使用的運算式值會產生警告。

  ![未使用的參數](media/unused-parameter.png)
  ![未使用的值](media/unused-value.png)
  ![未使用的值指派](media/unused-value-assignment.png)
  ![未使用的值 Discard](media/unused-value-discard.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [.NET 開發人員的秘訣](../../ide/visual-studio-2017-for-dotnet-developers.md)
