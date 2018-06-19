---
title: 支援的符號瀏覽工具 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08185f64310da610253dc35e69323b17ab0177fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134580"
---
# <a name="supporting-symbol-browsing-tools"></a>支援的符號瀏覽工具
**物件瀏覽器**，**類別檢視**，**呼叫瀏覽器**和**尋找符號結果**工具提供符號瀏覽 Visual Studio 中的功能。 這些工具中顯示的符號的階層式樹狀檢視，並且顯示在樹狀目錄中的符號之間的關聯性。 符號可能代表命名空間、 物件、 類別、 類別成員和各種元件中包含其他語言項目。 這些元件包括 Visual Studio 專案中，外部[!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)]元件和型別 (.tlb) 程式庫。 如需詳細資訊，請參閱[檢視程式碼的結構](../../ide/viewing-the-structure-of-code.md)。  
  
## <a name="symbol-browsing-libraries"></a>符號瀏覽程式庫  
 為語言實施者，您可以建立追蹤您的元件中的符號，並透過一組介面 Visual Studio 物件管理員提供的符號清單的程式庫來擴充 Visual Studio 符號瀏覽功能。 所描述的文件庫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2>介面。 Visual Studio 物件管理員回應要求新的資料從符號瀏覽工具與文件庫中取得的資料和組織。 接著會填入，或更新工具，以要求的資料。 若要取得 Visual Studio 物件管理員中，參考<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>，傳遞<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager>服務 ID 來`GetService`方法。  
  
 每個程式庫必須向 Visual Studio 物件管理員，在 所有程式庫會收集的資訊。 若要註冊文件庫，呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>方法。 根據哪一種工具起始要求時，Visual Studio 物件管理員會尋找適當的程式庫，並要求資料。 程式庫之間的資料會傳送和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]符號所描述的清單中的 物件管理員<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>介面。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員會負責定期重新整理符號瀏覽工具，以反映最新文件庫中所包含的資料。  
  
 下圖包含的索引鍵的項目之間的程式庫和 Visual Studio 物件管理員的要求/資料交換程序的範例。 在圖表中的介面為 managed 程式碼應用程式的一部分。  
  
 ![程式庫和物件管理員之間的資料流程](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 若要提供的符號清單至 Visual Studio 物件管理員，您必須先註冊文件庫與 Visual Studio 物件管理員藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>方法。 在註冊的程式庫之後，Visual Studio 物件管理員要求的程式庫功能的相關特定資訊。 例如，要求程式庫旗標，並支援類別，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A>方法。 在某些時候，當其中一個工具要求資料，此程式庫，從物件管理員要求最上層的符號清單藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A>方法。 為了回應，媒體櫃製造的符號清單，並使它公開給 Visual Studio 物件管理員透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>介面。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員決定多少項目會在清單中，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A>方法。 下列的所有要求與指定的項目在清單中，並提供項目索引編號，在每個要求。 Visual Studio 物件管理員會繼續收集的資訊上的類型、 可存取性，以及項目的其他屬性，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A>方法。  
  
 它會判斷項目的名稱，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A>方法，並藉由呼叫要求圖示資訊<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A>方法。 圖示會顯示左邊的項目名稱和描述項目、 協助工具，以及其他內容類型。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A>方法，以判斷指定的清單項目是可展開且有子系的項目。 如果 UI 傳送要求以展開的元素，物件管理員會藉由呼叫要求符號的子清單<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A>方法。 程序繼續執行視所建立的樹狀結構不同部分。  
  
> [!NOTE]
>  若要實作的原生程式碼的符號提供者，請使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2>介面。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 註冊物件管理員與程式庫](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [如何： 公開清單的程式庫提供對物件管理員中的符號](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [如何︰識別程式庫中的符號](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)