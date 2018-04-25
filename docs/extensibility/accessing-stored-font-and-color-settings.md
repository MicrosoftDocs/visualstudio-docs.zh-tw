---
title: 存取預存的字型和色彩設定 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1280555a2b8a293fcdd0f86891a1d198ef3c99d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="accessing-stored-font-and-color-settings"></a>存取預存的字型和色彩設定
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 會儲存已修改的設定的字型和色彩的登錄中。 您可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面，以存取這些設定。

## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>若要起始狀態持續性的字型和色彩
 字型和色彩資訊會儲存在下列登錄位置中的類別目錄: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio 版本 >* \FontAndColors\\ *\<CategoryGUID >*]，其中 *\<CategoryGUID >* 是類別目錄 GUID。

 因此，若要起始持續性，VSPackage 必須：

-   取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面，藉由呼叫`QueryService`針對全域服務提供者。

     `QueryService` 必須使用的服務識別碼引數呼叫`SID_SVsFontAndColorStorage`介面識別碼引數和`IID_IVsFontAndColorStorage`。

-   使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A>方法來開啟 類別目錄，才能保存做為引數使用的類別目錄 GUID 和模式的旗標。

     以指定的模式`fFlags`引數，會建構中的值從<xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>列舉型別。 此模式可控制：

    -   可以透過存取的設定<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面。

    -   所有的設定或那些設定的使用者修改，且皆可透過擷取<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面。

    -   將變更傳播至使用者設定的方式。

    -   所使用的色彩值的格式。

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>若要使用的字型和色彩的狀態持續性
 保存的字型和色彩牽涉到：

-   與儲存在登錄中的設定，同步處理的 IDE 設定。

-   傳播登錄修改資訊。

-   設定和擷取儲存在登錄中的設定。

 IDE 設定與同步處理的存放裝置設定是大致上。 基礎 IDE 會自動寫入的更新的設定**顯示項目**一個類別目錄的登錄項目。

 如果多個 Vspackage 共用特定分類，VSPackage 應該要求會產生事件時的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面用來修改預存的登錄設定。

 根據預設，不會啟用事件產生。 若要啟用事件的產生，類別必須開啟使用<xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>。 開啟 類別目錄會造成呼叫適當 IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> VSPackage 實作的方法。

> [!NOTE]
>  透過修改**字型和色彩**屬性頁產生事件的獨立<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>。 您可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>介面，以判斷是否需要更新的快取的字型和色彩設定呼叫的方法之前<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>類別。

### <a name="storing-and-retrieving-information"></a>儲存和擷取資訊
 要取得或設定使用者可修改具名的顯示中的項目開啟的類別目錄的資訊，請呼叫 Vspackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A>方法。

 字型的相關資訊屬性的特定某類透過使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A>方法。

> [!NOTE]
>  `fFlags`引數傳遞至<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A>開啟該類別的方法定義的行為<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>方法。 根據預設，這些方法只會傳回顯示項目已變更的相關資訊。 不過，如果類別已被使用<xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>旗標，同時更新和變更的顯示的項目可以存取<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>。

 根據預設，只有變更**顯示項目**資訊會儲存在登錄中。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面不能用來擷取所有設定的字型和色彩。

> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>方法傳回未變更的相關 REGDB_E_KEYMISSING，當您使用它們來擷取資訊 (0x80040152L)**顯示項目**。

 所有設定**顯示項目**依特定**類別**可以使用的方法可取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>介面。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>
- [實作自訂的分類和顯示項目](../extensibility/implementing-custom-categories-and-display-items.md)