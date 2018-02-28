---
title: "在 Visual Studio 中移除執行不到的程式碼重構 | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 1048458eb41a5c1f9842c3cfea1b3c8a553fbf20
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="remove-unreachable-code-refactoring"></a>移除執行不到的程式碼重構

此重構適用於：

- C#

**功能：**移除永遠不會執行的程式碼。

**時機：**您的程式沒有某個程式碼片段的路徑，使得該程式碼片段變成不必要的程式碼片段。

**原因：**藉由移除多餘且永遠不會執行的程式碼來提升可讀性和便於維護。

## <a name="how-to"></a>操作說明

1. 將游標放在執行不到之褪色程式碼中的任何位置：

![執行不到的褪色程式碼](media/unreachablecode-faded-cs.png)

1. 接著，執行下列其中一項操作：

   - **鍵盤**
     - 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [移除執行不到的程式碼]。
   - **滑鼠**
     - 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [移除執行不到的程式碼]。

1. 對變更感到滿意時，按 **Enter**或按一下功能表中的修正，便會認可變更。

範例：

```csharp
// Before
private void Method()
{
    throw new Exception(nameof(Method));
    Console.WriteLine($"Exception for method {nameof(Method)}");
}

// Remove unreachable code

// After
private void Method()
{
    throw new Exception(nameof(Method));
}
```

## <a name="see-also"></a>另請參閱

[重構](../refactoring-in-visual-studio.md)  
[預覽變更](../../ide/preview-changes.md)