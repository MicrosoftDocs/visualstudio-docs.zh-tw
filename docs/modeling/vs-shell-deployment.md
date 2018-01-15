---
title: "VS Shell 部署 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cbd972609f06f9ce7d3a7745b33b8d0d78dcad2e
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="vs-shell-deployment"></a>VS Shell 部署
獨立的 shell 可讓您判斷哪些 Visual Studio 需要與特定領域語言，和該方案的顯示方式互動功能。 如需 Visual Studio isolated shell 的詳細資訊，請參閱[自訂 Isolated Shell](../extensibility/customizing-the-isolated-shell.md)。 您可以找到有關如何自訂在 isolated 的 shell 中的詳細資訊[自訂 Isolated Shell](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf)。  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>若要設定在 Visual Studio shell 之上，做為部署目標  
  
1.  在**DslPackage**專案中，開啟**source.extension.tt**。  
  
2.  在下`<SupportedProducts>`插入：  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     取代*MyIsolatedShell*獨立的 shell 封裝的名稱。