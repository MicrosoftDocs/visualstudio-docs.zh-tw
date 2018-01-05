---
title: "移動靠近參考-重構 (C#) 的宣告 |Microsoft 文件"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: d79d55ae-f6bb-4902-8db2-e7fe01bdb0bf
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: c274fd758fdae468bee884fcf1686abc16ec1d7e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="move-declaration-near-reference-in-c"></a>在 C# 中移動靠近參考的宣告 #
**項目：**可讓您將更接近變數宣告移至其使用方式。

**當：**有可能是較窄的範圍中的變數宣告。

**原因：**無法為是，但卻可能導致可讀性問題或資訊隱藏保留。 這是要重構機會，以提高可讀性。

**如何：**

1. 將游標放在變數宣告中。

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**移動靠近參考的宣告**從預覽視窗快顯視窗。
   * **滑鼠**
     * 以滑鼠右鍵按一下程式碼中，選取**快速控制項目及重構**功能表，然後選取**移動靠近參考的宣告**從預覽視窗快顯視窗。

1. 您很滿意變更，請按下**Enter**或按一下 [修正] 功能表中的，會認可變更。

範例：
```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>請參閱  
[重構 (C#)](../refactoring-csharp.md)  
[預覽變更](../../ide/preview-changes.md)