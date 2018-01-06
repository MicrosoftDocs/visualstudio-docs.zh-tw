---
title: "移除無法連線到程式碼的重構 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: e57db74ea431d9090df1dc34fd3cff3cf03dd475
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="remove-unreachable-code-in-c"></a>在 C# 中移除無法到達的程式碼 #
**項目：**永遠不會執行的程式碼中移除。

**當：**程式有任何程式碼片段，進行不必要的程式碼片段的路徑。

**原因：**藉由移除多餘的程式碼提升可讀性和可維護性和絕對不會執行。

**如何：**

1. 將游標放在無法連線到淡出程式碼中的任何位置：

![無法連線到較淡的程式碼](media/unreachablecode_faded.png)  

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**移除無法連線到程式碼**從預覽視窗快顯視窗。
   * **滑鼠**
     * 以滑鼠右鍵按一下程式碼中，選取**快速控制項目及重構**功能表，然後選取**移除無法連線到程式碼**從預覽視窗快顯視窗。

1. 您很滿意變更，請按下**Enter**或按一下 [修正] 功能表中的，會認可變更。

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

## <a name="see-also"></a>請參閱  
[重構 (C#)](../refactoring-csharp.md)  
[預覽變更](../../ide/preview-changes.md)