---
title: 重構程式碼以將 LINQ 查詢轉換為 foreach 陳述式
description: 將以查詢語法撰寫的任何 LINQ 查詢語法轉換為 foreach 陳述式。
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
ms.openlocfilehash: 6e1b24cb8406ff29659eb79d1d9fa856db628b89
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094092"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>重構以將 LINQ 轉換為 foreach 陳述式

使用這個重構以將 [LINQ 查詢語法](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq)轉換為 [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 陳述式。

此重構適用於：

- C#

- Visual Basic

## <a name="how-to-use-it"></a>如何使用它

1. 選取開頭為 `from` 的整個 LINQ 查詢。

   > [!NOTE]
   > 這個重構只能用來轉換以查詢語法而非方法語法表示的 LINQ 查詢。

1. 按**Ctrl**+**。** 或按一下程式碼檔案邊界的螺絲起子 ![螺絲起子圖示](../media/screwdriver-icon.png) 圖示。

   ![將 LINQ 轉換為 foreach 快速動作功能表](media/convert-linq-to-foreach.png)

1. 選取 [轉換為 'foreach']****。 或選取 [預覽變更]**** 以開啟 [[預覽變更]](../../ide/preview-changes.md) 對話方塊，然後選取 [套用]****。

> [!NOTE]
> 就 C# 而言，這些重構所產生的程式碼會針對 `foreach` 迴圈的反覆運算變數，使用明確的類型或 [var](/dotnet/csharp/language-reference/keywords/var)。 所產生程式碼中的類型 (不論是明確還是隱含) 會取決於範圍內的程式碼樣式設定。 這些特定的代碼樣式設置在**工具** > **選項** > **文字編輯器** > **C#** > **代碼樣式** > **一般** > **\'var 的首選項**下或在[編輯器配置](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types)檔中的解決方案級別配置。 如果您在 [選項]**** 中變更某個程式碼樣式，請重新開啟程式碼檔案以讓變更生效。

## <a name="see-also"></a>另請參閱

- [LINQ](/dotnet/standard/using-linq)
- [Refactoring](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
