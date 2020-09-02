---
title: 透過 IntelliSense 功能表的 DateTime 和 TimeSpan 完成
ms.date: 07/31/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 36b6d5440e532653845638f87f7f1d7066af6ba3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "87471546"
---
# <a name="datetime-and-timespan-completion-through-intellisense-menu"></a>透過 IntelliSense 功能表的 DateTime 和 TimeSpan 完成

此重構適用於：

- C#

事項 **：** DateTime 和 TimeSpan 字串常值，以及透過 IntelliSense 功能表完成的格式字串。

時機 **：** 您想要撰寫 DateTime 和 TimeSpan 字串常值和格式字串。 IntelliSense 提供基本的完成功能，以及每個字元意義的說明。 

**原因：** 記住 DateTime 格式是很困難的，且 IntelliSense 可協助您撰寫。

## <a name="how-to"></a>操作方式

1. 將游標放在 DateTime 或 TimeSpan 格式字串中。
2. 按**Ctrl** + **空格鍵**以觸發 [ **IntelliSense** ] 功能表。
3. 選取您要新增的字元。

   ![DateTime 完成 IntelliSense](media/datetime-completion.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
