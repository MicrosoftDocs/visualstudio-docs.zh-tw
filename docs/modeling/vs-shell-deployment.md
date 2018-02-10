---
title: "VS Shell 部署 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: eb5446c8c3090624f327c234a1b518dc1928b6c9
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
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