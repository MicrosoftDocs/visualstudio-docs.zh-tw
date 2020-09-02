---
title: 設計工具初始化和中繼資料設定 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2dec3937616c712c56b7012949e044702e6b11f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703074"
---
# <a name="designer-initialization-and-metadata-configuration"></a>設計工具初始化和中繼資料組態
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

管理與設計工具或設計工具元件相關聯的中繼資料和篩選屬性，可提供一種機制，讓應用程式定義特定設計工具使用哪些工具來處理不同的 <xref:System.Type> 物件 (例如資料結構、類別或圖形實體) 、可用的設計工具，以及 Visual Studio 的 IDE 如何設定為支援設計工具 (例如，可以使用 [ **工具箱** ] 分類或索引標籤) 。  
  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]提供數種機制，可協助您控制設計工具或設計工具元件的初始化，以及透過 VSPackage 來操作其中繼資料。  
  
## <a name="initializing-metadata-and-configuration-information"></a>初始化中繼資料和設定資訊  
 因為它們是視需要載入，所以在設計工具具現化之前，環境可能尚未載入 Vspackage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 因此，在建立時，Vspackage 無法使用標準機制來設定設計工具或設計工具元件，也就是處理 <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> 事件。 相反地，VSPackage 會執行介面的實例 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> ，並自行註冊以提供自訂，稱為設計介面延伸。  
  
### <a name="customizing-initialization"></a>自訂初始化  
 自訂設計工具、元件或設計工具介面，包括：  
  
1. 修改設計工具中繼資料，並有效地變更特定 <xref:System.Type> 存取或轉換的方式。  
  
     這通常是透過 <xref:System.Drawing.Design.UITypeEditor> 或機制來完成 <xref:System.ComponentModel.TypeConverter> 。  
  
     例如，當 <xref:System.Windows.Forms> 初始化設計工具時，環境會修改與設計工具搭配使用的物件，以 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <xref:System.Drawing.Design.UITypeEditor> <xref:System.Web.UI.WebControls.Image> 使用資源管理員來取得點陣圖，而不是檔案系統。  
  
2. 與環境整合，例如，藉由訂閱事件或取得專案設定資訊。 您可以取得專案設定資訊，並藉由取得介面來訂閱事件 <xref:System.ComponentModel.Design.ITypeResolutionService> 。  
  
3. 藉由啟用適當的工具箱分類，或藉由將類別的實例套用至設計工具來限制設計 **工具** 的適用性，以修改使用者環境 <xref:System.ComponentModel.ToolboxItemFilterAttribute> 。  
  
### <a name="designer-initialization-by-a-vspackage"></a>VSPackage 的設計工具初始化  
 VSPackage 應該透過下列方式來處理設計工具初始化：  
  
1. 建立執行類別的物件 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 。  
  
   > [!NOTE]
   > <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>類別絕對不應該在與類別相同的物件上執行 <xref:Microsoft.VisualStudio.Shell.Package> 。  
  
2. 註冊類別，以藉 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 由將的實例  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> 和 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> 提供 VSPackage 之實作為的類別，來支援 VSPackage 的設計工具延伸模組 <xref:Microsoft.VisualStudio.Shell.Package> 。  
  
   每當建立任何設計工具或設計工具元件時， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 環境都會：  
  
3. 存取每個已註冊的設計介面擴充功能提供者。  
  
4. 具現化並初始化每個設計介面擴充提供者 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 物件的實例  
  
5. 呼叫每個設計介面擴充提供者的 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> 方法或 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> 方法 (適當的) 。  
  
   將物件實 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 作為 VSPackage 的成員時，請務必瞭解：  
  
6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]環境不會針對特定 `DesignSurfaceExtension` 提供者修改的中繼資料或其他設定設定提供任何控制權。 有兩個或多個 `DesignSurfaceExtension` 提供者可在衝突的情況下修改相同的設計工具功能，最終的修改是最終的修改方式。 它不確定上次套用的修改。  
  
7. 您可以藉由將的 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> 實例套用至特定的設計工具，以明確限制物件的執行 <xref:System.ComponentModel.ToolboxItemFilterAttribute> 。 如需 [ **工具箱** ] 專案篩選的詳細資訊，請參閱 <xref:System.ComponentModel.ToolboxItemFilterAttribute> 和 <xref:System.ComponentModel.ToolboxItemFilterType> 。  
  
## <a name="additional-metadata-provisioning"></a>額外的中繼資料布建  
 VSPackage 可以在設計階段變更設計工具或設計工具元件的設定。  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>類別可以用程式設計方式使用，或套用至提供設計工具的 VSPackage。  
  
 類別的實例 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> 是用來修改在設計介面上建立之元件的中繼資料。 例如，您可以 <xref:System.Windows.Forms.CommonDialog> 使用自訂的屬性瀏覽器來取代物件所使用的預設屬性瀏覽器。  
  
 套用 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> 至 VSPackage 之執行的實例所提供的修改 <xref:Microsoft.VisualStudio.Shell.Package> 可以有兩個範圍之一：  
  
- Global--適用于指定元件的所有新實例  
  
- Local--僅與目前 VSPackage 所提供之設計介面上建立的元件實例有關。  
  
  套用 `IsGlobal` <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> 至 VSPackage 之執行的實例屬性會 <xref:Microsoft.VisualStudio.Shell.Package> 決定這個範圍。  
  
  將屬性（attribute）的屬性（attribute）套用至的實 <xref:Microsoft.VisualStudio.Shell.Package> <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> ，如下所示 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> `true` ，變更整個環境的瀏覽器 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ：  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
  如果全域旗標設定為 `false` ，則中繼資料變更會在目前 VSPackage 目前所支援的設計工具的本機變更：  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
> [!NOTE]
> 目前，設計介面僅支援建立元件，因此只有元件可以有本機中繼資料。 在上述範例中，我們嘗試修改屬性，例如 `Color` 物件的屬性。 如果 `false` 傳入全域旗標的，則 `CustomBrowser` 永遠不會出現，因為設計工具絕不會實際建立的實例 `Color` 。 將全域旗標設定為對 `false` 元件（例如控制項、計時器和對話方塊）很有用。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [擴充設計階段支援](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
