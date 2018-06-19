---
title: 使用者的意見反應 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 629d12974a52bca30c0db96e838c5c731ae1abf7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129941"
---
# <a name="feedback-to-the-user"></a>意見反應給使用者
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 中，有關可用的功能根據使用者的目前選取範圍和全域選取範圍內容的視覺化回饋。 下表列出可在不同的選取項目內容中的功能。  
  
|選取項目內容|可用的功能|  
|-----------------------|-----------------------------|  
|IDE|Global|  
|目前的產品集|特定產品|  
|使用中的階層|特定階層類型|  
|使用中的階層項目|特定階層項目類型|  
|主動式文件|特定文件類型|  
|最上層的多重文件介面 (MDI) 視窗|特定的視窗類型|  
|目前的選取項目內容|選取內容特定|  
  
 如果您只會出現使用者需要和持續提供一致的選取項目與環境內容意見反應的功能，減少在 IDE 中的複雜度。 每當在 IDE 中開啟視窗時，就會適用下列規則：  
  
-   視窗會變更其選取項目內容，如果選取回應清楚顯示在視窗中，並動態說明 視窗中，如果顯示，會更新以反映目前的內容。  
  
-   如果視窗變更全域選取範圍內容時，所有與特定內容相關功能表、 作用中的階層視窗中和應用程式標題列會更新以反映目前的內容。  
  
-   視窗應該介面中目前選取項目的內容**屬性**視窗以及 （選擇性） 如果顯示，**屬性頁** 對話方塊。  
  
-   如果視窗不介面屬性或變更全域選取範圍內容中，選取回應不應維持視窗時就無法再使用中視窗在 IDE 中。  
  
-   所有特定文件的工具視窗應該會持續都反映使用中文件。  
  
-   功能表、 工具列和應用程式標題列應該會反映最上層的多重文件介面 (MDI) 用戶端視窗。  
  
 例如，在 Visual Basic Web 應用程式專案內的 Web 表單的 [HTML] 檢視會開啟，且使用者選取`<td>`標記，以下列方式提供意見反應：  
  
-   選取範圍的使用中視窗所示，而且反映在**屬性**視窗。  
  
-   特定文件**工具箱**會更新以反映目前的文件。  
  
-   **編輯器**工具列和**資料表**功能表會顯示並更新以反映 Web 表單視窗的標題列。  
  
-   使用中階層視窗中，通常是**方案總管 中**，和其標題列更新，以反映目前的內容和即時線上**專案**功能表命令現在會套用至使用中的 Web應用程式專案。  
  
## <a name="see-also"></a>另請參閱  
 [選取項目及在 IDE 中的貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [選擇內容物件](../../extensibility/internals/selection-context-objects.md)   
 [階層和選取範圍](../../extensibility/internals/hierarchies-and-selection.md)