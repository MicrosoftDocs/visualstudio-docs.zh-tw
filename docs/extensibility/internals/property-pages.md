---
title: 屬性頁 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 42638d9ae5467ec3b8cf8341a170b9b7eca9e86e
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512014"
---
# <a name="property-pages"></a>屬性頁
使用者可以檢視和變更使用屬性頁的專案組態相關和-獨立屬性。 A**屬性頁**中已啟用 按鈕**屬性**視窗或 方案總管 工具列上的物件可提供所選物件的屬性頁面檢視。 屬性頁所建立的環境，並可供方案和專案。 它們，不過，也可以是可進行的專案項目使用的組態相關的屬性。 當專案中的檔案需要不同的編譯器參數設定，才能正確建置時，可能會使用這項功能。  
  
## <a name="using-property-pages"></a>使用屬性頁  
 如果已顯示的屬性頁的選取範圍變更 （例如，從專案的解決方案），資訊顯示在頁面變更為顯示新的選取範圍的屬性。 如果有物件上不支援屬性頁的屬性，[屬性] 頁面是空的。  
  
 如果選取多個物件，[屬性] 頁面會顯示所有選取的項目屬性的交集。 如果選取的項目不包含組態相關的屬性和**屬性頁**按一下方案總管 工具列上的按鈕時，焦點變更至 屬性 視窗。 [屬性視窗] 和選取項目與相關的詳細資訊，請參閱[擴充屬性](../../extensibility/internals/extending-properties.md)。  
  
 如果屬性會顯示多個物件，而且您變更值，以在 [屬性] 頁面上，所有物件的值會設定為新值即使一開始不同而且頁面是空白時顯示個別物件的屬性。  
  
 有兩種一般的**ProjectProperty 頁面**對話方塊中可用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 在第一個 Visual Basic 專案，例如，屬性頁會顯示使用欄位的格式，如下列螢幕擷取畫面所示。 在第二個，稍後說明本節中，屬性頁面主機屬性 方格類似於在 屬性 視窗中找到。  
  
 ![Visual Basic 屬性頁](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
專案屬性頁 對話方塊中欄位的格式和樹狀結構  
  
 在 [屬性頁] 對話方塊中的樹狀結構不是使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>。 環境中，根據層級的名稱傳遞給它所<xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>而<xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>介面，來建置它。  
  
 只有兩個最上層類別是用於[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]屬性頁：  
  
-   通用屬性，會顯示所選取的物件或物件的獨立設定的資訊。 如此一來，選取其中一個通用屬性的子類別目錄時，頂端的 [] 對話方塊中的組態、 平台和 Configuration Manager 的選項無法使用。  
  
-   組態屬性，其中包含與方案或專案的偵錯、 最佳化及組建參數相關的組態相關資訊。  
  
 您無法建立任何額外的最上層類別，但是您可以選擇不想再顯示在您實作的其中一種`IVsPropertyPage`。 如果，比方說，您還沒有任何設定獨立屬性，以顯示物件，您可以選擇不想再顯示通用屬性類別目錄。 如果您顯示通用屬性`ISpecifyPropertyPages`實作時，會將項目的瀏覽的物件與組態屬性實作`ISpecifyPropertyPages`組態物件中 (物件，實作`IVsCfg`， `IVsProjectCfg`，和相關介面）。  
  
 下最上層類別顯示每個類別都代表一個個別的屬性頁面。 類別目錄和子類別目錄中的項目可用的對話方塊取決於您實作`ISpecifyPropertyPages`和`IVsPropertyPage`。  
  
 `IDispatch` 物件中選取容器中沒有顯示在 屬性頁面實作的屬性的項目`ISpecifyPropertyPages`列舉類別 Id 的清單。 類別識別碼會當做變數傳遞至`ISpecifyPropertyPages`，並用來具現化的屬性頁。 類別識別碼的清單也會傳遞至`IVsPropertyPage`建立對話方塊的左側的樹狀結構。 屬性頁則傳遞資訊回到`IDispatch`可實作物件`ISpecifyPropertyPages`並填滿每個頁面的資訊。  
  
 瀏覽物件的屬性會擷取使用`IDispatch`選取容器中每個物件。  
  
 實作`Help::DisplayTopicFromF1Keyword`VSPackage 中提供的功能 [說明] 按鈕。  
  
 如需詳細資訊，請參閱 <<c0> `IDispatch` 和`ISpecifyPropertyPages`MSDN library 中。  
  
 第二個類型的屬性頁面顯示範例主機中表單的 [屬性] 方格中，如下列螢幕擷取畫面所示。  
  
 ![VC 屬性頁](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
屬性頁 對話方塊中使用屬性方格  
  
 介面`IVSMDPropertyBrowser`和`IVSMDPropertyGrid`（vsmanaged.h 中宣告） 用來建立和填入對話方塊或視窗中的 [屬性] 方格。  
  
 專案的架構已大幅變更，從舊版[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 特別是，哪一個專案的概念是作用中已變更。 在  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，沒有使用中專案的概念。 在先前的開發環境中，使用中的專案已之專案的建置和部署命令會預設為不論內容為何。 現在，控制解決方案，並將其建置和部署命令會進行仲裁會套用至哪一個專案。  
  
 在下列三種不同的方式現在擷取功能先前使用中的專案：  
  
-   啟始專案  
  
     您可以指定專案或方案的屬性頁，將會啟動，當使用者按下 F5，或從 [建置] 功能表中選取執行專案。 這適用於以類似舊的使用中專案，其名稱會顯示在 [方案總管] 中，使用粗體字型的意義的方式。  
  
     您也可以呼叫 automation 模型中的屬性擷取啟始專案`DTE.Solution.SolutionBuild.StartupProjects`。 在 VSPackage 中，您可以呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>方法。 `IVsSolutionBuildManager` 是由以服務形式供`QueryService`SID_SVsSolutionBuildManager 上。 如需詳細資訊，請參閱 <<c0> [ 專案組態物件](../../extensibility/internals/project-configuration-object.md)並[方案組態](../../extensibility/internals/solution-configuration.md)。  
  
-   使用中的方案組建組態  
  
     [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 具有使用中的方案設定，藉由實作 automation 模型中，您可以使用`DTE.Solution.SolutionBuild.ActiveConfiguration`。 方案組態是集合，其中包含一個專案設定 （每個專案可以有多個組態，在使用不同名稱的多重平台） 的方案中的每個專案。 方案屬性頁的相關詳細資訊，請參閱[方案組態](../../extensibility/internals/solution-configuration.md)。  
  
-   目前選取的專案  
  
     實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A>方法來擷取專案階層架構和專案項目或選取的項目。 從 DTE，您會使用`SelectedItems.SelectedItem.Project`和`SelectedItems.SelectedItem.ProjectItem`方法。 在核心中的這些標題下的範例程式碼[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]文件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [管理組態選項](../../extensibility/internals/managing-configuration-options.md)   
 [專案組態物件](../../extensibility/internals/project-configuration-object.md)   
 [方案組態](../../extensibility/internals/solution-configuration.md)