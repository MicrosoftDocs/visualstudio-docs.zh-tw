---
title: 支援 Symbol-Browsing 工具 |Microsoft Docs
description: Visual Studio 在 Visual Studio 中提供符號流覽功能。 瞭解如何使用元件的程式庫擴充這些功能，以取得元件中的符號。
ms.custom: SEO-VS-2020
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d54f56ae3bc5fd5956f67400d84edfd4c8c9e55c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080563"
---
# <a name="supporting-symbol-browsing-tools"></a>支援符號瀏覽工具
**物件瀏覽器**、 **類別檢視**、 **呼叫瀏覽器** 和 **尋找符號結果** 工具提供 Visual Studio 中的符號流覽功能。 這些工具會顯示符號的階層式樹狀檢視，並顯示樹狀結構中符號之間的關聯性。 這些符號可能表示命名空間、物件、類別、類別成員，以及各種元件中所含的其他語言元素。 元件包含 Visual Studio 專案、外部 .NET Framework 元件和類型 ( .tlb) 程式庫。 如需詳細資訊，請參閱 [查看程式碼的結構](../../ide/viewing-the-structure-of-code.md)。

## <a name="symbol-browsing-libraries"></a>Symbol-Browsing 程式庫
 您可以藉由建立可追蹤元件中符號的程式庫，並透過一組介面將符號清單提供給 Visual Studio 物件管理員，來擴充 Visual Studio 的符號流覽功能。 程式庫是由介面描述 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> 。 Visual Studio 物件管理員會從程式庫取得資料並加以組織，以回應來自符號流覽工具的新資料要求。 接著，它會以要求的資料填入或更新工具。 若要取得 Visual Studio 物件管理員的參考， <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> 請將 <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> 服務識別碼傳遞給 `GetService` 方法。

 每個程式庫都必須向 Visual Studio 物件管理員註冊，這會收集所有程式庫的資訊。 若要註冊程式庫，請呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 方法。 根據啟動要求的工具而定，Visual Studio 物件管理員會尋找適當的程式庫並要求資料。 資料在程式庫和物件管理員之間，會 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 在介面所描述的符號清單中移動 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> 。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員負責定期重新整理符號流覽工具，以反映包含在程式庫中的最新資料。

 下圖包含程式庫和 Visual Studio 物件管理員之間要求/資料交換程式的重要元素範例。 圖中的介面是 managed 程式碼應用程式的一部分。

 ![程式庫和物件管理員之間的資料流程](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 若要將符號清單提供給 Visual Studio 物件管理員，您必須先呼叫方法，以 Visual Studio 物件管理員註冊程式庫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 。 註冊程式庫之後，Visual Studio 物件管理員會要求有關程式庫功能的特定資訊。 例如，它會藉由呼叫和方法來要求程式庫旗標和支援的類別 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> 。 在某個時間點，當其中一個工具要求這個程式庫的資料時，物件管理員會藉由呼叫方法來要求最上層的符號清單 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> 。 在回應中，程式庫會製造符號清單，並透過介面將其公開給 Visual Studio 的物件管理員 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> 。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員會藉由呼叫方法來判斷清單中有多少專案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> 。 下列所有要求都與清單中的指定專案相關，並在每個要求中提供專案索引編號。 Visual Studio 物件管理員會藉由呼叫方法，繼續收集項目的類型、存取範圍和其他屬性的資訊 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> 。

 它會藉由呼叫方法來判斷專案的名稱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> ，並藉由呼叫方法來要求圖示資訊 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> 。 此圖示會顯示在專案名稱的左邊，並描述專案的類型、存取範圍和其他屬性。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理員 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> 會呼叫方法來判斷指定的清單專案是否可展開，以及是否有子專案。 如果 UI 傳送要求以展開專案，物件管理員會藉由呼叫方法來要求子符號的子清單 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> 。 此程式會繼續根據需求建立樹狀結構的不同部分。

> [!NOTE]
> 若要執行原生程式碼符號提供者，請使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> 介面。

## <a name="see-also"></a>另請參閱
- [如何︰使用物件管理員註冊程式庫](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [如何︰將程式庫提供的符號清單公開至物件管理員](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [如何︰識別程式庫中的符號](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
