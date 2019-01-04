---
title: 管理部署的專案組態 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 02b7f04afc666fb842414c8a46793eb3178fe404
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852582"
---
# <a name="project-configuration-for-managing-deployment"></a>管理部署的專案組態
部署是指實際將從建置程序的輸出項目移至 偵錯和安裝的預期位置。 比方說，Web 應用程式可能會在本機電腦上建置，然後放在伺服器上。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支援兩種方式可以在部署中牽涉到專案：  
  
- 部署程序的主體。  
  
- 為部署程序管理員。  
  
  在部署解決方案之前，您必須先新增部署專案來設定部署選項。 如果部署專案不存在，系統會詢問您要建立一個，當您選取**部署的解決方案**從**建置**功能表或以滑鼠右鍵按一下方案。 按一下 **[是]** 便會開啟**加入新的專案**對話方塊，其中包含**遠端部署精靈**選取專案。  
  
  遠端部署精靈會要求您的應用程式 （Windows 或 Web） 的類型、 要包含的專案輸出群組、 您想要包括的任何其他檔案和您想要部署到遠端電腦。 在精靈的最後一頁會顯示所選選項的摘要。  
  
  對象的部署程序的專案會產生必須移至其他環境的輸出項目。 這些輸出項目會被稱為參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>介面，其主要用途，讓專案輸出群組的 if。 如需詳細資訊與相關的實作`IVsProjectCfg2`，請參閱 <<c2> [ 輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)。  
  
  部署專案，管理在部署程序，啟用 部署 命令，並回應時選取此命令時。 部署專案實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>介面來執行部署，並對進行呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback>介面來報告部署狀態事件。  
  
  設定可以指定會影響其組建或部署作業的相依性。 建置或部署的相依性都必須是內建或部署之前或之後設定本身是建置或部署的專案。 說明專案之間的組建相依性<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency>介面，並部署與相依性<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>介面。 如需詳細資訊，請參閱 <<c0> [ 建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管理組態選項](../../extensibility/internals/managing-configuration-options.md)   
 [建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)   
 [輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)