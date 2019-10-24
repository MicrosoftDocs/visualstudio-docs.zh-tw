---
title: 管理部署的專案設定 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ffa661d8bf33219a3a2956cef3e456c9b5f1146
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726024"
---
# <a name="project-configuration-for-managing-deployment"></a>管理部署的專案組態
部署是指將輸出專案從組建進程實際移到預期的位置以進行偵錯工具和安裝的動作。 例如，Web 應用程式可能會建立在本機電腦上，然後放在伺服器上。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支援兩種可在部署中牽涉到專案的方式：

- 作為部署程式的主旨。

- 作為部署程式的主管。

  在部署方案之前，您必須先加入部署專案來設定部署選項。 如果部署專案不存在，當您從 [**建立**] 功能表選取 [**部署方案**] 或以滑鼠右鍵按一下方案時，系統會詢問您是否要建立一個。 按一下 [**是]** 會開啟 [**加入新的專案**] 對話方塊，並選取 [**遠端部署嚮導]** 專案。

  遠端部署嚮導會要求您提供應用程式類型（Windows 或 Web）、要包含的專案輸出群組、您想要包含的任何其他檔案，以及您要部署到的遠端電腦。 Wizard 的最後一頁會顯示所選選項的摘要。

  屬於部署程式主旨的專案會產生必須移至替代環境的輸出專案。 這些輸出專案會描述為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 介面的參數，如果要允許專案群組輸出，其主要用途為。 如需 `IVsProjectCfg2` 的執行相關詳細資訊，請參閱[輸出的專案](../../extensibility/internals/project-configuration-for-output.md)設定。

  部署專案（管理部署程式）：選取此命令時，啟用 [部署] 命令並回應。 部署專案會實作為執行部署的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 介面，並呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> 介面來報告部署狀態事件。

  設定可以指定影響其組建或部署作業的相依性。 組建或部署相依性是必須在建立或部署設定本身之前或之後建立或部署的專案。 專案之間的組建相依性會與 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> 介面一併描述，並使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> 介面部署相依性。 如需詳細資訊，請參閱[建立的專案](../../extensibility/internals/project-configuration-for-building.md)設定。

## <a name="see-also"></a>請參閱
- [管理組態選項](../../extensibility/internals/managing-configuration-options.md)
- [建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)
- [輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)