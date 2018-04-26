---
title: VS Shell 部署
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e7df1991832e954def71a6cee5bd5516dfd4e961
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="vs-shell-deployment"></a>VS Shell 部署

獨立的 shell 可讓您判斷哪些 Visual Studio 需要與特定領域語言，和該方案的顯示方式互動功能。 如需 Visual Studio isolated shell 的詳細資訊，請參閱[自訂 Isolated Shell](../extensibility/customizing-the-isolated-shell.md)。

## <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>若要設定在 Visual Studio shell 之上，做為部署目標

1.  在**DslPackage**專案中，開啟**source.extension.tt**。

2.  在下`<SupportedProducts>`插入：

    ```
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     取代*MyIsolatedShell*獨立的 shell 封裝的名稱。