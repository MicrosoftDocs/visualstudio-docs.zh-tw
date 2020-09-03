---
title: 產生執行 IComparable 之類型的比較運算子
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 31e33b562a5a11ff77c1d610fbce9e90506b036d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85290158"
---
# <a name="generate-comparison-operators-for-types-that-implement-icomparable"></a>產生執行 IComparable 之類型的比較運算子

此程式碼產生適用於：

- C#

事項 **：** 可讓您針對實 IComparable 的型別產生**比較**運算子。

時機 **：** 您有一個可實 IComparable 的型別，我們會自動加入比較運算子。

**原因：** 如果您要執行實值型別，您應該考慮覆寫 **equals** 方法，以提升 ValueType 上 equals 方法的預設執行效能。

## <a name="how-to"></a>操作方式

1. 將游標放在類別或 IComparable 關鍵字的內部。

2. 接著，執行下列其中一項操作：

   - 按下**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。

   - 以滑鼠右鍵按一下並選取 [快速動作與重構]**** 功能表。

   - 按一下 ![螺絲起子](../media/screwdriver-icon.png) 圖示。

   ![產生比較運算子](media/generate-comparison-operators.png)

3. 從下拉式功能表中選取 [ **產生等於 (物件) ** ]。

## <a name="see-also"></a>另請參閱

- [程式碼產生](../code-generation-in-visual-studio.md)
- [預覽變更](../../ide/preview-changes.md)
