---
title: 使用者的意見反應 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3462edb539822cd856cd7281566674b4ed0c4def
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499622"
---
# <a name="feedback-to-the-user"></a>使用者的意見反應
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[使用者的意見反應](https://docs.microsoft.com/visualstudio/extensibility/internals/feedback-to-the-user)。  
  
在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]整合式的開發環境 (IDE) 中，有關可用的功能以使用者的目前選取範圍和全域選取範圍內容為基礎的視覺化回饋。 下表列出可在不同的選取項目內容中的功能。  
  
|選取項目內容|可用的功能|  
|-----------------------|-----------------------------|  
|IDE|Global|  
|目前的產品集|特定的產品|  
|作用中的階層|特定階層類型|  
|作用中的階層項目|特定階層項目類型|  
|主動式文件|特定文件類型|  
|最上層的多重文件介面 (MDI) 視窗|特定視窗類型|  
|目前的選取項目內容|特定的選取項目內容|  
  
 如果您只會顯示使用者的需求和持續提供一致的選取項目與環境內容意見反應的功能，您就會減少在 IDE 中的複雜度。 每當在 IDE 中開啟視窗時，就會適用下列規則：  
  
-   視窗變更其選取項目內容，如果選取回應清楚指出在視窗中，並動態說明 視窗中，如果顯示，會更新以反映目前的內容。  
  
-   如果視窗變更全域選取範圍內容時，所有的特定內容功能表、 [作用中的階層] 視窗中和應用程式標題列會更新以反映目前的內容。  
  
-   視窗應該出現在目前的選取範圍的屬性**屬性**視窗並選擇性地顯示，如果**屬性頁** 對話方塊。  
  
-   如果視窗不會呈現屬性或變更全域選取範圍的內容，選取意見反應不應維持在視窗時就無法再使用中視窗在 IDE 中。  
  
-   所有文件特定工具視窗應該持續會反映在使用中文件。  
  
-   功能表、 工具列和應用程式標題列應該會反映最上層的多重文件介面 (MDI) 用戶端視窗。  
  
 例如，在開啟的 Visual Basic Web 應用程式專案內的 Web 表單的 [HTML] 檢視，而且使用者選取`<td>`標記，以下列方式提供意見反應：  
  
-   選取項目是使用中視窗所示，而且會反映在**屬性**視窗。  
  
-   文件特有**工具箱**會更新以反映目前的文件。  
  
-   **編輯器**工具列並**資料表**功能表會顯示與更新以反映 Web Form 視窗的標題列。  
  
-   使用中階層視窗中，通常是**方案總管**，和其標題列更新，以反映目前的內容與內容相關**專案**功能表命令現在會套用至使用中的 Web應用程式專案。  
  
## <a name="see-also"></a>另請參閱  
 [選取項目及在 IDE 中的貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [選取內容物件](../../extensibility/internals/selection-context-objects.md)   
 [階層和選取範圍](../../extensibility/internals/hierarchies-and-selection.md)

