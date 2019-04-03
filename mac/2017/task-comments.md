---
title: 工作註解
description: 新增程式碼的工作註解
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 3caef73ba46afd8eaf90826540248cb2d5c4efef
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2019
ms.locfileid: "58568140"
---
# <a name="task-comments"></a>工作註解

撰寫程式碼時，標準做法是明確註解未完成或有問題的程式碼，或使用警告進行快速因應措施。 Visual Studio for Mac 所提供的預設訊號權杖是 TODO、HACK、FIXME 和 UNDONE。 個人化的權杖可在 [Visual Studio] > [喜好設定] > [環境] > [工作] 下定義，如下圖所示：

![工作清單喜好設定](media/source-editor-image10.png)

若要新增工作註解，請新增包含工作關鍵字的註解。 例如：

```csharp
//TODO: Finish this for all properties.
```

Visual Studio for Mac 透過在 [工作清單] 板中醒目提示這些標記來注意它們，而此板的顯示方式是巡覽至 [檢視] > [板] > [工作]：

![工作清單板](media/source-editor-image11.png)

## <a name="see-also"></a>另請參閱

- [使用工作清單 (Windows 上的 Visual Studio)](/visualstudio/ide/using-the-task-list)