---
title: 工作註解
description: 新增程式碼的工作註解
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 02eacb312931d941b716ee65f91cd478eac8bb8a
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493526"
---
# <a name="task-comments"></a>工作註解

撰寫程式碼時，標準做法是明確註解未完成或有問題的程式碼，或使用警告進行快速因應措施。 Visual Studio for Mac 所提供的預設訊號權杖是 TODO、HACK、FIXME 和 UNDONE。 個人化的權杖可在 [Visual Studio] > [喜好設定] > [環境] > [工作] 下定義，如下圖所示：

![工作清單喜好設定](media/source-editor-image10.png)

若要新增工作註解，請新增包含工作關鍵字的註解。 例如：

```csharp
//TODO: Finish this for all properties.
```

Visual Studio for Mac 藉由在 [ **工作清單** ] 視窗中反白顯示這些標記來將其醒目提示，您可以使用 [ **視圖 >** 工作] 功能表來顯示這些標記：

![顯示單一 TODO 專案的 [工作清單] 視窗](media/source-editor-image11.png)

## <a name="see-also"></a>請參閱

- [使用工作清單 (Windows 上的 Visual Studio)](/visualstudio/ide/using-the-task-list)