---
title: 產生結構的 IEquatable 運算子
description: 瞭解如何使用 [快速動作與重構] 功能表來產生結構的 Equals 和 IEquatable 運算子。
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 05792636e1094c53869f0235145aec73b26deea9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952976"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>產生結構的 Equals 時產生 IEquatable 運算子

此程式碼產生適用於：

- C#

事項 **：** 可讓您產生 [結構](/dotnet/csharp/language-reference/builtin-types/struct)的 **Equals** 和 **IEquatable** 運算子。

時機 **：** 您有一個結構，我們會為您自動新增 IEquatable 以及 equals 和 not equals 運算子。

**為什麼：**

- 如果您要實作實值型別，便應該考慮覆寫 **Equals** 方法，以獲得比在 ValueType 上實作預設 Equals 方法更好的效能。

- Implements IEquatable 介面會執行特定類型的 Equals ( # A1 方法。

## <a name="how-to"></a>使用方法

1. 將游標放在您的結構宣告行的某個位置。

2. 接著，執行下列其中一項操作：

   - 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

   - 以滑鼠右鍵按一下並選取 [快速動作與重構] 功能表。

   - 按一下 ![螺絲起子](../media/screwdriver-icon.png) 圖示。

   ![產生結構的 IEquatable 和 Equals](media/generate-equals-structs.png)

3. 從下拉式功能表中選取 [ **產生等於 (物件)** ]。

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)