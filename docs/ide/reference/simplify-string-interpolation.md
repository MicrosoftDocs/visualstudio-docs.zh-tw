---
title: 簡化字串插補
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
ms.openlocfilehash: 5e801d417280d5d9ce8225c2185b582544fe2cef
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810333"
---
# <a name="simplify-string-interpolation-refactoring"></a>簡化字串插補重構

此重構適用於：

- C#

- Visual Basic

事項 **：** 可讓您簡化[字串插補](/dotnet/csharp/tutorials/string-interpolation)。

時機 **：** 您有可簡化的字串插補。

**原因：** 簡化字串插補可提供更清楚且更簡潔的語法。 此重構工具將會自動執行工作，而不需要手動執行。

## <a name="how-to"></a>使用方法

1. 將插入號放在字串插補上：

2. 按下**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。

3. 選取 **簡化插補**

    ![簡化字串插補](media/simplify-string-interpolation.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)