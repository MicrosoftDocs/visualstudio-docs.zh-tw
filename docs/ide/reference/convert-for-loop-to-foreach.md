---
title: 重構程式碼以將 for 迴圈轉換成 foreach 陳述式
ms.date: 05/10/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 3d35897bd928166410ffd950534277cfac2c06b7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654546"
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>重構以在 for 迴圈與 foreach 陳述式之間轉換

本文說明在兩個迴圈結構之間進行轉換的快速動作重構。 其中包括您可能會想要在程式碼中於 [for](/dotnet/csharp/language-reference/keywords/for) 迴圈與 [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 陳述式之間切換的原因。

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>將 for 迴圈轉換成 foreach 陳述式

若您的程式碼中有 [for](/dotnet/csharp/language-reference/keywords/for) 迴圈，您可以使用此重構，將其轉換為 [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 陳述式。

此重構適用於：

- C#

> [!NOTE]
> [轉換為 foreach] 快速動作重構僅適用於包含下列所有三個組件的 [for](/dotnet/csharp/language-reference/keywords/for) 迴圈：初始設定式、條件及迭代器。

### <a name="why-convert"></a>轉換的理由

將 [for](/dotnet/csharp/language-reference/keywords/for) 迴圈轉換為 [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 陳述式的理由包括：

- 除了當作用來存取項目的索引之外，您不會在迴圈內使用區域迴圈變數。

- 您想要簡化程式碼，以及降低初始設定式、條件及迭代器區段中發生邏輯錯誤的可能性。

### <a name="how-to-use-it"></a>如何使用

1. 將插入號放在 `for` 關鍵字中。

1. 在字行任何地方按 **Ctrl**+ **.** ， 或按一下程式碼檔案邊界的螺絲起子 ![螺絲起子圖示](../media/screwdriver-icon.png) 圖示。

   ![轉換為 foreach 功能表](media/convert-to-foreach.png)

1. 選取 [轉換為 'foreach']。 或選取 [預覽變更] 以開啟 [[預覽變更]](../../ide/preview-changes.md) 對話方塊，然後選取 [套用]。

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>將 foreach 陳述式轉換成 for 迴圈

如果您的程式碼中有 [foreach (C#)](/dotnet/csharp/language-reference/keywords/foreach-in) 或 [For Each...Next (Visual Basic)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) 陳述式，則可以使用此重構將其轉換為 [for](/dotnet/csharp/language-reference/keywords/for) 迴圈。

此重構適用於：

- C#

- Visual Basic

### <a name="why-convert"></a>轉換的理由

將 [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 陳述式轉換為 [for](/dotnet/csharp/language-reference/keywords/for) 迴圈的理由包括：

- 除了存取項目之外，您想要在迴圈內使用區域迴圈變數來進行其他工作。

- 您[透過多維度陣列反覆運算](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays)，並想要對陣列元素有更多控制權。

### <a name="how-to-use-it"></a>如何使用

1. 將插入號放在 `foreach` 或 `For Each` 關鍵字中。

1. 在字行任何地方按 **Ctrl**+ **.** ， 或按一下程式碼檔案邊界的螺絲起子 ![螺絲起子圖示](../media/screwdriver-icon.png) 圖示。

   ![轉換為 for 功能表](media/convert-to-for.png)

1. 選取 [轉換為 'for']。 或選取 [預覽變更] 以開啟 [[預覽變更]](../../ide/preview-changes.md) 對話方塊，然後選取 [套用]。

1. 由於重構採用了新的反覆運算計數變數，因此 [重新命名] 方塊會顯示在編輯器的右上角。 若您想為變數選擇其他名稱，請鍵入名稱後按 **Enter 鍵**或選取 [重新命名] 方塊中的 [套用]。 若您不想選擇新名稱，則按 **Esc 鍵**或選取 [套用] 關閉 [重新命名] 方塊。

> [!NOTE]
> 就 C# 而言，這些重構所產生的程式碼會針對集合中項目的類型，使用明確的類型或 [var](/dotnet/csharp/language-reference/keywords/var)。 所產生程式碼中的類型 (不論是明確還是隱含) 會取決於範圍內的程式碼樣式設定。 設定這些特定程式碼樣式設定時，是在電腦層級的下列位置底下設定：[工具] > [選項] > [文字編輯器] > [C#] > [程式碼樣式] > [一般] > [\'var' 喜歡設定]，或在 [EditorConfig](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types) 檔案中的方案層級設定。 如果您在 [選項] 中變更某個程式碼樣式，請重新開啟程式碼檔案以讓變更生效。

## <a name="see-also"></a>請參閱

- [重構](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
