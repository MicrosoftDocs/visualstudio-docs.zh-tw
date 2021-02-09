---
title: 重構程式碼以將 var 取代為明確類型
description: 瞭解如何使用快速動作，以明確型別取代區域變數運算式中的 var。
ms.custom: SEO-VS-2020
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: d45d4ffcbdedb456bde40b3fd1103fa8b21a8f9b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919594"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>重構以將 var 取代為明確類型

使用這個重構以將本機變數宣告中的 [var](/dotnet/csharp/language-reference/keywords/var) 取代為明確類型。

此重構適用於：

- C#

## <a name="why-to-use-an-explicit-type"></a>為何要使用明確類型

以下是以明確類型宣告變數的一些原因：

- 改善程式碼的可讀性。

- 您不想要在宣告中將變數初始化。

不過，以匿名類型將變數初始化，且稍後才會存取物件的屬性時，則必須使用 [var](/dotnet/csharp/language-reference/keywords/var)。 如需詳細資訊，請參閱[隱含類型區域變數 (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)。

## <a name="how-to-use-it"></a>用法

1. 將插入號放在 `var` 關鍵字上。

1. 按下 **Ctrl** + **。** 或按一下程式碼檔案邊界的螺絲起子 ![螺絲起子圖示](../media/screwdriver-icon.png) 圖示。

   ![使用明確類型快速動作功能表](media/use-explicit-type.png)

1. 選取 [使用明確類型]。 或選取 [預覽變更] 以開啟 [[預覽變更]](../../ide/preview-changes.md) 對話方塊，然後選取 [套用]。

## <a name="see-also"></a>另請參閱

- [隱含類型變數 (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [重構](../refactoring-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
