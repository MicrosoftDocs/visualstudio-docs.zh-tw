---
title: 實作自訂類別和顯示項目 |Microsoft Docs
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
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f4a9f18330060888527466c29f911a37ce29ce46
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218669"
---
# <a name="implementing-custom-categories-and-display-items"></a>實作自訂類別和顯示項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage 可以提供控制項的字型和色彩，其文字的[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]整合式的開發環境 (IDE) 透過自訂類別和顯示項目。  
  
 自訂類別和顯示項目位於**字型和色彩**屬性頁。 若要開啟 **字型和色彩** 屬性頁面上**工具**功能表上，按一下 **選項**。 依序展開**環境**，然後按一下**字型和色彩**。  
  
 當使用這項機制，Vspackage 必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>介面和其相關聯的介面。  
  
 基本上，這項機制可用來修改現有的所有**顯示的項目**並**類別**包含它們。 不過，它應該不會用來修改**文字 EditorCategory**或其**顯示項目**。 如需詳細資訊，請參閱 <<c0> [ 字型和色彩概觀](../extensibility/font-and-color-overview.md)。  
  
 若要實作自訂**分類**或是**顯示項目**，VSPackage 必須：  
  
-   建立或識別登錄中的類別。  
  
     IDE 的實作**字型和色彩**屬性頁會使用此資訊正確查詢服務，支援指定的類別。  
  
-   建立或識別登錄中 （選擇性） 的群組。  
  
     它可能是適合用來定義群組，這代表兩個或多個類別的聯集。 如果定義群組，則 IDE 會自動合併子類別，並且會顯示群組內的項目。  
  
-   實作 IDE 支援。  
  
-   處理字型和色彩的變更。  
  
 如需資訊，請參閱[存取儲存的字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)。  
  
## <a name="to-create-or-identify-categories"></a>若要建立或識別分類  
  
-   建構一種特殊的類別目錄下的登錄項目 [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio 版本 >* \FontAndColors\\`<Category>`]  
  
     *\<類別目錄 >* 是類別目錄的非當地語系化名稱。  
  
-   填入登錄中的以兩個值：  
  
    |名稱|類型|資料|描述|  
    |----------|----------|----------|-----------------|  
    |分類|REG_SZ|GUID|若要識別類別，建立 GUID。|  
    |Package|REG_SZ|GUID|VSPackage 服務，可支援分類的 GUID。|  
  
 在登錄中指定的服務必須提供實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>對應分類。  
  
## <a name="to-create-or-identify-groups"></a>若要建立或識別群組  
  
-   建構一種特殊的類別目錄下的登錄項目 [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio 版本 >* \FontAndColors\\  *\<群組 >*]  
  
     *\<群組 >* 是群組的非當地語系化名稱。  
  
-   填入登錄中的以兩個值：  
  
    |名稱|類型|資料|描述|  
    |----------|----------|----------|-----------------|  
    |分類|REG_SZ|GUID|建立識別群組的 GUID。|  
    |Package|REG_SZ|GUID|支援的類別目錄服務的 GUID。|  
  
 在登錄中指定的服務必須提供實作`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`對應的群組。  
  
## <a name="to-implement-ide-support"></a>若要實作 IDE 支援  
  
-   實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>，這會傳回<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>介面或有`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`介面，以針對每個 IDE**分類**或群組提供的 GUID。  
  
-   針對每個**分類**它支援、 VSPackage 實作的個別執行個體<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>介面。  
  
-   透過實作方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>必須提供具有的 IDE:  
  
    -   清單**顯示的項目**在**類別目錄。**  
  
    -   可當地語系化的名稱，如**顯示的項目**。  
  
    -   顯示針對每個成員的資訊**分類**。  
  
    > [!NOTE]
    >  每隔**分類**必須包含至少一個**顯示項目**。  
  
-   IDE 使用`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup`介面來定義數個類別的聯集。  
  
     它的實作提供的 IDE:  
  
    -   一份**分類**組成特定的群組。  
  
    -   存取的執行個體<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>支援每個**分類**群組內。  
  
    -   可當地語系化的群組名稱。  
  
-   正在更新 IDE:  
  
     IDE 會快取資訊的相關**字型和色彩**設定。 因此，在 IDE 的任何修改後**字型和色彩**組態，建議您最好確定快取是最新狀態。  
  
 更新快取透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>介面，而且可以是執行全域方式或只在選取的項目。  
  
## <a name="to-handle-font-and-color-changes"></a>若要處理的字型和色彩的變更  
 若要正確支援 VSPackage 顯示文字的顏色標示，支援 VSPackage 的顏色標示服務必須回應使用者起始所做的變更透過**字型和色彩**屬性頁面。 VSPackage 的做法是：  
  
-   藉由實作處理 IDE 所產生的事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>介面。  
  
     IDE 呼叫適當的方法遵循使用者修改**字型和色彩**頁面。 比方說，它會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A>方法如果在選取新的字型。  
  
     -或-  
  
-   輪詢變更的 IDE。  
  
     這可透過系統實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面。 主要目的是為了支援持續性，雖然<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>方法可用來取得字型和色彩資訊**顯示項目**。 如需詳細資訊，請參閱 <<c0> [ 存取儲存的字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)。  
  
    > [!NOTE]
    >  為了確保透過輪詢所得到的結果正確無誤，它可能會使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>介面，以決定在呼叫的擷取方法之前是否需要快取排清和更新<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [取得字型和色彩資訊文字的顏色標示](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [存取預存的字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)   
 [如何： 存取的內建的字型和色彩配置](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [字型和色彩概觀](../extensibility/font-and-color-overview.md)

