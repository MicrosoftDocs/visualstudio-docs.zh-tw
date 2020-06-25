---
title: 一般字串和逐字字串常值之間的轉換
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 7e8e239f53f92727072a2fcd6573d6957b7cd3ec
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290157"
---
# <a name="convert-between-regular-string-and-verbatim-string-literals-refactoring"></a>一般字串和逐字字串常值重構之間的轉換

此重構適用於：

- C#

**功能：** 可讓您在一般字串和逐字字串常值之間進行轉換。

時機 **：** 您想要節省空間，或在您的程式碼中提供更清楚的資訊。

**原因：** 將逐字字串常值轉換成一般字串常值，有助於節省空間。 將一般字串常值轉換成逐字字串常值，可提供更清楚的資訊。

## <a name="how-to"></a>操作方式

1. 將插入號放在一般字串或逐字字串常值上：

2. 按**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。

3. 選取下列其中一個選項： 

    選取 [Convert to regular string] \(轉換為一般字串\)。

    ![轉換成一般字串](media/convert-to-regular-string.png)

    選取 [Convert to verbatim string] \(轉換為逐字字串\)。

    ![轉換成逐字字串](media/convert-to-verbatim-string.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)