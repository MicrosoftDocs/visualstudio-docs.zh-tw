---
title: 在工作流程設計工具中的錯誤訊息 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: efd6bc680be42f1074da8d2313b1a4b8e9307580
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894842"
---
# <a name="error-messages-in-workflow-designer"></a>工作流程設計工具的錯誤訊息
本主題描述處理 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 時可能遇到的錯誤訊息類型。  
  
## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>在工作流程設計工具中發生錯誤的情況  
 在下列情況中，[!INCLUDE[wfd2](../includes/wfd2-md.md)] 中會發生錯誤：  
  
1. 此為運算式中的錯誤。  
  
2. 未滿足活動的驗證條件約束。  
  
3. XAML 檔中發生導致活動無法載入的錯誤。  
  
4. XAML 檔中發生導致工作流程無法載入的錯誤。  
  
   無效的運算式與不滿足驗證條件限制並不會造成工作流程建置失敗。 工作流程會成功建置，但是在執行階段擲回 <xref:System.Activities.InvalidWorkflowException>。 如果 XAML 中有錯誤，建置就會失敗。  
  
   內部[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，當工作流程載入時，其錯誤會顯示在**錯誤清單**。 若要瀏覽至錯誤的來源活動，按兩下 [] 中的錯誤**錯誤清單**。  
  
### <a name="expression-errors"></a>運算式錯誤  
 如果有無效的運算式，則會在運算式旁出現內含白色驚嘆號的紅色圓圈來標註。 將游標移至這個圖示上方，隨即出現描述錯誤來源的工具提示。 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 內，請按一下運算式來檢視在錯誤來源底下的行。 將游標移至這行文字上方，隨即出現描述錯誤來源的工具提示。  
  
### <a name="activity-validation-errors"></a>活動驗證錯誤  
 當未滿足活動的驗證條件限制時，活動的右上角會出現內含白色驚嘆號的紅色圓圈。 將游標移至這個圖示上方，隨即出現描述錯誤來源的工具提示。  
  
### <a name="xaml-load-errors"></a>XAML 載入錯誤  
 活動無法載入時，會出現包含「XAML 中發生錯誤，因此無法載入活動」文字的紅色方塊。 通常當活動型別無法解析時，就會發生這個錯誤。 選取紅色方塊並加以刪除，以刪除設計工具中無效的活動。  
  
### <a name="workflow-load-errors"></a>工作流程載入錯誤  
 當工作流程無法載入時，設計工具設計介面上會出現「工作流程設計工具在處理您的文件時發生問題」文字，並附上造成工作流程無法載入的例外狀況資訊。 通常當無法剖析 XAML 檔時，就會發生這個錯誤。