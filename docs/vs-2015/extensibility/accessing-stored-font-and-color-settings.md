---
title: 存取預存的字型和色彩設定 |Microsoft Docs
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
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8179262ceabe1765ee6c9eab96553bcbcbbee419
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49191395"
---
# <a name="accessing-stored-font-and-color-settings"></a>存取預存的字型和色彩設定
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]整合式的開發環境 (IDE) 會儲存已修改的設定的字型和色彩的登錄中。 您可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面來存取這些設定。  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>若要起始狀態的持續性的字型和色彩  
 字型和色彩資訊會儲存下列登錄位置中依分類: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio 版本 >* \FontAndColors\\ *\<CategoryGUID >*]，其中 *\<CategoryGUID >* 類別 GUID。  
  
 因此，若要起始持續性，VSPackage 必須：  
  
-   取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面，藉由呼叫`QueryService`對全域服務提供者。  
  
     `QueryService` 必須使用的服務識別碼引數來呼叫`SID_SVsFontAndColorStorage`和 介面識別碼引數的`IID_IVsFontAndColorStorage`。  
  
-   使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A>方法來開啟 保存使用類別的 GUID 和模式旗標做為引數類別。  
  
     以指定的模式`fFlags`引數，從中的值建構<xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>列舉型別。 此模式可控制：  
  
    -   您可以透過設定<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面。  
  
    -   所有的設定或只有那些使用者修改，且可透過擷取<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面。  
  
    -   「 的傳播變更使用者設定的方式。  
  
    -   所使用的色彩值的格式。  
  
## <a name="to-use-state-persistence-of-fonts-and-colors"></a>若要使用的字型和色彩的狀態持續性  
 保存的字型和色彩牽涉到：  
  
-   與儲存在登錄中的設定，同步處理的 IDE 設定。  
  
-   傳播登錄修改資訊。  
  
-   設定和擷取儲存在登錄中的設定。  
  
 IDE 設定與同步處理的儲存體設定是透明化的。 基礎的 IDE 會自動寫入更新的設定，如**顯示的項目**至類別的登錄項目。  
  
 如果多個的 Vspackage 會共用特定分類，VSPackage 應要求會產生事件時的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面用來修改預存的登錄設定。  
  
 根據預設，不會啟用事件產生。 若要啟用的事件產生時，類別必須開啟使用<xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>。 這會導致呼叫適當 IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> VSPackage 實作的方法。  
  
> [!NOTE]
>  透過修改**字型和色彩** 屬性頁產生事件的獨立<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>。 您可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>介面，以判斷呼叫的方法之前是否需要更新的快取的字型和色彩設定<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>類別。  
  
### <a name="storing-and-retrieving-information"></a>儲存和擷取資訊  
 若要取得或設定使用者可修改的已命名的顯示中的項目開啟分類的資訊，請呼叫 Vspackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A>方法。  
  
 字型的資訊屬性，對於特定類別由使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A>方法。  
  
> [!NOTE]
>  `fFlags`傳遞給引數<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A>方法，該類別已開啟時定義的行為<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>而<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>方法。 根據預設，這些方法只會傳回資訊 aboutdisplay itemsthat 已變更。 不過，如果類別使用開啟<xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>旗標，同時更新，並變更的顯示項目可以存取<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>。  
  
 根據預設，只變更**顯示的項目**資訊會保留在登錄中。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面不能用來擷取所有設定的字型和色彩。  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>而<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>方法會傳回 REGDB_E_KEYMISSING，當您使用它們來擷取資訊 (0x80040152L) 未變更的相關**顯示項目**。  
  
 所有的設定**顯示的項目**特別**類別目錄**使用的方法可以取得`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults`介面。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [實作自訂類別和顯示項目](../extensibility/implementing-custom-categories-and-display-items.md)

