---
title: "管理部署的專案組態 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 87098c362e5b37690e2ab3116ffca431d58f129d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="project-configuration-for-managing-deployment"></a>管理部署的專案組態
部署是指實際建置程序從輸出項目移至期望位置進行偵錯和安裝。 例如，Web 應用程式可能會在本機電腦上建置，並將其放在伺服器上。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援兩種方式可以在部署中牽涉到專案：  
  
-   為部署程序主題。  
  
-   與部署程序管理員。  
  
 可以部署方案之前，您必須先將設定部署選項部署專案。 如果部署專案不存在，您會問您是否選取時，請建立一個**部署方案**從**建置**功能表或以滑鼠右鍵按一下方案。 按一下**是**開啟**加入新的專案**對話方塊**遠端部署精靈**選取專案。  
  
 遠端部署精靈會要求您的應用程式 （Windows 或 Web） 的類型、 要包含的專案輸出群組、 您想要包括的任何其他檔案和您要部署到遠端電腦。 在精靈的最後一頁會顯示選取之選項的摘要。  
  
 主旨的部署程序的專案會產生必須移至其他環境的輸出項目。 這些輸出項目描述做為參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>介面，其主要用途是否允許群組輸出的專案。 如需詳細資訊與相關的實作`IVsProjectCfg2`，請參閱[專案組態輸出](../../extensibility/internals/project-configuration-for-output.md)。  
  
 部署專案，其管理的部署程序，啟用 [部署] 命令，並選取這個命令時回應。 部署專案實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>介面來執行這種部署，並呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback>介面，以報告部署狀態事件。  
  
 設定可以指定會影響其組建或部署作業的相依性。 建置或部署的相依性都必須為內建或部署之前或之後建立本身的組態或部署的專案。 建置專案之間的相依性的說明<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency>介面，並部署相依性與<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>介面。 如需詳細資訊，請參閱[建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管理組態選項](../../extensibility/internals/managing-configuration-options.md)   
 [建置專案組態](../../extensibility/internals/project-configuration-for-building.md)   
 [輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)