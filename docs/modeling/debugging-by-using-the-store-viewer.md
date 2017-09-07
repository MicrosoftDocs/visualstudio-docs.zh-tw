---
title: "使用存放區檢視偵錯 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 17
author: alancameronwills
ms.author: awills
manager: douge
ms.translationtype: MT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 6fde5dfc012b43d71f6d8db2519607724eeeadc9
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# <a name="debugging-by-using-the-store-viewer"></a>使用存放區檢視進行偵錯
以儲存檢視器中，您可以檢查的狀態*儲存*供[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]。 儲存的檢視器會顯示所有的網域模型項目在特定的存放區，以及項目屬性和項目之間的連結。  
  
## <a name="opening-store-viewer"></a>開啟存放區檢視器  
 如果您正在進行[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]實驗組建，停止於中斷點的程式碼執行個體存放區的位置包含模型資訊。 然後，輸入下列命令中的，開啟存放區檢視器**即時運算**視窗：  
  
```  
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);  
```  
  
> [!NOTE]
>  您必須取代`mystore`存放區執行個體的名稱。 此外，如果您將命名空間加入您的程式碼時，您可以輸入不完整的命名空間的情況下顯示存放區檢視器的命令：  
>   
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`  
>   
>  `...`  
>   
>  `StoreViewer.Show(mystore);`  
  
 `Show`方法有數個多載。 您可以指定存放區或資料分割的執行個體做為參數。  
  
 或者，您可以將存放區檢視器顯示程式碼中的任何位置的程式碼行所在的參數，您將傳遞至`Show`方法是在範圍內。 此動作的一行程式碼執行以內容存放區的快照集時，會顯示儲存的檢視器。  
  
### <a name="using-store-viewer"></a>使用存放區檢視器  
 存放區檢視器開啟時，則非強制回應的 Windows Form 視窗隨即出現，如下圖所示。  
  
 ![](../modeling/media/storeviewer2.png "storeviewer2")  
存放區檢視器  
  
 存放區檢視器有三個窗格： 左邊的窗格、 右上方窗格中和右下方的窗格。 左的窗格是樹狀檢視中的型別`DomainDataDirectory`存放區的成員。 如果您展開 [資料分割] 節點，然後按一下項目，項目的屬性會出現在右上方窗格中。 如果項目連結到其他項目，其他項目會出現在右下方窗格中。 如果您按兩下右下方窗格中的項目，項目會在左窗格中反白顯示。  
  
## <a name="see-also"></a>另請參閱  
 [巡覽及更新程式碼中的模型](../modeling/navigating-and-updating-a-model-in-program-code.md)
