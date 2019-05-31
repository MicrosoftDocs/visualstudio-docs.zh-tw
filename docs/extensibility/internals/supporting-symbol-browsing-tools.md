---
title: 支援符號瀏覽工具 |Microsoft Docs
ms.date: 11/04/2016
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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 649ba0583a70d0d53d8b12f26573daf3c52cf5e9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331196"
---
# <a name="supporting-symbol-browsing-tools"></a>支援符號瀏覽工具
**物件瀏覽器**，**類別檢視**，**呼叫瀏覽器**並**尋找符號結果**工具提供符號瀏覽 Visual Studio 中的功能。 這些工具顯示的符號的階層式樹狀結構檢視，並顯示在樹狀目錄中的符號之間的關聯性。 符號可能代表命名空間、 物件、 類別、 類別成員和各種元件中包含其他語言項目。 這些元件包括 Visual Studio 專案中，外部[!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)]元件和型別 (.tlb) 程式庫。 如需詳細資訊，請參閱[檢視程式碼的結構](../../ide/viewing-the-structure-of-code.md)。

## <a name="symbol-browsing-libraries"></a>符號瀏覽程式庫
 為語言實作者，您可以建立追蹤您的元件中的符號，並透過一組介面 Visual Studio 物件管理員提供的符號清單的程式庫來擴充 Visual Studio 符號瀏覽功能。 所描述的文件庫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2>介面。 Visual Studio 物件管理員回應要求新的資料從符號瀏覽工具與文件庫中取得的資料，並將其組織。 接著，它會填入或更新工具，以要求的資料。 若要取得 Visual Studio 物件管理員 中，參考<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>，傳遞<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager>服務識別碼`GetService`方法。

 每個程式庫必須向 Visual Studio 物件管理員，以收集所有的程式庫中的資訊。 若要註冊程式庫，呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>方法。 取決於哪一種工具起始要求時，Visual Studio object manager 會尋找適當的程式庫，並要求資料。 資料移動程式庫之間，[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]所描述的符號清單中的 物件管理員<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>介面。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員是負責定期重新整理以反映最新的資料包含的程式庫中的符號瀏覽工具。

 下圖中包含的索引鍵的項目之間的程式庫和 Visual Studio 物件管理員要求/資料交換程序的範例。 在圖表中的介面是 managed 程式碼應用程式的一部分。

 ![程式庫和物件管理員之間的資料流程](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 若要提供的符號清單至 Visual Studio 物件管理員，您必須先註冊文件庫與 Visual Studio 物件管理員藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>方法。 此程式庫註冊之後，Visual Studio 物件管理員會要求功能程式庫的特定資訊。 例如，要求程式庫旗標，並支援類別，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A>方法。 在某個時間點，當其中一個工具要求資料此程式庫，從物件管理員要求最上層的符號清單藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A>方法。 在回應中，媒體櫃製造的符號清單，並公開 （expose） 至 Visual Studio 物件管理員透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>介面。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員可讓您判斷多少項目是清單中，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A>方法。 所有下列要求會關聯到指定的項目清單中，並提供項目索引編號，在每個要求。 Visual Studio 物件管理員會繼續收集資訊的類型、 可存取性，以及其他屬性的項目上，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A>方法。

 它會決定項目的名稱，藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A>方法，並藉由呼叫要求圖示資訊<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A>方法。 顯示的項目名稱左邊的圖示，並描述項目、 協助工具，和其他屬性的類型。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A>方法，以判斷指定的清單項目是可展開且有子系的項目。 UI 會傳送要求以展開項目，如果物件管理員會藉由呼叫要求符號的子清單<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A>方法。 視所建立的樹狀結構的不同部分的程序繼續執行。

> [!NOTE]
> 若要實作的原生程式碼符號提供者，請使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2>介面。

## <a name="see-also"></a>另請參閱
- [如何：使用物件管理員註冊程式庫](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [如何：將程式庫提供的符號清單公開至物件管理員](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [如何：識別程式庫中的符號](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)