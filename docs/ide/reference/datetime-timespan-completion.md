---
title: 透過 IntelliSense 功能表進行日期時間和 TimeSpan 完成
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: eaa8a344e46c031b37b52106ba9aef25dac59b0c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290159"
---
# <a name="datetime-and-timespan-completion-through-intellisense-menu"></a>透過 IntelliSense 功能表進行日期時間和 TimeSpan 完成

此重構適用於：

- C#

**功能：** 透過 IntelliSense 功能表進行日期時間和 TimeSpan 字串常值的完成。

時機 **：** 您想要寫入 DateTime 和 TimeSpan 字串常值。 IntelliSense 提供您基本的完成，並說明每個字元的意義。 

**原因：** 記住 DateTime 格式很困難，而且 IntelliSense 可以協助您撰寫它。

## <a name="how-to"></a>操作方式

1. 將游標放在 DateTime 或 TimeSpan 字串常值中。
2. 按**Ctrl** + **空格鍵**以觸發 [ **IntelliSense** ] 功能表。
3. 選取您想要新增的字元。

   ![DateTime 完成 IntelliSense](media/datetime-completion.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
