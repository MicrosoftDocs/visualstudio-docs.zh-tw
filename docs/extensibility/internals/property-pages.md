---
title: 屬性頁 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac788f51bcdc52cd39469a272909890333c5016b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706061"
---
# <a name="property-pages"></a>屬性頁
用戶可以使用屬性頁查看和更改與專案配置無關的屬性和 - 獨立屬性。 屬性**頁**按鈕在 **「屬性」** 視窗或解決方案資源管理器工具列上為提供所選物件的屬性頁視圖的物件啟用。 屬性頁由環境創建,可用於解決方案和專案。 但是,它們也可以提供給使用與配置相關的屬性的專案項。 當專案中的檔需要不同的編譯器開關設置才能正確生成時,可能會使用此功能。

## <a name="using-property-pages"></a>使用屬性頁
 如果屬性頁已顯示且所選內容發生更改(例如,從解決方案到專案),則頁面中顯示的資訊將更改以顯示新選擇的屬性。 如果物件上沒有支援屬性頁的屬性,則屬性頁為空。

 如果選擇了多個物件,則屬性頁將顯示所有選定項的屬集。 如果所選項不包含與配置相關的屬性,並且按下"解決方案資源管理器"工具列上**的屬性頁**按鈕,則對焦將更改為"屬性"視窗。 關於屬性視窗與選擇的詳細資訊,請參考[副檔屬性](../../extensibility/internals/extending-properties.md)。

 如果為多個物件顯示屬性,並在屬性頁上更改值,則物件的所有值都設置為新值,即使它們最初不同,並且當顯示單個物件的屬性時頁面為空也是如此。

 中提供了兩種一般類型的**項目屬性頁**[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]對話框 。 例如,在第一個中,對於 Visual Basic 專案,屬性頁使用欄位格式顯示,如下圖所示。 在第二部分(本節後面顯示)中,屬性頁承載的屬性網格與屬性視窗中的屬性網格類似。

 ![視覺化基本屬性頁](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")具有欄位格式與樹結構的項目屬性頁對話框

 屬性頁對話框中的樹結構不是使用 建<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>構的 。 環境基於介面<xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages><xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>傳遞給它的級別名稱,生成它。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]屬性頁面上只有兩個頂級類別可用:

- 公共屬性,它顯示所選物件或物件與配置無關的資訊。 因此,當選擇「通用屬性」子類別之一時,對話框頂部的「設定、平臺」和「設定管理員」選項不可用。

- 配置屬性,其中包含與解決方案或項目的調試、優化和生成參數相關的配置資訊。

  不能創建任何其他頂級類別,但可以選擇在的實現中不顯示其中一`IVsPropertyPage`個類別。 例如,如果您沒有任何與配置無關的屬性要顯示物件,則可以選擇不顯示"公共屬性"類別。 在配置物件(對`ISpecifyPropertyPages`象`IVsCfg`實現`IVsProjectCfg`) 和相關介面中實現時,如果從專案`ISpecifyPropertyPages`的流覽物件和配置屬性實現,則顯示公共屬性。

  顯示在頂級類別下的每個類別表示單獨的屬性頁。 對話框中可用的類別和子類別條目由和`ISpecifyPropertyPages``IVsPropertyPage`的實現確定。

  `IDispatch`選擇容器中具有要在屬性頁上顯示的屬性的物件,以`ISpecifyPropertyPages`枚舉類 I 的清單。 類I以變數傳遞到`ISpecifyPropertyPages`,並用於實例化屬性頁。 類別指示清單也會傳遞給,`IVsPropertyPage`以建立對話框左邊的樹結構。 然後,屬性頁將信息傳遞回實現`IDispatch``ISpecifyPropertyPages`並填充每個頁面的資訊的物件。

  使用`IDispatch`選擇容器中的每個物件檢索流覽物件的屬性。

  在`Help::DisplayTopicFromF1Keyword`VSPackage 中實現為"説明"按鈕提供了功能。

  有關詳細資訊,請參閱`IDispatch`MSDN`ISpecifyPropertyPages`庫中和。

  示例中顯示的第二種屬性頁承載屬性網格的形式,如下圖所示。

  ![VC 屬性頁](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")屬性頁對話框包含屬性格線

  介面`IVSMDPropertyBrowser``IVSMDPropertyGrid`和 (在 vs 託管.h 中聲明)用於在對話框或視窗中創建和填充屬性網格。

  與過去的版本相比,專案的體系結構已經發生了很大變化[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 特別是,哪個項目處於活動狀態的概念已經改變。 在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中,沒有活動專案的概念。 在以前的開發環境中,活動項目是產生和部署指令的項目,無論上下文如何,都預設為 。 現在,解決方案控制和仲裁生成和部署命令適用於哪些專案。

  以前處於活動狀態的項目現在以三種不同方式之一捕獲:

- 啟動項目

   您可以從解決方案的屬性頁指定專案或專案,當使用者按 F5 或從「生成」功能表中選擇「執行」時,該專案將啟動該專案或專案。 其工作方式與舊活動項目類似,其名稱以粗體顯示在解決方案資源管理器中。

   您可以通過調`DTE.Solution.SolutionBuild.StartupProjects`用 來檢索啟動專案作為自動化模型中的屬性。 在 VSPackage 中,<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>呼<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>叫或方法。 `IVsSolutionBuildManager`可在SID_SVsSolutionBuildManager`QueryService`作為服務提供。 關於詳細資訊,請參考[專案設定物件](../../extensibility/internals/project-configuration-object.md)與[解決方案設定](../../extensibility/internals/solution-configuration.md)。

- 活動解決方案產生設定

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]具有活動解決方案配置,可通過實現`DTE.Solution.SolutionBuild.ActiveConfiguration`在自動化模型中提供。 解決方案配置是一個集合,其中包含解決方案中每個專案的一個專案配置(每個專案可以在多個平臺上具有多個配置,名稱不同)。 有關解決方案屬性頁的詳細資訊,請參閱[解決方案設定](../../extensibility/internals/solution-configuration.md)。

- 目前選取的項目

   實現方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A>以檢索專案層次結構和專案項或所選項。 在 DTE 中,`SelectedItems.SelectedItem.Project`您`SelectedItems.SelectedItem.ProjectItem`將使用和方法。 核心[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]文件中這些標題下有示例代碼。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [管理組態選項](../../extensibility/internals/managing-configuration-options.md)
- [專案組態物件](../../extensibility/internals/project-configuration-object.md)
- [方案組態](../../extensibility/internals/solution-configuration.md)
