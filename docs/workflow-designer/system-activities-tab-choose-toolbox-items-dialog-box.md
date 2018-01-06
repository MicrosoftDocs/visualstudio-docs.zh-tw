---
title: "系統活動索引標籤中，選擇工具箱項目對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: ba4078a903c1e30b968928e13c8d160c898bbf0d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>系統活動索引標籤，選擇工具箱項目對話方塊
此索引標籤的**選擇工具箱項目**對話方塊會顯示一份[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]活動、 範本和項目可供您使用。 若要顯示這份清單，請選取**選擇工具箱項目**從**工具**功能表或以滑鼠右鍵按一下**工具箱**，然後選取**選擇的項目**顯示**選擇工具箱項目**對話方塊，然後選取其**System.Activities**  索引標籤。根據預設，此清單包含 System.Activities、 System.ServiceModel.Activities 及 System.Activities.Core.Presentation 組件; 的工作流程活動不過，只有系統提供所顯示的活動和活動中顯示其他組件透過新增**工具箱**依預設都會被勾選。 新加入的活動會自動核取和會出現在**工具箱**當您按一下**確定**在對話方塊中。 此外，這些項目會出現在**工具箱**下對應到活動/項目/範本所在的命名空間的新類別。  
  
> [!WARNING]
>  如果嘗試加入的組件並未包含任何工作流程活動，就會顯示錯誤對話方塊，說明該組件沒有包含任何活動。  
  
 這個對話方塊不受專案影響，因此**System.Activities**索引標籤會繼續顯示在獨立 XAML 或非工作流程專案型別。  
  
 篩選會在各個索引標籤上進行。這表示您不可以透過工作流程活動，將新增**.NET 元件** 索引標籤。他們必須透過新增**System.Activities**  索引標籤本身。  
  
 您可以取消核取不想要在中查看任何項的目**工具箱**從這個對話方塊索引標籤上，或者，您可以執行使用**刪除**中的內容功能表選項**工具箱**和取消參考的組件不會移除的項目從**工具箱**。  
  
 利用拖放到設計工具的方式為活動建立執行個體，就會自動將包含該項目的組件加入至參考組件清單。 此外，如果活動參考某個組件 C，並不會將 C 加入至參考組件清單。 組件 C 必須位於 GAC 或相同的目錄與活動 b在獨立的情況下，組件必須在 GAC 中，或是在 VS 的 Probe 路徑中。 唯有如此，才可在工作流程設計工具介面上拖放活動。  
  
 **工具箱**儲存為使用者選項的預設設定，下一次，當您開啟**工具箱**，它會顯示您自訂工作流程活動的清單。 一個副作用是，如果您加入特定網域項目**工具箱**透過**選擇工具箱項目**對話方塊中，您還是繼續看到這些項目，當您使用工作流程主控台應用程式。 如果您不想看到它們，然後使用內容功能表加以刪除或取消核取透過**選擇工具箱項目**對話方塊中，如先前所述。  
  
 這個對話方塊的資料行包含了下列資訊：  
  
 名稱  
 列出目前已登錄在您本機電腦上的工作流程活動名稱。  
  
 命名空間  
 顯示 .NET Framework 類別程式庫命名空間的階層架構，這個命名空間定義了活動的結構。  
  
 組件名稱  
 顯示包含該活動之 .NET Framework 組件的名稱與版本。  
  
 Directory  
 顯示包含這些工作流程活動之 .NET Framework 組件的位置。 所有組件的預設位置為 [全域組件快取]。  
  
 若要排序上列元件，請選取任一資料行標題。