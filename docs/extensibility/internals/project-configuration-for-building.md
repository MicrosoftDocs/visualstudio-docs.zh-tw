---
title: 建築專案設定 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdd084053e06206a99298b234b4d51c8504119a2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706735"
---
# <a name="project-configuration-for-building"></a>建置的專案組態
給定解決方案的解決方案配置清單由「解決方案配置」對話方塊管理。

 用戶可以創建其他解決方案配置,每個配置都有自己的唯一名稱。 當使用者創建新的解決方案配置時,IDE 預設為專案中的相應配置名稱,如果不存在相應的名稱,則「調試」。。 如有必要,使用者可以更改所選內容以滿足特定要求。 此行為的唯一例外是專案支援與新解決方案配置名稱匹配的配置。 例如,假設解決方案包含 Project1 和 Project2。 Project1 具有專案配置調試、零售和 MyConfig1。 Project2 具有專案配置調試、零售和 MyConfig2。

 如果用戶創建了名為 MyConfig2 的新解決方案配置,Project1 預設情況下將其調試配置綁定到解決方案配置。 默認情況下,Project2 還將其 MyConfig2 配置綁定到解決方案配置。

> [!NOTE]
> 綁定不區分大小寫。

 當使用者在配置下拉清單中選擇 **「多個選擇**」項時,環境將顯示一個對話框,提供可用配置的清單。

 ![多種設定](../../extensibility/internals/media/vsmultiplecfgs.gif "vs 多倍Cfgs")多種設定

 在此對話框中,用戶可以選擇一個或多個配置。 選中後,屬性頁對話框中顯示的屬性值將反映所選配置的值的交集。

 有關新增與重命名解決方案和專案的設定的資訊,請參閱[解決方案設定](../../extensibility/internals/solution-configuration.md)。

 項目依賴項和生成順序與解決方案配置無關:也就是說,只能為解決方案中的所有專案設置一個依賴項樹。 右鍵單擊解決方案或項目並選擇專案**依賴項目**或 **「專案產生訂單」** 選項將打開 **「項目依賴項」** 對話方塊。 也可以從 **「專案」** 功能表打開它。

 ![項目相依項](../../extensibility/internals/media/vsprojdependencies.gif "vsProj 相依")項目相依項

 項目依賴項確定專案生成的順序。 使用對話方塊上的「生成訂單」選項卡查看解決方案中專案生成的確切順序,並使用「依賴項」選項卡修改生成順序。

> [!NOTE]
> 由於<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency><xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency>或介面指定的顯式依賴項,環境已添加清單中選中其複選框但顯示為變暗的項目,並且無法更改。 例如,將專案引用添加到另一[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]個專案會自動添加只能通過刪除引用刪除的生成依賴項。 無法選擇複選框清晰且顯示為變暗的項目,因為這樣做將創建依賴項迴圈(例如,Project1 將依賴於 Project2,Project2 將依賴於 Project1),這將阻止生成。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]生成過程包括使用單個 Build 命令調用的典型編譯和連結操作。 還可以支援另外兩個生成過程:從上一個生成中刪除所有輸出項的乾淨操作,以及確定配置中的輸出項是否已更改的最新檢查。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>物件返回相應的<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>(<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>從返回)來管理其生成過程。 要報告生成操作發生時的狀態,配置將<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>調用 ,環境與對生成狀態事件感興趣的任何其他物件實現的介面。

 生成配置設置后,可以使用 這些設置來確定它們是否可以在調試器的控制下運行。 支援調試的<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>配置實現。

 實現項目依賴項后,可以通過自動化模型以程式設計方式操作依賴項。 在自動化<xref:EnvDTE.SolutionBuild.BuildDependencies%2A>模型中調用。 沒有可用的 VSIP API 介面允許直接操作解決方案生成管理員配置及其屬性。

 此外,您可以在項目依賴項視窗中提供網格。 有關詳細資訊,請參閱[屬性顯示格線](../../extensibility/internals/properties-display-grid.md)。

## <a name="see-also"></a>另請參閱
- [管理組態選項](../../extensibility/internals/managing-configuration-options.md)
- [管理部署的專案組態](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)
