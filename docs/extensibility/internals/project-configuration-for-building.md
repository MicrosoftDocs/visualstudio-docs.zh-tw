---
title: 組建的專案設定 |Microsoft Docs
description: 瞭解特定方案的解決方案設定清單如何由新專案類型中的 [方案設定] 對話方塊管理。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b817607f765626a6b63693e681306309512fdb7d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074440"
---
# <a name="project-configuration-for-building"></a>建置的專案組態
給定解決方案的解決方案設定清單是由 [方案設定] 對話方塊所管理。

 使用者可以建立額外的解決方案設定，每個設定都有自己的唯一名稱。 當使用者建立新的方案設定時，IDE 會預設為專案中的對應設定名稱，如果沒有對應的名稱則會進行 Debug。 必要時，使用者可以視需要變更選取範圍以符合特定需求。 此行為的唯一例外狀況是當專案支援的設定符合新解決方案設定的名稱時。 例如，假設方案包含 Project1 和 Project2。 Project1 具有專案設定 Debug、Retail 和 MyConfig1。 Project2 具有專案設定 Debug、Retail 和 MyConfig2。

 如果使用者建立名為 MyConfig2 的新方案設定，Project1 預設會將其偵錯工具設定系結至方案設定。 Project2 預設也會將其 MyConfig2 設定系結至方案設定。

> [!NOTE]
> 系結不區分大小寫。

 當使用者在 [設定] 下拉式清單中選取 **多重選取** 專案時，環境會顯示一個對話方塊，提供可用設定的清單。

 ![多個](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") 設定多個設定

 在此對話方塊中，使用者可以選取一或多個設定。 一旦選取之後，[屬性頁] 對話方塊上顯示的屬性值就會反映所選設定的值交集。

 如需新增和重新命名方案和專案設定的相關資訊，請參閱 [方案](../../extensibility/internals/solution-configuration.md) 設定。

 專案相依性和組建順序與方案設定無關：也就是說，您只能為方案中的所有專案設定一個相依性樹狀結構。 以滑鼠右鍵按一下方案或專案，然後選取 [ **專案** 相依性] 或 [ **專案建立順序** ] 選項，就會開啟 [ **專案** 相依性] 對話方塊。 也可以從 [ **專案** ] 功能表開啟。

 ![專案](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") 相依性專案相依性

 專案相依性會決定專案的建立順序。 您可以使用對話方塊中的 [建立順序] 索引標籤，來查看方案內的專案將建立的確切順序，並使用 [相依性] 索引標籤來修改組建順序。

> [!NOTE]
> 由於或介面所指定的明確相依性，環境會加入清單中已選取核取方塊但呈現暗灰色的專案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> ，而且無法變更。 例如，將專案參考從 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 專案加入至另一個專案時，會自動加入只有藉由刪除參考才能移除的組建相依性。 因為這樣做會建立相依性迴圈，所以無法選取其核取方塊會變成灰色的專案， (例如，Project1 會相依于 Project2，而 Project2 會相依于 Project1) ，而這會使組建停止。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 組建流程包括使用單一組建命令叫用的一般編譯和連結作業。 也可以支援兩個其他組建程式：刪除先前組建中所有輸出專案的清除作業，以及最新的檢查，以判斷設定中的輸出專案是否已變更。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 物件會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> 傳回從) 傳回的對應 (<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A> ，以管理其組建處理常式。 若要在發生組建作業時回報其狀態，設定會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback> ，這是環境所執行的介面，以及任何對組建狀態事件感興趣的其他物件。

 一旦建立之後，就可以使用設定設定來判斷是否可以在偵錯工具控制下執行。 設定會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> 以支援調試。

 在執行專案相依性之後，您可以透過自動化模型，以程式設計方式操作相依性。 您會 <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> 在 automation 模型中呼叫。 沒有可用的 VSIP API 層級介面，可直接操作解決方案組建管理員設定和其屬性。

 此外，您可以在 [專案相依性] 視窗中提供方格。 如需詳細資訊，請參閱 [屬性顯示方格](../../extensibility/internals/properties-display-grid.md)。

## <a name="see-also"></a>另請參閱
- [管理組態選項](../../extensibility/internals/managing-configuration-options.md)
- [管理部署的專案組態](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)
