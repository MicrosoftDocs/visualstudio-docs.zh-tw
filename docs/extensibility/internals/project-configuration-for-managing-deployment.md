---
title: 管理部署的項目設定 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62f7bf6535a89e46799ade88fe8976974b3019c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706703"
---
# <a name="project-configuration-for-managing-deployment"></a>管理部署的專案組態
部署是物理將輸出項從生成過程移動到用於調試和安裝的預期位置的行為。 例如,Web 應用程式可能構建在本地電腦上,然後放置在伺服器上。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援項目參與部署的兩種方式:

- 作為部署過程的主題。

- 作為部署過程的經理。

  在部署解決方案之前,必須首先添加部署專案以配置部署選項。 如果部署專案不存在,當您從 **「生成**」功能表中選擇 **「部署解決方案」** 或右鍵單擊解決方案時,系統會詢問您是否要創建一個部署專案。 按下 **「是**」將打開「**新增新項目**」對話框,並選擇 **「遠端部署精靈」** 專案。

  遠端部署精靈要求您提供應用程式類型(Windows或 Web)、要包括的專案輸出組、要包括的任何其他檔以及要部署到的遠端電腦。 嚮導的最後一頁顯示所選選項的摘要。

  作為部署過程主題的專案將生成必須移動到備用環境的輸出項。 這些輸出項被描述為介面的<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>參數,如果允許專案對輸出進行分組,則介面的主要目的是這些參數。 有關`IVsProjectCfg2`實作的詳細資訊,請參考[輸出的項目設定](../../extensibility/internals/project-configuration-for-output.md)。

  管理部署過程的部署專案啟用"部署"命令並在選擇此命令時回應。 部署項目實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>該介面以執行部署,並調<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback>用 該介面以報告部署狀態事件。

  配置可以指定影響其生成或部署操作的依賴項。 生成或部署依賴項是必須在構建或部署配置之前或之後生成或部署的專案。 使用介面描述項目之間的生成依賴關係,<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency>並部署<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>使用介面的依賴項。 有關詳細資訊,請參閱[用於建構的項目設定](../../extensibility/internals/project-configuration-for-building.md)。

## <a name="see-also"></a>另請參閱
- [管理組態選項](../../extensibility/internals/managing-configuration-options.md)
- [建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)
- [輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)
