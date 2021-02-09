---
title: 管理部署的專案設定 |Microsoft Docs
description: 瞭解如何部署到預期的偵測和安裝位置，以及兩種 Visual Studio 支援支援部署之專案的方式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ebdc1dc529e73e17ba55a0b4766f11dced4addcb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893642"
---
# <a name="project-configuration-for-managing-deployment"></a>管理部署的專案組態
部署是指將輸出專案從組建進程實際移至預期位置以進行偵錯工具的動作。 例如，Web 應用程式可能會建立在本機電腦上，然後放在伺服器上。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 支援兩種可在部署中牽涉到專案的方式：

- 作為部署程式的主體。

- 作為部署流程的管理員。

  在部署方案之前，您必須先新增部署專案來設定部署選項。 如果部署專案不存在，系統會詢問您是否要在選取 [**組建**] 功能表中的 [**部署方案**] 或以滑鼠右鍵按一下方案時建立一個專案。 按一下 [ **是]** 會開啟 [ **加入新的專案** ] 對話方塊，並選取 [ **遠端部署嚮導]** 專案。

  遠端部署嚮導會要求您輸入應用程式的類型 (Windows 或 Web) 、要包含的專案輸出群組、要包含的任何其他檔案，以及您想要部署的遠端電腦。 Wizard 的最後一頁會顯示所選選項的摘要。

  屬於部署程式主體的專案會產生必須移至替代環境的輸出專案。 這些輸出專案會描述為介面的參數 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> ，如果允許專案將輸出分組，其主要目的為。 如需與的執行相關的詳細資訊 `IVsProjectCfg2` ，請參閱 [輸出的專案](../../extensibility/internals/project-configuration-for-output.md)設定。

  管理部署程式的部署專案，啟用 [部署] 命令，並在選取此命令時回應。 部署專案會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 執行介面，以執行部署並對介面進行呼叫， <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> 以報告部署狀態事件。

  設定可以指定影響其組建或部署作業的相依性。 組建或部署相依性是必須在建立或部署設定本身之前或之後建立或部署的專案。 專案之間的組建相依性會使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> 介面來描述，並部署與介面的相依性 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> 。 如需詳細資訊，請參閱 [建立的專案](../../extensibility/internals/project-configuration-for-building.md)設定。

## <a name="see-also"></a>另請參閱
- [管理組態選項](../../extensibility/internals/managing-configuration-options.md)
- [建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)
- [輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)
