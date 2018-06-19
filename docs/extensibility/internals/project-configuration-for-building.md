---
title: 專案建置組態 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 4d78ac1cabc356db162639d3eb19d0bff71e295e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133298"
---
# <a name="project-configuration-for-building"></a>建置專案組態
給定方案的方案組態的清單是由方案組態 對話方塊來管理。  
  
 使用者可以建立額外的方案組態，各有其唯一名稱。 當使用者建立新的方案組態時，IDE 會預設為對應的組態名稱，在偵錯的專案中，如果沒有對應的名稱存在。 使用者可以變更以符合特定需求，視選取項目。 唯一的例外狀況，這個問題發生時，專案支援的設定，以符合新的方案組態的名稱。 例如，假設解決方案包含 Project1 和 Project2。 Project1 有偵錯、 零售版和 MyConfig1 專案組態。 Project2 有偵錯、 零售版和 MyConfig2 專案組態。  
  
 如果使用者建立新的方案組態，名為 MyConfig2，Project1 預設繫結其偵錯組態的方案組態。 Project2 也預設繫結其 MyConfig2 組態的方案組態。  
  
> [!NOTE]
>  繫結是不區分大小寫。  
  
 當使用者選取**多重選取**項目在 [組態] 下拉式清單中，環境會顯示一個對話方塊，提供的可用設定清單方塊。  
  
 ![多個組態](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
多個組態  
  
 在此對話方塊，使用者可以選取一或多個組態。 一旦選取，顯示在 [屬性頁] 對話方塊上的屬性值會反映選取的組態值的交集。  
  
 請參閱[方案組態](../../extensibility/internals/solution-configuration.md)的新增和重新命名方案和專案組態的相關資訊。  
  
 專案相依性和建置順序是獨立的方案組態： 也就是您可以只設定所有方案中專案的一種相依性樹狀結構。 以滑鼠右鍵按一下方案或專案，然後選取 [**專案相依性**或**專案建置順序**選項會開啟**專案相依性**] 對話方塊。 您也可以開啟從**專案**功能表。  
  
 ![專案相依性](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
專案相依性  
  
 專案相依性會決定的順序建置專案。 使用對話方塊上的建置順序 索引標籤，以檢視方案中的專案建置及修改的建置順序使用 相依性 索引標籤的正確順序。  
  
> [!NOTE]
>  已經由的環境，因為所指定明確的相依性加入專案清單中的選取其核取方塊，但會呈現暗灰色<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>介面，而且無法變更。 例如，將專案參考從[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]至另一個專案的專案會自動將只會移除刪除參考的組建相依性。 無法選取其核取方塊已清除，而且會呈現暗灰色的專案，因為這樣會建立相依性迴圈 （例如 Project1 會相依於 Project2，並會相依於 Project1 Project2），這會停止組建。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 建置程序包括一般的編譯和連結作業，使用單一的建置命令叫用。 也可支援兩個其他建置處理序： 若要刪除所有輸出項目從某一個組建和最新的檢查，以判斷是否已變更組態中的輸出項目清除作業。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 物件會傳回對應<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>(從傳回<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) 來管理其建置程序。 若要報告建立作業的狀態，進行時，組態進行呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>、 由環境實作的介面和任何其他物件感興趣的組建狀態事件。  
  
 一旦建立之後，組態設定可用來判斷可以執行控制的偵錯工具。 設定實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>支援偵錯。  
  
 在實作之後的專案相依性，您可以透過程式設計方式操作透過 automation 模型的相依性。 您呼叫<xref:EnvDTE.SolutionBuild.BuildDependencies%2A>automation 模型中。 沒有任何可用的 VSIP API 層級介面允許直接操作方案建置 manager 組態和其屬性。  
  
 此外，您可以提供的方格中的專案相依性的視窗。 如需詳細資訊，請參閱[屬性顯示格線](../../extensibility/internals/properties-display-grid.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管理組態選項](../../extensibility/internals/managing-configuration-options.md)   
 [管理部署的專案組態](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)