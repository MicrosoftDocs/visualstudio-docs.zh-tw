---
title: 將變數宣告移到靠近參考的位置
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 35735009a5b813ca29159f276fe2d5abb734be0e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585280"
---
# <a name="move-declaration-near-reference-refactoring"></a>將宣告移到靠近參考的位置重構

此重構適用於：

- C#

**功能：** 讓您將變數宣告移到靠近其使用方式的位置。

**時機：** 您有可以在更小範圍中的變數宣告。

**原因：** 您可以保持不變，但可能造成可讀性問題或資訊隱藏。 這是一個可進行重構來提升可讀性的機會。

## <a name="how-to"></a>操作說明

1. 將游標放在變數宣告中。

1. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 在字行任何地方按 **Ctrl**+ **.** ， 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [將宣告移近參考]。
   - **滑鼠**
      - 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [將宣告移近參考]。

1. 對變更感到滿意時，按 **Enter**或按一下功能表中的修正，便會認可變更。

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

- [重構](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
