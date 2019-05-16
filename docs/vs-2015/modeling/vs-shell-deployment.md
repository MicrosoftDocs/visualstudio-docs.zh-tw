---
title: VS Shell 部署 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5bfe88d7e7d742eb67273d307c3a8e72e9a85833
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704040"
---
# <a name="vs-shell-deployment"></a>VS Shell 部署
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

獨立模式的 shell 可讓您判斷哪一個 Visual Studio 需要特定領域語言，和如何呈現該解決方案互動的功能。 如需 Visual Studio 隔離 shell 的詳細資訊，請參閱[自訂 Isolated Shell](../extensibility/customizing-the-isolated-shell.md)。 您可以找到有關如何自訂 isolated 的 shell 中的詳細資訊[自訂 Isolated Shell](https://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf)。  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>若要設定做為部署目標的 Visual Studio Shell  
  
1. 在  **DslPackage**專案中，開啟**source.extension.tt**。  
  
2. 在下`<SupportedProducts>`插入：  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     取代*MyIsolatedShell*獨立模式的 shell 封裝的名稱。
