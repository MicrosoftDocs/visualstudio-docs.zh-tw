---
title: 支援符號流覽工具 |Microsoft Docs
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
ms.openlocfilehash: ca171fa75adda3deef5b941852fc3e6c648c84c6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723074"
---
# <a name="supporting-symbol-browsing-tools"></a>支援符號瀏覽工具
**物件瀏覽器**、**類別檢視**、**呼叫瀏覽器**和**尋找符號結果**工具會在 Visual Studio 中提供符號流覽功能。 這些工具會顯示符號的階層式樹狀檢視，並顯示樹狀結構中符號之間的關聯性。 這些符號可能代表命名空間、物件、類別、類別成員，以及包含在各種元件中的其他語言元素。 這些元件包括 Visual Studio 專案、外部 .NET Framework 元件和類型（.tlb）程式庫。 如需詳細資訊，請參閱[檢視程式碼的結構](../../ide/viewing-the-structure-of-code.md)。

## <a name="symbol-browsing-libraries"></a>符號流覽程式庫
 身為語言實施者，您可以藉由建立程式庫來追蹤元件中的符號，並透過一組介面提供符號清單給 Visual Studio 物件管理員，來擴充 Visual Studio 符號流覽功能。 程式庫是由 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> 介面所描述。 Visual Studio 物件管理員會從程式庫取得資料並加以組織，以回應來自符號流覽工具的新資料要求。 接著，它會使用要求的資料來填入或更新工具。 若要取得 Visual Studio 物件管理員的參考，請 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>，將 <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> 服務識別碼傳遞給 `GetService` 方法。

 每個程式庫都必須向 Visual Studio 物件管理員註冊，這會收集所有程式庫上的資訊。 若要註冊程式庫，請呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 方法。 根據起始要求的工具而定，Visual Studio 物件管理員會尋找適當的程式庫並要求資料。 在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> 介面所描述的符號清單中，資料在程式庫和 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 物件管理員之間移動。

 @No__t_0 物件管理員負責定期重新整理符號流覽工具，以反映程式庫中包含的最新資料。

 下圖包含程式庫和 Visual Studio 物件管理員之間的要求/資料交換程式的重要元素範例。 圖表中的介面是受控碼應用程式的一部分。

 ![程式庫和物件管理員之間的資料流程](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 若要將符號清單提供給 Visual Studio 物件管理員，您必須先呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 方法，向 Visual Studio 物件管理員註冊程式庫。 註冊程式庫之後，Visual Studio 物件管理員會要求有關程式庫功能的特定資訊。 例如，它會藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> 方法來要求程式庫旗標和支援的類別。 在某些時候，當其中一個工具要求此程式庫中的資料時，物件管理員會藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> 方法來要求最上層的符號清單。 為了回應，程式庫會製造一份符號清單，並透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> 介面將它公開給 Visual Studio 物件管理員。 @No__t_0 物件管理員會藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> 方法，判斷清單中有多少個專案。 下列所有要求都與清單中的指定專案有關，並在每個要求中提供專案索引編號。 Visual Studio 物件管理員會藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> 方法，繼續收集該專案的類型、存取範圍和其他屬性上的資訊。

 它會藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> 方法來判斷專案的名稱，並藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> 方法來要求圖示資訊。 圖示會顯示在專案名稱的左邊，並描述專案的類型、協助工具和其他屬性。

 @No__t_0 物件管理員會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> 方法，以判斷指定的清單專案是否為可擴充的，以及是否有子專案。 如果 UI 傳送要求以展開專案，物件管理員會藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> 方法來要求子符號清單。 此程式會繼續進行，並視需要建立樹狀結構的不同部分。

> [!NOTE]
> 若要執行機器碼符號提供者，請使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> 介面。

## <a name="see-also"></a>請參閱
- [如何︰使用物件管理員註冊程式庫](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [如何︰將程式庫提供的符號清單公開至物件管理員](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [如何︰識別程式庫中的符號](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)