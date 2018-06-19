---
title: 屬性頁 |Microsoft 文件
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
ms.openlocfilehash: 1b08e210a57388d77859600c02c0e6a30a404884
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133261"
---
# <a name="property-pages"></a>屬性頁
使用者可以檢視和變更使用屬性頁的專案組態相關和-獨立屬性。 A**屬性頁**中啟用按鈕**屬性**視窗或 [方案總管] 工具列上的物件，提供所選物件的屬性頁面上檢視。 屬性頁所建立的環境，而且可供方案和專案。 它們，不過，也可以是可進行的專案項目使用的組態相關的屬性。 在專案中的檔案需要不同的編譯器參數設定，才能正確建置時，可能會使用這項功能。  
  
## <a name="using-property-pages"></a>使用屬性頁  
 如果已顯示屬性頁的選取範圍變更 （例如，從專案的解決方案），資訊顯示在頁面變更為顯示新的選取範圍的屬性。 如果有物件上不支援屬性頁的屬性，屬性頁是空的。  
  
 如果選取多個物件，屬性頁面會顯示所有選取的項目屬性的交集。 如果選取的項目不包含組態相關的屬性和**屬性頁**按一下方案總管 工具列上的按鈕時，焦點變更為 屬性 視窗。 如需詳細資訊與相關屬性 視窗和選取範圍，請參閱[擴充屬性](../../extensibility/internals/extending-properties.md)。  
  
 屬性會顯示多個物件，而且您變更屬性頁中的值，如果所有物件的值會設定為新值即使一開始不同而且頁面是空白時顯示個別物件的屬性。  
  
 有兩種一般的**ProjectProperty 頁面**對話方塊中可用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 第一個範圍，Visual Basic 專案中，例如屬性頁會顯示使用欄位的格式，如下列螢幕擷取畫面所示。 第二、 後面顯示在此區段中，屬性頁面的主機屬性方格類似於在 [屬性] 視窗中找到。  
  
 ![Visual Basic 屬性頁](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
專案屬性頁對話方塊中，與欄位的格式和樹狀結構  
  
 在 [屬性頁] 對話方塊中的樹狀結構未建置使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>。 環境中，根據層級的名稱傳遞給它的<xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>介面，它會建置。  
  
 只有兩個最上層的類別並用於[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]屬性頁：  
  
-   通用屬性，會顯示所選的物件或物件組態無關的資訊。 如此一來，當選取其中一個通用屬性的子類別目錄時，對話方塊頂端的組態、 平台和 Configuration Manager 選項無法使用。  
  
-   組態屬性，其中包含對方案或專案的偵錯、 最佳化，以及建置參數相關的組態相關資訊。  
  
 您無法建立任何額外的頂層類別，但是您可以選擇顯示的實作中的其中一個`IVsPropertyPage`。 例如，您沒有任何組態無關的屬性顯示的物件，如果您可以選擇不想再顯示 [通用屬性] 分類。 如果顯示通用屬性`ISpecifyPropertyPages`實作時，從項目的瀏覽的物件和設定屬性的實作`ISpecifyPropertyPages`組態物件中 (物件實作`IVsCfg`， `IVsProjectCfg`，與相關介面）。  
  
 最上層類別底下顯示每個類別目錄代表不同的屬性頁。 類別目錄和子類別目錄可用的項目 對話方塊中，由實作`ISpecifyPropertyPages`和`IVsPropertyPage`。  
  
 `IDispatch` 物件中選取容器中沒有顯示在屬性頁實作屬性的項目`ISpecifyPropertyPages`列舉類別 Id 的清單。 類別識別碼會當做變數傳遞至`ISpecifyPropertyPages`，並用來具現化的屬性頁。 類別識別碼的清單也會傳遞至`IVsPropertyPage`左邊的對話方塊中建立樹狀結構。 屬性頁則傳遞資訊傳回到`IDispatch`實作物件`ISpecifyPropertyPages`並填入每個頁面的資訊。  
  
 瀏覽物件的屬性會擷取使用`IDispatch`選取容器中每個物件。  
  
 實作`Help::DisplayTopicFromF1Keyword`VSPackage 中提供的功能 [說明] 按鈕。  
  
 如需詳細資訊，請參閱`IDispatch`和`ISpecifyPropertyPages`MSDN library 中。  
  
 屬性頁的第二個類型顯示範例主機中表單的 [屬性] 方格中，如下列螢幕擷取畫面所示。  
  
 ![VC 屬性頁](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
屬性頁對話方塊，與屬性方格  
  
 介面`IVSMDPropertyBrowser`和`IVSMDPropertyGrid`（宣告於 vsmanaged.h） 用來建立並填入屬性方格 對話方塊或視窗內。  
  
 從舊版的專案結構已大幅變更[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 特別是，哪個專案的概念為作用中已變更。 在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，沒有作用中專案的概念。 在上一個開發環境中，使用中的專案已之專案的建置和部署命令不論內容為何，會預設為。 現在，方案控制及 arbitrates 的建置和部署命令套用至哪一個專案。  
  
 現在擷取在三種不同方式的其中一個項目先前已使用中的專案：  
  
-   啟始專案  
  
     您可以指定專案或方案的屬性頁面會在使用者按下 F5，或從 [建置] 功能表中選取執行時啟動的專案。 此工作會以舊的使用中專案，其名稱會顯示在 [方案總管] 中，以粗體字型在概念上類似的方式。  
  
     您可以藉由呼叫 automation 模型中的屬性擷取啟始專案`DTE.Solution.SolutionBuild.StartupProjects`。 VSPackage，在您呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>或<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A>方法。 `IVsSolutionBuildManager` 可做為服務，方法是`QueryService`SID_SVsSolutionBuildManager 上。 如需詳細資訊，請參閱[專案組態物件](../../extensibility/internals/project-configuration-object.md)和[方案組態](../../extensibility/internals/solution-configuration.md)。  
  
-   使用中的方案組建組態  
  
     [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 具有作用中的方案組態，藉由實作 automation 模型中可用`DTE.Solution.SolutionBuild.ActiveConfiguration`。 方案組態是集合，其中包含一個專案設定 （每個專案可以有多個組態，在多種平台，以不同的名稱） 的方案中每個專案。 方案屬性頁的相關詳細資訊，請參閱[方案組態](../../extensibility/internals/solution-configuration.md)。  
  
-   目前選取的專案  
  
     實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A>方法來擷取專案階層架構和專案項目或選取的項目。 您會使用 DTE，`SelectedItems.SelectedItem.Project`和`SelectedItems.SelectedItem.ProjectItem`方法。 沒有核心中的這些標題下的範例程式碼[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]文件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [管理組態選項](../../extensibility/internals/managing-configuration-options.md)   
 [專案組態物件](../../extensibility/internals/project-configuration-object.md)   
 [方案組態](../../extensibility/internals/solution-configuration.md)