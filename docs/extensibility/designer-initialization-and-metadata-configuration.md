---
title: "設計工具的初始設定和中繼資料組態 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 61624d9926f4d984386f1a8b3fe8a575ce465331
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="designer-initialization-and-metadata-configuration"></a>設計工具的初始設定和中繼資料組態
管理與設計工具或設計工具元件相關聯的中繼資料和篩選條件屬性提供機制，以定義特定的設計工具所使用的工具來處理不同的應用程式<xref:System.Type>物件 （例如資料結構類別或圖形化的實體），在設計工具時，以及如何設定 Visual Studio IDE，以支援在設計工具 (如執行個體的**工具箱**類別目錄或索引標籤可供使用)。  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]提供數種機制，以協助控制的設計工具或設計工具元件初始化與它的中繼資料，VSPackage 所管理。  
  
## <a name="initializing-metadata-and-configuration-information"></a>初始化中繼資料和組態資訊  
 因為它們會視需要載入，Vspackage 可能會有尚未載入[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]之前的具現化的設計工具的環境。 因此，Vspackage 時，無法設定上建立，這是要處理的設計工具或設計工具元件使用的標準機制<xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated>事件。 相反地，VSPackage 實作的執行個體<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>介面，並自行註冊以提供自訂項目，稱為設計介面的延伸模組。  
  
### <a name="customizing-initialization"></a>自訂初始化  
 自訂設計工具、 元件或設計工具的介面，包括：  
  
1.  修改設計工具中繼資料，以及更有效地變更如何特定<xref:System.Type>存取，或轉換。  
  
     這通常是透過<xref:System.Drawing.Design.UITypeEditor>或<xref:System.ComponentModel.TypeConverter>機制。  
  
     例如，當<xref:System.Windows.Forms>-基礎設計工具都已初始化，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境修改<xref:System.Drawing.Design.UITypeEditor>如<xref:System.Web.UI.WebControls.Image>與設計工具用來使用資源管理員取得點陣圖，而不是檔案系統物件。  
  
2.  整合的環境，例如，訂閱事件，或取得專案的組態資訊。 您可以取得專案的組態資訊，並取得訂閱事件<xref:System.ComponentModel.Design.ITypeResolutionService>介面。  
  
3.  藉由啟用適當的使用者環境修改**工具箱**類別目錄或藉由設計工具的適用性限制所套用的執行個體<xref:System.ComponentModel.ToolboxItemFilterAttribute>類別設計工具。  
  
### <a name="designer-initialization-by-a-vspackage"></a>設計工具的 VSPackage 的初始化  
 VSPackage 應該處理由設計工具的初始設定：  
  
1.  建立實作<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>類別。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>類別應該永遠不會為相同的物件上實作<xref:Microsoft.VisualStudio.Shell.Package>類別。  
  
2.  註冊類別實作<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>做為提供的 VSPackage 的設計工具擴充功能的支援，藉由套用的執行個體<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>，<xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>和<xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>類別提供的 VSPackage 實作<xref:Microsoft.VisualStudio.Shell.Package>.  
  
 建立任何的設計工具或設計工具元件時，每當[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境：  
  
1.  存取每個已註冊的設計介面的擴充提供者。  
  
2.  執行個體化並初始化的每個的設計介面的擴充提供者的執行個體<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>物件  
  
3.  呼叫每個的設計介面的擴充提供者的<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>方法或<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A>方法 （視情況）。  
  
 當實作<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>物件當做成員的 VSPackage，請務必了解：  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境不提供任何控制哪些中繼資料或其他特殊的組態設定`DesignSurfaceExtension`提供者的修改。 可能的兩部以上`DesignSurfaceExtension`衝突的方式修改相同的設計工具功能，最後修改正在最終的提供者。 它是不定上次套用的修改。  
  
2.  您可明確限制的實作<xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>特定設計工具中，藉由套用的執行個體的物件<xref:System.ComponentModel.ToolboxItemFilterAttribute>該實作。 如需有關**工具箱**篩選項目，請參閱<xref:System.ComponentModel.ToolboxItemFilterAttribute>和<xref:System.ComponentModel.ToolboxItemFilterType>。  
  
## <a name="additional-metadata-provisioning"></a>佈建額外的中繼資料  
 VSPackage 可以變更組態設計工具或設計工具以外的元件在設計階段。  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>類別可以用程式設計的方式，或套用至 VSPackage 提供的設計工具。  
  
 執行個體<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>類別用來修改元件在設計介面上建立的中繼資料。 例如，一個無法取代所使用的預設屬性瀏覽器<xref:System.Windows.Forms.CommonDialog>物件，使用自訂屬性瀏覽器。  
  
 執行個體所提供的修改<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>套用至 VSPackage 實作<xref:Microsoft.VisualStudio.Shell.Package>可以有兩個範圍的其中一個：  
  
-   Global-針對所有新的執行個體指定的元件  
  
-   本機-指只有在目前 VSPackage 提供的設計介面上建立的元件執行個體。  
  
 `IsGlobal`屬性<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>套用至 VSPackage 實作的執行個體<xref:Microsoft.VisualStudio.Shell.Package>決定此範圍。  
  
 這個屬性套用至實作<xref:Microsoft.VisualStudio.Shell.Package>與<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A>屬性<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>物件設定為`true`下，變更整個瀏覽器[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境：  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 如果全域旗標設為`false`，則中繼資料變更是目前的設計工具支援目前 VSPackage 的本機：  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  在現階段，設計介面只支援建立的元件，因此只元件可以有本機中繼資料。 在上述範例中，我們已嘗試修改屬性，例如`Color`物件的屬性。 如果`false`傳入的全域旗標，`CustomBrowser`會永遠不會出現在設計工具不會實際建立的執行個體因為`Color`。 若要設定全域旗標`false`適用於元件，例如控制項、 計時器和對話方塊。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [擴充設計階段支援](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)