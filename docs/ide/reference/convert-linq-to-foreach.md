---
title: 重構程式碼以將 LINQ 查詢轉換為 foreach 陳述式
ms.date: 05/15/2018
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
ms.openlocfilehash: e3e4e448931e028c53d62c534e2785e4f026a7ec
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>重構以將 LINQ 轉換為 foreach 陳述式

使用這個重構以將 [LINQ 查詢語法](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq)轉換為 [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 陳述式。

此重構適用於：

- C#

## <a name="how-to-use-it"></a>如何使用

1. 選取開頭為 `from` 的整個 LINQ 查詢。

   > [!NOTE]
   > 這個重構只能用來轉換以查詢語法而非方法語法表示的 LINQ 查詢。

1. 在字行任何地方按 **Ctrl**+**.**， 或按一下程式碼檔案邊界的螺絲起子 ![螺絲起子圖示](../media/screwdriver-icon.png) 圖示。

   ![將 LINQ 轉換為 foreach 快速動作功能表](media/convert-linq-to-foreach.png)

1. 選取 [轉換為 'foreach']。 或選取 [預覽變更] 以開啟 [[預覽變更]](../../ide/preview-changes.md) 對話方塊，然後選取 [套用]。

> [!NOTE]
> 就 C# 而言，這些重構所產生的程式碼會針對 `foreach` 迴圈的反覆運算變數，使用明確的類型或 [var](/dotnet/csharp/language-reference/keywords/var)。 所產生程式碼中的類型 (不論是明確還是隱含) 會取決於範圍內的程式碼樣式設定。 設定這些特定程式碼樣式設定時，是在電腦層級的下列位置底下設定：[工具] > [選項] > [文字編輯器] > [C#] > [程式碼樣式] > [一般] > [\'var' 喜歡設定]，或在 [EditorConfig](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types) 檔案中的方案層級設定。 如果您在 [選項] 中變更某個程式碼樣式，請重新開啟程式碼檔案以讓變更生效。

## <a name="see-also"></a>另請參閱

- [LINQ](/dotnet/standard/using-linq)
- [重構](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)