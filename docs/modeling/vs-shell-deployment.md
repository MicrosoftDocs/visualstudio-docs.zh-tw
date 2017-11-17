---
title: "VS Shell 部署 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: e7632b99d3fa9d347b5a259cd446edc2f6d9efa8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
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