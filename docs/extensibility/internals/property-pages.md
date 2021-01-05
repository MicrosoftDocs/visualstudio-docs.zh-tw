---
title: 屬性頁 |Microsoft Docs
description: 瞭解如何在 Visual Studio SDK 中使用新專案類型的屬性頁面，讓使用者能夠查看和變更專案屬性。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 5d446e731c08b85c2c903c2414528ac2a7370c26
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875527"
---
# <a name="property-pages"></a>屬性頁
使用者可使用屬性頁來查看和變更專案設定相依且獨立的屬性。 在 [**屬性**] 視窗或 [方案總管] 工具列上，會針對提供所選取物件之屬性頁視圖的物件啟用 [**屬性頁**] 按鈕。 屬性頁是由環境所建立，而且適用于方案和專案。 不過，它們也可以提供給利用設定相依屬性的專案專案使用。 當專案中的檔案需要不同的編譯器切換設定才能正確建立時，可能會使用這項功能。

## <a name="using-property-pages"></a>使用屬性頁
 如果已顯示內容頁，而且選取專案 (例如，從方案變更為) ，則頁面中顯示的資訊會變更，以顯示新選取專案的屬性。 如果物件上沒有支援屬性頁的屬性，則屬性頁會是空的。

 如果選取多個物件，則屬性頁會顯示所有選取專案的屬性交集。 如果選取的專案不包含設定相依屬性，且按一下 [方案總管] 工具列上的 [ **屬性頁** ] 按鈕，則會將焦點變更為屬性視窗。 如需屬性視窗和選取專案的相關資訊，請參閱 [擴充屬性](../../extensibility/internals/extending-properties.md)。

 如果顯示多個物件的屬性，而且您變更了屬性頁上的值，則物件的所有值都會設定為新的值，即使它們最初是不同的，而且在顯示個別物件的屬性時，頁面也是空白的。

 有兩種一般類型的 **ProjectProperty 頁面** 對話方塊 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 在第一種情況下，在 Visual Basic 專案中，會使用欄位格式來顯示內容頁，如下列螢幕擷取畫面所示。 在第二個（本節稍後所示）中，屬性頁裝載的屬性方格類似于 [屬性] 視窗中找到的屬性。

 ![Visual Basic 屬性頁](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") 具有欄位格式和樹狀結構的 [專案屬性頁] 對話方塊

 [屬性頁] 對話方塊中的樹狀結構並不是使用建立的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 。 環境會根據和介面傳遞給它的層級名稱 <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> ，建立它。

 屬性頁只有兩個最上層類別可用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ：

- 一般屬性，會顯示所選物件的與設定無關的資訊。 如此一來，當選取其中一個 [通用屬性] 子類別時，就無法使用對話方塊頂端的 [設定]、[平臺] 和 [Configuration Manager 選項。

- 設定屬性，其中包含與解決方案或專案的偵錯工具、優化和組建參數相關的設定相關資訊。

  您無法建立任何其他最上層的類別，但您可以選擇不在您的執行中顯示其中一個 `IVsPropertyPage` 。 舉例來說，如果您沒有任何與設定無關的屬性可顯示物件，您可以選擇不顯示 [通用屬性] 類別。 `ISpecifyPropertyPages`當您在設定物件中執行時，如果是從專案的流覽物件和設定屬性執行，則會顯示通用屬性， `ISpecifyPropertyPages` (執行 `IVsCfg` 、 `IVsProjectCfg` 和相關介面) 的物件。

  最上層類別下顯示的每個類別都代表一個不同的屬性頁。 對話方塊中可用的類別目錄和子類別目錄專案，是由和的實作為決定 `ISpecifyPropertyPages` `IVsPropertyPage` 。

  `IDispatch` 選取容器中具有要在屬性頁上顯示內容之專案的物件，會執行 `ISpecifyPropertyPages` 以列舉類別識別碼的清單。 類別識別碼會以變數的形式傳遞至 `ISpecifyPropertyPages` ，並用來具現化屬性頁。 類別識別碼的清單也會傳遞至， `IVsPropertyPage` 以在對話方塊的左邊建立樹狀結構。 屬性頁面接著會將資訊傳回給 `IDispatch` 執行的物件， `ISpecifyPropertyPages` 並填入每個頁面的資訊。

  流覽物件的屬性會使用 `IDispatch` [選取] 容器中的每個物件進行抓取。

  `Help::DisplayTopicFromF1Keyword`在您的 VSPackage 中執行可提供 [說明] 按鈕的功能。

  如需詳細資訊，請參閱 `IDispatch` `ISpecifyPropertyPages` MSDN library 中的和。

  範例中顯示的第二個屬性頁面類型會裝載屬性方格的形式，如下列螢幕擷取畫面所示。

  ![VC 屬性頁](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") 具有屬性方格的 [屬性頁] 對話方塊

  `IVSMDPropertyBrowser` `IVSMDPropertyGrid` 在) vsmanaged 中宣告的介面和 (會用來建立及填入對話方塊或視窗內的屬性方格。

  專案的架構與舊版的變更很明顯 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 尤其是使用中專案的概念已變更。 在中，沒有作用中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 專案的概念。 在先前的開發環境中，使用中專案是組建和部署命令會預設為的專案，不論內容為何。 現在，解決方案會控制和仲裁要套用至哪些專案的組建和部署命令。

  目前使用中的專案是以三種不同的方式之一來捕捉：

- 啟始專案

   您可以從方案的屬性頁指定專案或專案，當使用者按 F5 或從 [建立] 功能表選取 [執行] 時，就會啟動該專案。 這的運作方式類似于舊的作用中專案，其名稱會以粗體字顯示在方案總管中。

   您可以藉由呼叫，以 automation 模型中的屬性形式取出啟始專案 `DTE.Solution.SolutionBuild.StartupProjects` 。 在 VSPackage 中，您可以呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> 方法。 `IVsSolutionBuildManager` SID_SVsSolutionBuildManager 上以服務的形式提供 `QueryService` 。 如需詳細資訊，請參閱 [專案設定物件](../../extensibility/internals/project-configuration-object.md) 和 [方案](../../extensibility/internals/solution-configuration.md)設定。

- 使用中的解決方案組建設定

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 具有作用中的解決方案設定，可透過實作為自動化模型 `DTE.Solution.SolutionBuild.ActiveConfiguration` 。 解決方案設定是一個集合，其中包含方案中每個專案的一個專案設定 (每個專案在多個平臺上都可以有多個設定，) 不同的名稱。 如需與方案的屬性頁相關的詳細資訊，請參閱 [方案](../../extensibility/internals/solution-configuration.md)設定。

- 目前選取的專案

   執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> 方法，以抓取專案階層和專案專案，或選取的專案。 您可以從 DTE 使用 `SelectedItems.SelectedItem.Project` 和 `SelectedItems.SelectedItem.ProjectItem` 方法。 核心檔中的這些標題底下有範例程式碼 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [管理組態選項](../../extensibility/internals/managing-configuration-options.md)
- [專案組態物件](../../extensibility/internals/project-configuration-object.md)
- [解決方案設定](../../extensibility/internals/solution-configuration.md)
