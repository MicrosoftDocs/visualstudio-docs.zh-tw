---
title: 存取預存字型和色彩設定 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbb2f118d903eae2124e705f14c7aa7b51bf9c4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821835"
---
# <a name="accessing-stored-font-and-color-settings"></a>存取預存字型和色彩設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]整合式開發環境 (IDE) 將已修改的字型和色彩設定儲存在登錄中。 您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 介面來存取這些設定。  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>起始字型和色彩的狀態持續性  
 字型和色彩資訊是依類別目錄儲存在下列登錄位置： [HKCU\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<CategoryGUID>* ]，其中 *\<CategoryGUID>* 是類別 GUID。  
  
 因此，若要起始持續性，VSPackage 必須：  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>呼叫 `QueryService` 全域服務提供者以取得介面。  
  
     `QueryService` 必須使用的服務識別碼引數 `SID_SVsFontAndColorStorage` 和的介面識別碼引數來呼叫 `IID_IVsFontAndColorStorage` 。  
  
- 您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> 方法，以類別的 GUID 和模式旗標做為引數，來開啟要保存的類別。  
  
  引數所指定的模式 `fFlags` 是從列舉中的值所構成 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> 。 此模式控制：  

  - 可以透過介面存取的設定 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 。  

  - 所有設定，或僅限使用者修改且可透過介面取出的設定 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 。  

  - 將變更傳播到使用者設定的方式。  

  - 所使用色彩值的格式。  

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>使用字型和色彩的狀態持續性  
 保存字型和色彩包含：  
  
- 將 IDE 設定與儲存在登錄中的設定進行同步處理。  
  
- 傳播登錄的修改資訊。  
  
- 設定和取出儲存在登錄中的設定。  
  
  將儲存體設定與 IDE 設定同步處理大多是透明的。 基礎 IDE 會自動將 **顯示專案** 的更新設定寫入至類別目錄的登錄專案。  
  
  如果有多個 Vspackage 共用特定的類別，則在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 使用介面的方法來修改儲存的登錄設定時，VSPackage 應該會要求產生事件。  
  
  依預設，不會啟用事件產生。 若要啟用事件產生，必須使用開啟類別目錄 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> 。 這會導致 IDE 呼叫 VSPackage 所執行的適當 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> 方法。  
  
> [!NOTE]
> 透過 [ **字型] 和 [色彩** ] 屬性頁所做的修改會產生與無關的事件 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 。 在呼叫類別的方法之前，您可以使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> 介面來判斷是否需要更新快取的字型和色彩設定 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 。  
  
### <a name="storing-and-retrieving-information"></a>儲存和取出資訊  
 若要取得或設定使用者可針對開啟類別中的命名顯示專案修改的資訊，請 Vspackage 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> 方法。  
  
 您可以使用和方法，取得特定類別目錄的字型屬性相關資訊 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> 。  
  
> [!NOTE]
> `fFlags`當該分類開啟時，傳遞給方法的引數會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> 定義和方法的行為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> 。 根據預設，這些方法只會傳回 aboutdisplay itemsthat 已變更的資訊。 但是，如果使用旗標來開啟類別 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> ，則和可以存取更新和未變更的顯示專案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> 。  
  
 依預設，只有變更的 **顯示專案** 資訊會保留在登錄中。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面不能用來取得字型和色彩的所有設定。  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> 方法會傳回 REGDB_E_KEYMISSING，當您使用它們來抓取未變更**顯示專案**的相關資訊時， (0x80040152L) 。  
  
 您可以使用介面的方法，取得特定**類別**中所有**顯示專案**的設定 `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` 。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [實作自訂類別和顯示項目](../extensibility/implementing-custom-categories-and-display-items.md)
