---
title: 專案建置的組態 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f320a23fa75dccdb4c273bc851832f3b762696d1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910213"
---
# <a name="project-configuration-for-building"></a>建置的專案組態
給定方案的方案組態的清單是由 [方案組態] 對話方塊中管理。  
  
 使用者可以建立額外的方案組態，各有自己唯一的名稱。 當使用者建立新的方案組態時，IDE 會預設為對應的組態名稱，在偵錯的專案中，如果不有任何對應的名稱。 使用者可以變更選取項目，以符合特定需求，如有必要。 唯一的例外狀況，此行為時，專案支援的組態，以符合新的方案組態的名稱。 例如，假設解決方案包含 Project1 和 Project2。 Project1 有偵錯、 零售版和 MyConfig1 的專案組態。 Project2 有偵錯、 零售版和 MyConfig2 的專案組態。  
  
 如果使用者建立新的方案組態，名為 MyConfig2，Project1 預設繫結其偵錯組態的方案組態。 Project2 也預設會繫結其 MyConfig2 組態的方案組態。  
  
> [!NOTE]
>  繫結是不區分大小寫。  
  
 當使用者選取**多重選取**項目在 [組態] 下拉式清單中，環境會顯示對話方塊，來提供可用的組態清單。  
  
 ![多個組態](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
多個組態  
  
 在此對話方塊中，使用者可以選取一或多個組態。 選取之後，顯示在 [屬性頁] 對話方塊上的屬性值會反映選取的組態值的交集。  
  
 請參閱[方案組態](../../extensibility/internals/solution-configuration.md)與新增和重新命名方案和專案的組態相關資訊。  
  
 專案相依性和建置順序是獨立的解決方案組態： 也就是您只能設定一個依存性方案中專案的所有的樹狀目錄。 以滑鼠右鍵按一下方案或專案，然後選取**專案相依性**或**專案建置順序**選項會開啟**專案相依性** 對話方塊。 您也可以開啟從**專案**功能表。  
  
 ![專案相依性](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
專案相依性  
  
 專案相依性會決定專案建置的順序。 使用對話方塊上的建置順序 索引標籤，來檢視專案的方案中建置及修改的建置順序使用 相依性 索引標籤的正確順序。  
  
> [!NOTE]
>  由於明確的相依性所指定的環境已新增專案清單中的選取其核取方塊，但呈現暗灰色<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>介面，而且無法變更。 例如，將專案參考從[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]到另一個專案的專案會自動將會移除它必須刪除參考的組建相依性。 無法選取其核取方塊已清除，而且會呈現暗灰色的專案，因為這樣會建立相依性迴圈 （比方說，會相依於 Project2 Project1 和 Project2 會相依於 Project1），這會停止組建。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 建置程序包含一般的編譯和連結作業使用單一組建命令叫用。 也可支援兩個其他組建程序： 若要刪除所有輸出項目從某一個組建和最新的檢查，以判斷是否有變更輸出中的項目設定的清除作業。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 物件會傳回相對應<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>(從傳回<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) 來管理其組建程序。 若要報告建立作業的狀態，它發生時，設定發出呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>、 環境所實作的介面，以及任何其他物件有興趣建置狀態事件。  
  
 建置後，組態設定可用來判斷可以執行偵錯工具的控制之下。 設定實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>以支援偵錯。  
  
 在實作之後的專案相依性，您可以以程式設計方式處理透過 automation 模型的相依性。 您呼叫<xref:EnvDTE.SolutionBuild.BuildDependencies%2A>automation 模型中。 沒有任何可用的 VSIP API 層級介面允許直接操作方案建置 manager 組態和其屬性。  
  
 此外，您可以提供 [專案相依性] 視窗中的方格。 如需詳細資訊，請參閱 <<c0> [ 屬性顯示格線](../../extensibility/internals/properties-display-grid.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管理組態選項](../../extensibility/internals/managing-configuration-options.md)   
 [管理部署的專案組態](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)