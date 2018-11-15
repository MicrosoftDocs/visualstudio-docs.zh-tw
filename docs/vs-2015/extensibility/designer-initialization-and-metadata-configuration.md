---
title: 設計工具初始化和中繼資料組態 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41ea3342f19639a7051e5c9dfb641620b1b6688b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49821990"
---
# <a name="designer-initialization-and-metadata-configuration"></a>設計工具初始化和中繼資料組態
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

操作的中繼資料和篩選器相關聯的屬性使用設計工具或設計工具元件提供一個機制，來定義特定的設計工具所使用的工具來處理不同的應用程式<xref:System.Type>物件 （例如資料結構類別或圖形化的實體），當設計工具可用，而且 Visual Studio IDE 的設定以支援設計工具的方式 (如執行個體這**工具箱**分類或索引標籤可供使用)。  
  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]提供數種機制，以協助設計工具或設計工具元件初始化的控制項和它的中繼資料，VSPackage 所管理。  
  
## <a name="initializing-metadata-and-configuration-information"></a>初始化中繼資料和組態資訊  
 因為它們是依需求載入，Vspackage 可能會有尚未載入[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]之前的具現化的設計工具的環境。 因此，Vspackage 時，無法在建立後，也就是處理設定設計工具或設計工具元件使用的標準機制<xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated>事件。 相反地，VSPackage 實作的執行個體<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>介面，並自行註冊以提供自訂項目，稱為設計介面的延伸模組。  
  
### <a name="customizing-initialization"></a>自訂初始設定  
 自訂設計工具、 元件或設計工具的介面，包括：  
  
1.  修改設計工具的中繼資料，以及更有效地變更如何特定<xref:System.Type>是存取或轉換。  
  
     這通常透過<xref:System.Drawing.Design.UITypeEditor>或<xref:System.ComponentModel.TypeConverter>機制。  
  
     例如，當<xref:System.Windows.Forms>-根據設計工具都已初始化，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]環境修改<xref:System.Drawing.Design.UITypeEditor>如<xref:System.Web.UI.WebControls.Image>與設計工具來使用資源管理員以取得點陣圖，而不是檔案系統的物件。  
  
2.  整合環境，例如，藉由訂閱事件，或取得專案的組態資訊。 您可以取得專案的組態資訊，並取得訂閱事件<xref:System.ComponentModel.Design.ITypeResolutionService>介面。  
  
3.  藉由啟用適當的使用者環境修改**工具箱**類別目錄或藉由限制所套用的執行個體的設計工具的適用性<xref:System.ComponentModel.ToolboxItemFilterAttribute>類別設計工具。  
  
### <a name="designer-initialization-by-a-vspackage"></a>VSPackage 的設計工具初始化  
 VSPackage 應該處理由設計工具初始化：  
  
1. 建立物件，實作<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>類別。  
  
   > [!NOTE]
   >  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>應該永遠不會在相同物件上實作類別<xref:Microsoft.VisualStudio.Shell.Package>類別。  
  
2. 註冊類別實作<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>做為 VSPackage 的設計工具擴充功能提供支援，藉由套用的執行個體<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>，<xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>並<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>提供的 VSPackage 的實作類別<xref:Microsoft.VisualStudio.Shell.Package>.  
  
   建立任何的設計工具或設計工具元件時，每當[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]環境：  
  
3. 存取每個已註冊的設計介面的延伸模組提供者。  
  
4. 具現化並初始化每個的設計介面的延伸模組提供者的執行個體<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>物件  
  
5. 呼叫每一個設計介面的延伸模組提供者<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>方法或<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A>方法 （視情況）。  
  
   當實作<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>物件做為成員的 VSPackage，請務必了解：  
  
6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]環境中不提供任何控制哪些中繼資料或特定的其他組態設定`DesignSurfaceExtension`提供者的修改。 您有兩個或多個`DesignSurfaceExtension`衝突的方式，修改相同的設計工具功能，最終的修改所限定的提供者。 它為不定上次套用的修改。  
  
7. 您可明確限制的實作<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>特定的設計工具，藉由套用的執行個體的物件<xref:System.ComponentModel.ToolboxItemFilterAttribute>該實作。 如需詳細資訊**工具箱**項目篩選，請參閱<xref:System.ComponentModel.ToolboxItemFilterAttribute>和<xref:System.ComponentModel.ToolboxItemFilterType>。  
  
## <a name="additional-metadata-provisioning"></a>佈建額外的中繼資料  
 VSPackage 可以變更組態設計工具或設計工具以外的元件在設計階段。  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>類別可以用程式設計的方式，或套用至 VSPackage 提供設計工具。  
  
 執行個體<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>類別用來修改元件在設計介面上建立的中繼資料。 例如，一個可以取代預設屬性瀏覽器中使用<xref:System.Windows.Forms.CommonDialog>物件，使用自訂屬性瀏覽器。  
  
 修改提供的執行個體所<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>套用至 VSPackage 實作<xref:Microsoft.VisualStudio.Shell.Package>可以有兩個範圍的其中一個：  
  
- 全域-針對所有新的執行個體的指定元件  
  
- 本機-有關只由目前 VSPackage 所提供的設計介面上所建立的元件的執行個體。  
  
  `IsGlobal`的屬性<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>套用至 VSPackage 實作的執行個體<xref:Microsoft.VisualStudio.Shell.Package>決定這個範圍。  
  
  將屬性套用至實作<xref:Microsoft.VisualStudio.Shell.Package>具有<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A>屬性<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>物件設為`true`，，如下所示，變更整個瀏覽器[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]環境：  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
  如果全域旗標設為`false`，則目前的設計工具目前 VSPackage 支援的本機中繼資料變更：  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  在現階段，設計介面僅支援建立的元件，因此只元件可以有本機中繼資料。 在上述範例中，我們已嘗試修改屬性，例如`Color`物件的屬性。 如果`false`為全域的旗標，傳入`CustomBrowser`永遠不會出現，因為設計工具不會實際建立的執行個體`Color`。 全域旗標設定為`false`適用於元件，例如控制項、 計時器和對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [擴充設計階段支援](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)

