---
title: 產生參數重構
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 372a3f705e5e85c0edb31a754105f61056402b9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094358"
---
# <a name="generate-parameter"></a>產生參數

此重構適用於：

- C#

- Visual Basic

**內容：** 自動生成方法參數。

**何時：** 引用方法中的變數，該變數在當前上下文中不存在並收到錯誤;因此，請引用當前上下文中不存在的變數。但是，如果該方法在當前上下文中不存在，則會導致錯誤。可以生成參數作為代碼修復。 

**原因：** 您可以快速修改方法簽名，而不會丟失上下文。

## <a name="how-to"></a>操作方式

1. 將游標放在變數名稱中，然後按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。
1. 選取 [產生參數]****。

   ![產生參數](media/generate-parameter.png) 

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)
