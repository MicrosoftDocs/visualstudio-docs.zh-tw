---
title: 屬性頁 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51487b35686da9676f201a157ddb8e47afb75ce8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725050"
---
# <a name="property-pages"></a>屬性頁
使用者可以使用屬性頁來查看和變更與專案設定相關且獨立的屬性。 在 **屬性** 視窗中，或在提供所選取物件之屬性頁視圖的物件方案總管 工具列上，會啟用 **屬性頁** 按鈕。 屬性頁是由環境所建立，適用于方案和專案。 不過，它們也可以提供給使用設定相依屬性的專案專案。 當專案中的檔案需要不同的編譯器切換設定才能正確建立時，可能會使用這項功能。

## <a name="using-property-pages"></a>使用屬性頁
 如果屬性頁已顯示，而選取範圍變更（例如，從方案到專案），則頁面中顯示的資訊會變更，以顯示新選取專案的屬性。 如果物件上沒有支援屬性頁的屬性，則屬性頁會是空的。

 如果選取多個物件，[屬性] 頁面會顯示所有選取專案的屬性交集。 如果選取的專案未包含 [設定相依屬性]，而且按一下 [方案總管] 工具列上的 [**屬性頁**] 按鈕，焦點就會變更為屬性視窗。 如需屬性視窗和選取專案的相關詳細資訊，請參閱[擴充屬性](../../extensibility/internals/extending-properties.md)。

 如果顯示多個物件的屬性，而且您變更了屬性頁上的值，則物件的所有值都會設定為新值，即使它們最初是不同的，而且當個別物件的屬性顯示時，該頁面也會是空白的。

 @No__t_1 中提供兩種一般類型的**ProjectProperty 頁面**對話方塊。 在第一個中，針對 Visual Basic 專案，例如，使用欄位格式來顯示內容頁，如下列螢幕擷取畫面所示。 在第二個（如本節稍後所示）中，屬性頁會主控類似于 [屬性] 視窗中找到的屬性方格。

 ![Visual Basic 屬性頁](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")具有欄位格式和樹狀結構的專案屬性頁對話方塊

 [屬性頁] 對話方塊中的樹狀結構不是使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 建立的。 環境（根據 <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> 介面傳遞給它的層級名稱）會建立它。

 @No__t_0 屬性頁上只能使用兩個最上層的類別：

- 通用屬性，會顯示所選取物件或物件的與設定無關的資訊。 如此一來，當選取其中一個 [通用屬性] 子類別時，就無法使用位於對話方塊頂端的 [設定]、[平臺] 和 [Configuration Manager] 選項。

- 設定屬性，其中包含與解決方案或專案的偵錯工具、優化和組建參數相關的設定相關資訊。

  您無法建立任何額外的頂層類別，但可以選擇不要在 `IVsPropertyPage` 的執行中顯示其中一種。 例如，如果您沒有任何與設定無關的屬性可顯示給物件，您可以選擇不顯示 [通用屬性] 類別。 當您在設定物件（執行 `IVsCfg`、`IVsProjectCfg` 和相關介面的物件）中執行 `ISpecifyPropertyPages` 時，您會顯示通用屬性（如果 `ISpecifyPropertyPages` 是從專案的流覽物件和設定屬性中執行）。

  最上層類別底下顯示的每個類別，都代表個別的屬性頁。 對話方塊中可用的類別和子類別目錄專案，是由您的 `ISpecifyPropertyPages` 和 `IVsPropertyPage` 的執行所決定。

  `IDispatch` 選取容器中的專案物件，其中包含要在屬性頁上顯示的屬性，可執行 `ISpecifyPropertyPages` 來列舉類別識別碼的清單。 類別識別碼會當做變數傳遞至 `ISpecifyPropertyPages`，並用來具現化屬性頁。 類別識別碼清單也會傳遞給 `IVsPropertyPage`，以在對話方塊的左側建立樹狀結構。 屬性頁接著會將資訊傳回至執行 `ISpecifyPropertyPages` 的 `IDispatch` 物件，並填入每個頁面的資訊。

  流覽物件的屬性是使用選取容器中每個物件的 `IDispatch` 來抓取。

  在 VSPackage 中執行 `Help::DisplayTopicFromF1Keyword` 可提供 [說明] 按鈕的功能。

  如需詳細資訊，請參閱 MSDN library 中的 `IDispatch` 和 `ISpecifyPropertyPages`in。

  範例中顯示的第二個屬性頁類型會主控屬性方格的形式，如下列螢幕擷取畫面所示。

  ![VC 屬性頁](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")具有屬性方格的 [屬性頁] 對話方塊

  @No__t_0 和 `IVSMDPropertyGrid` 的介面（在 vsmanaged 中宣告）是用來建立和填入對話方塊或視窗內的屬性方格。

  從舊版的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，專案的架構已大幅變更。 特別是，使用中專案的概念已變更。 在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中，沒有使用中專案的概念。 在先前的開發環境中，使用中的專案是組建和部署命令會預設為的專案，不論內容為何。 現在，解決方案會控制並仲裁哪些組建和部署命令適用于哪些專案。

  先前的作用中專案現在是以三種不同的方式之一來捕捉：

- 啟始專案

   您可以從方案的屬性頁指定專案或專案，當使用者按下 F5 或從 [組建] 功能表選取 [執行] 時，就會啟動。 這的運作方式類似于舊的使用中專案，其名稱會以粗體字顯示在方案總管中。

   您可以藉由呼叫 `DTE.Solution.SolutionBuild.StartupProjects`，將啟始專案當做 automation 模型中的屬性來抓取。 在 VSPackage 中，您可以呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> 方法。 `IVsSolutionBuildManager` 是以服務方式提供，`QueryService` 在 SID_SVsSolutionBuildManager 上。 如需詳細資訊，請參閱[專案設定物件](../../extensibility/internals/project-configuration-object.md)和[解決方案](../../extensibility/internals/solution-configuration.md)設定。

- 有效的解決方案組建設定

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 具有有效的解決方案設定，可在自動化模型中藉由執行 `DTE.Solution.SolutionBuild.ActiveConfiguration` 來取得。 解決方案設定是一個集合，其中包含方案中每個專案的一個專案設定（每個專案可以在多個平臺上有多個具有不同名稱的設定）。 如需與解決方案的屬性頁相關的詳細資訊，請參閱[解決方案](../../extensibility/internals/solution-configuration.md)設定。

- 目前選取的專案

   執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> 方法，以取出專案階層和專案專案，或選取的專案。 從 DTE，您會使用 `SelectedItems.SelectedItem.Project` 和 `SelectedItems.SelectedItem.ProjectItem` 方法。 核心 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 檔的這些標題底下有範例程式碼。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [管理組態選項](../../extensibility/internals/managing-configuration-options.md)
- [專案組態物件](../../extensibility/internals/project-configuration-object.md)
- [方案組態](../../extensibility/internals/solution-configuration.md)