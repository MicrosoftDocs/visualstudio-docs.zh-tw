---
title: 重構程式碼以將 for 迴圈轉換成 foreach 陳述式
ms.date: 05/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 34758473bcbee8ccad7d9dff9df2f1478ca1202c
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/11/2018
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>重構以在 for 迴圈與 foreach 陳述式之間轉換

這些重構適用於：

- C#

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>將 for 迴圈轉換成 foreach 陳述式

若您的程式碼中有 [for](/dotnet/csharp/language-reference/keywords/for) 迴圈，您可以使用此重構，將其轉換為 [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 陳述式。

### <a name="why-convert"></a>轉換的理由

將 [for](/dotnet/csharp/language-reference/keywords/for) 迴圈轉換為 [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 陳述式的理由包括：

- 您不會在迴圈內使用反覆運算計數變數，除了當作索引來存取項目以外。

- 您想要簡化程式碼，以及減少初始設定式、條件及反覆運算陳述式出現邏輯錯誤的可能性。

### <a name="how-to-use-it"></a>如何使用

1. 將游標放在 `for` 迴圈的第一行。

1. 在字行任何地方按 **Ctrl**+**.**， 或按一下程式碼檔案邊界的螺絲起子 ![螺絲起子圖示](../media/screwdriver-icon.png) 圖示。

   ![轉換為 foreach 功能表](media/convert-to-foreach.png)

1. 選取 [轉換為 'foreach']。 或選取 [預覽變更] 以開啟 [[預覽變更]](../../ide/preview-changes.md) 對話方塊，然後選取 [套用]。

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>將 foreach 陳述式轉換成 for 迴圈

若您的程式碼中有 [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 陳述式，您可以使用此重構，將其轉換為 [for](/dotnet/csharp/language-reference/keywords/for) 迴圈。

### <a name="why-convert"></a>轉換的理由

將 [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 陳述式轉換為 [for](/dotnet/csharp/language-reference/keywords/for) 迴圈的理由包括：

- 您想要在迴圈中使用反覆運算計數變數，而不只是存取項目。

- 您[透過多維度陣列反覆運算](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays)，並想要陣列元素的更多控制權。

### <a name="how-to-use-it"></a>如何使用

1. 將游標放在 `foreach` 陳述式的第一行。

1. 在字行任何地方按 **Ctrl**+**.**， 或按一下程式碼檔案邊界的螺絲起子 ![螺絲起子圖示](../media/screwdriver-icon.png) 圖示。

   ![轉換為 for 功能表](media/convert-to-for.png)

1. 選取 [轉換為 'for']。 或選取 [預覽變更] 以開啟 [[預覽變更]](../../ide/preview-changes.md) 對話方塊，然後選取 [套用]。

1. 由於重構採用了新的反覆運算計數變數，因此 [重新命名] 方塊會顯示在編輯器的右上角。 若您想為變數選擇其他名稱，請鍵入名稱後按 **Enter 鍵**或選取 [重新命名] 方塊中的 [套用]。 若您不想選擇新名稱，則按 **Esc 鍵**或選取 [套用] 關閉 [重新命名] 方塊。

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)