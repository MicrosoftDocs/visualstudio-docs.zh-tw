---
title: 簡化字串插補
ms.date: 02/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 15f034b0ecf46e19681f3b74e4137a2de9e9d950
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2020
ms.locfileid: "77280751"
---
# <a name="simplify-string-interpolation-refactoring"></a>簡化字串插補重構

此重構適用於：

- C#

**功能：** 可讓您簡化[字串插補](https://docs.microsoft.com/dotnet/csharp/tutorials/string-interpolation)。

時機 **：** 您有可以簡化的字串插補。

**原因：** 簡化字串插補可提供更清楚易懂且更簡潔的語法。 這個重構工具會自動執行工作，而不需要手動執行。

## <a name="how-to"></a>操作方式

1. 將插入號放在字串插補上：

2. 在字行任何地方按 **Ctrl**+ **.** ， 以觸發 [快速動作與重構] 功能表。

3. 選取**簡化插補**

    ![簡化字串插補](media/simplify-string-interpolation.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)