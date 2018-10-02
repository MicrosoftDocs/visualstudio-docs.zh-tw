---
title: 使用存放區檢視進行偵錯 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d0955cae279ece70498ce05584d6b17d6e254f89
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489073"
---
# <a name="debugging-by-using-the-store-viewer"></a>使用存放區檢視進行偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[使用存放區檢視進行偵錯](https://docs.microsoft.com/visualstudio/modeling/debugging-by-using-the-store-viewer)。  
  
使用儲存的檢視器 中，您可以檢查的狀態*儲存*供[!INCLUDE[dsl](../includes/dsl-md.md)]。 儲存的檢視器會顯示所有的網域模型項目處於為特定的存放區，以及項目屬性和項目之間的連結。  
  
## <a name="opening-store-viewer"></a>開啟存放區檢視器  
 如果您正在進行[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]實驗性組建，停止於中斷點的程式碼執行個體存放區包含模型資訊的位置。 然後，輸入下列命令中的，開啟存放區檢視**Immediate**視窗：  
  
```  
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);  
```  
  
> [!NOTE]
>  您必須取代`mystore`存放區執行個體的名稱。 此外，如果您的命名空間新增至您的程式碼時，您可以輸入命令來顯示存放區檢視，而不需要完整的命名空間：  
>   
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`  
>   
>  `…`  
>   
>  `StoreViewer.Show(mystore);`  
  
 `Show`方法有數個多載。 您可以指定存放區或分割區的執行個體做為參數。  
  
 或者，您可以放入存放區檢視顯示程式碼中的任何位置的程式碼行，您傳遞給參數`Show`方法是在範圍內。 下的一行程式碼會執行的內容存放區的快照集時，此動作就會顯示儲存的檢視器。  
  
### <a name="using-store-viewer"></a>使用存放區檢視  
 當存放區檢視器開啟時，則非強制回應的 Windows Form 視窗隨即出現，如下圖所示。  
  
 ![](../modeling/media/storeviewer2.png "storeviewer2")  
存放區檢視  
  
 存放區檢視有三個窗格︰ 左的窗格中，右上方窗格中和右下方的窗格。 左的窗格是樹狀檢視中的型別`DomainDataDirectory`存放區的成員。 如果您展開 [資料分割] 節點，然後按一下項目，則會在右上方窗格中顯示項目的屬性。 如果項目連結至其他項目，則會在右下方窗格中顯示的其他項目。 如果您按兩下右下方窗格中的項目，項目會在左窗格中反白顯示。  
  
## <a name="see-also"></a>另請參閱  
 [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)



