---
title: 工作註解
description: 新增程式碼的工作註解
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: d88b74ab953f97e061f4be3befc227646006f38b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "67692317"
---
# <a name="task-comments"></a>工作註解

撰寫程式碼時，標準做法是明確註解未完成或有問題的程式碼，或使用警告進行快速因應措施。 Visual Studio for Mac 所提供的預設訊號權杖是 TODO、HACK、FIXME 和 UNDONE。 個人化的權杖可在 [Visual Studio] > [喜好設定] > [環境] > [工作]**** 下定義，如下圖所示：

![工作清單喜好設定](media/source-editor-image10.png)

若要新增工作註解，請新增包含工作關鍵字的註解。 例如：

```csharp
//TODO: Finish this for all properties.
```

Mac 的 Visual Studio 通過在**工作清單**墊中突出顯示這些標記來吸引人們對這些標記的注意，可以通過導航到**查看>板>任務**來顯示這些標記：

![工作清單板](media/source-editor-image11.png)

## <a name="see-also"></a>另請參閱

- [使用工作清單 (Windows 上的 Visual Studio)](/visualstudio/ide/using-the-task-list)