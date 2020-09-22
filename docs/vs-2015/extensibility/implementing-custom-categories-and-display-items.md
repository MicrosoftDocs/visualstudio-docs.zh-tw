---
title: 執行自訂類別和顯示專案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 474d5c66507b56bea609568b6acfe9f5eff75e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838898"
---
# <a name="implementing-custom-categories-and-display-items"></a>實作自訂類別和顯示項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage 可以透過自訂類別和顯示專案，將其文字的字型和色彩控制提供給 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 整合式開發環境 (IDE) 。  
  
 自訂類別和顯示專案位於 [字型 **和色彩** ] 屬性頁上。 若要開啟 [字型 **和色彩** ] 屬性頁，請按一下 [ **工具** ] 功能表上的 [ **選項**]。 展開 [ **環境** ]，然後按一下 [字型 **和色彩**]。  
  
 使用這種機制時，Vspackage 必須執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> 介面及其相關聯的介面。  
  
 基本上，這個機制可以用來修改所有現有的 **顯示專案** 和包含它們的 **類別** 。 不過，它不應該用來修改 **文字 EditorCategory** 或其 **顯示專案**。 如需詳細資訊，請參閱 [字型和色彩總覽](../extensibility/font-and-color-overview.md)。  
  
 若要執行自訂 **類別** 或 **顯示專案**，VSPackage 必須：  
  
- 建立或識別登錄中的類別。  
  
   IDE 的 [字型 **和色彩** ] 屬性頁的執行會使用這項資訊，正確地查詢支援指定分類的服務。  
  
- 在登錄中建立或識別群組 (選擇性) 。  
  
   定義群組（代表兩個或多個類別的聯集）可能會很有用。 如果已定義群組，IDE 會自動合併子類別，並將顯示專案散發到群組中。  
  
- 執行 IDE 支援。  
  
- 處理字型和色彩變更。  
  
  如需詳細資訊，請參閱 [存取預存字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)。  
  
## <a name="to-create-or-identify-categories"></a>若要建立或識別類別  
  
- 在 [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ `<Category>` ] 下建立特殊類型的分類登錄專案  
  
   *\<Category>* 這是類別目錄的非當地語系化名稱。  
  
- 以兩個值填入登錄：  
  
  |名稱|類型|資料|描述|  
  |----------|----------|----------|-----------------|  
  |類別|REG_SZ|GUID|建立用來識別類別目錄的 GUID。|  
  |套件|REG_SZ|GUID|支援類別目錄之 VSPackage 服務的 GUID。|  
  
  登錄中指定的服務必須針對對應的分類提供的實作為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> 。  
  
## <a name="to-create-or-identify-groups"></a>若要建立或識別群組  
  
- 在 [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<group>* ] 下建立特殊類型的分類登錄專案  
  
   *\<group>* 這是群組的非當地語系化名稱。  
  
- 以兩個值填入登錄：  
  
  |名稱|類型|資料|描述|  
  |----------|----------|----------|-----------------|  
  |類別|REG_SZ|GUID|建立用來識別群組的 GUID。|  
  |套件|REG_SZ|GUID|支援類別目錄的服務 GUID。|  
  
  登錄中指定的服務必須提供對應群組的實作為 `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` 。  
  
## <a name="to-implement-ide-support"></a>若要執行 IDE 支援  
  
- 實作為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` 提供的每個 **類別** 或群組 GUID 的介面或介面。  
  
- 針對它支援的每個 **類別** ，VSPackage 會實作為介面的個別實例 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> 。  
  
- 透過執行的方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> 必須提供 IDE：  
  
  - **類別目錄**中**顯示專案**的清單。  
  
  - **顯示專案**的可當地語系化名稱。  
  
  - 顯示每個 **類別目錄**成員的資訊。  
  
  > [!NOTE]
  > 每個 **類別** 都必須包含至少一個 **顯示專案**。  
  
- IDE 會使用 `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` 介面來定義數個類別的聯集。  
  
   它的實作為 IDE 提供：  
  
  - 組成指定群組的 **類別目錄** 清單。  
  
  - 存取 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> 支援群組內每個 **類別目錄** 的實例。  
  
  - 可當地語系化的組名。  
  
- 更新 IDE：  
  
   IDE 會快取 **字型和色彩** 設定的相關資訊。 因此，在任何修改 IDE **字型和色彩** 設定之後，建議您確認快取是最新的。  
  
  更新快取是透過介面完成 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> ，而且可以在全域或只在選取的專案上執行。  
  
## <a name="to-handle-font-and-color-changes"></a>處理字型和色彩變更  
 若要適當地支援 VSPackage 所顯示之文字的顏色標示，支援 VSPackage 的顏色標示服務必須透過 [字型] **和 [色彩** ] 屬性頁來回應使用者所起始的變更。 VSPackage 執行此動作的方法如下：  
  
- 藉由執行介面來處理 IDE 產生的事件 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> 。  
  
     IDE 會在使用者修改 [字型 **和色彩** ] 頁面之後，呼叫適當的方法。 例如， <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> 如果選取新的字型，則會呼叫方法。  
  
     -或-  
  
- 輪詢 IDE 以進行變更。  
  
     這可以透過系統實行的介面來完成 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 。 雖然主要是為了支援持續性，但是 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 方法可以用來取得 **顯示專案**的字型和色彩資訊。 如需詳細資訊，請參閱 [存取預存字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)。  
  
    > [!NOTE]
    > 為了確保輪詢所取得的結果正確，在呼叫介面的抓取方法之前，使用介面判斷是否需要快取排清和更新可能會很有用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [取得文字顏色標示的字型和色彩資訊](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [存取預存字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)   
 [如何：存取內建字型和色彩配置](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [字型和色彩概觀](../extensibility/font-and-color-overview.md)
