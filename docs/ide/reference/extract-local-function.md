---
title: 擷取區域函式
description: 選取程式碼並輸入 Ctrl+R、Ctrl+M，將程式碼片段轉換成它自己的方法。
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 031fbe22ec61837d489df7a6af923ef0cd2454c7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77515327"
---
# <a name="extract-local-function-refactoring"></a>提取局部函數重構

此重構適用於：

- C#

**內容：** 允許您將代碼片段從現有方法轉換為本地函數。

**何時：** 您在某些方法中具有現有代碼的片段，需要從本地函式呼叫。

**原因：** 您可以複製/貼上該程式碼，但那樣會造成重複。 更好的解決方案是將片段重構為其自己的局部函數。

## <a name="how-to"></a>操作方式

1. 突出顯示要提取的代碼。

2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。 

3. 選取 [擷取區域函式]****。

    ![擷取區域函式](media/extract-local-function.png)

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
