---
title: 支援符號瀏覽工具 |微軟文件
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4998e47ccd6f99df2710833c18975d57e3bb92f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704772"
---
# <a name="supporting-symbol-browsing-tools"></a>支援符號瀏覽工具
**物件瀏覽器**、**類別檢視**、**除錯瀏覽器**與**尋找符號結果**工具在可視化工作室中提供符號流覽功能。 這些工具顯示符號的分層樹檢視,並顯示樹中符號之間的關係。 符號可以表示命名空間、物件、類、類成員和各種元件中包含的其他語言元素。 這些元件包括 Visual Studio 專案、外部 .NET 框架元件和類型 (.tlb) 庫。 有關詳細資訊,請參閱[檢視程式碼的結構](../../ide/viewing-the-structure-of-code.md)。

## <a name="symbol-browsing-libraries"></a>符號流覽庫
 作為語言實現者,您可以通過創建跟蹤元件中的符號的庫,並通過一組介面向 Visual Studio 物件管理器提供符號清單來擴展 Visual Studio 符號流覽功能。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2>介面描述了庫。 Visual Studio 物件管理員通過從庫中獲取數據並組織數據來回應從符號流覽工具中獲取新數據的請求。 隨後,它將使用請求的數據填充或更新工具。 要獲取對 Visual Studio 物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>管理員的<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager>引用,`GetService`將服務 ID 傳遞給方法。

 每個庫都必須向 Visual Studio 物件管理器註冊,該管理器收集所有庫的資訊。 要註冊庫,請調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>方法。 根據啟動請求的工具,Visual Studio 物件管理員會查找相應的庫並請求數據。 數據在<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>介面描述的符號清單中在庫和[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]物件管理器之間傳輸。

 物件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]管理員負責定期刷新符號流覽工具,以反映庫中包含的最最新數據。

 下圖包含庫和 Visual Studio 物件管理員之間的請求/資料交換過程的關鍵元素範例。 關係圖中的介面是託管代碼應用程式的一部分。

 ![程式庫和物件管理員之間的資料流程](../../extensibility/internals/media/callbrowserdiagram.gif "通話瀏覽器圖")

 要向 Visual Studio 物件管理員提供符號清單,必須首先<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>透過呼叫方法將庫註冊到 Visual Studio 物件管理員。 註冊庫後,Visual Studio 物件管理員會請求有關庫功能的某些資訊。 例如,它通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A>方法請求庫標誌和支援的類別。 在某些時候,當其中一個工具請求來自此庫的數據時,物件管理器通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A>方法請求符號的頂級清單。 作為回應,庫會創建符號清單,並通過<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>介面將其公開給 Visual Studio 物件管理器。 物件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]管理員通過調<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A>用 方法確定清單中有多少項。 以下所有請求都與清單中的給定項相關,並在每個請求中提供物料索引編號。 Visual Studio 物件管理員繼續通過<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A>調用 方法收集有關項的類型、可存取性和其他屬性的資訊。

 它透過呼叫方法確定的名稱,<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A>並透過呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A>方法請求圖示資訊。 圖示顯示在專案名稱的左側,並描述項的類型、輔助功能和其他屬性。

 物件[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]管理員調<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A>用 方法以確定給定清單項是否可展開,並且具有子項。 如果 UI 發送延伸元素的請求,物件管理員透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A>呼叫方法請求符號的子清單。 該過程繼續,樹的不同部分正在按需構建。

> [!NOTE]
> 要實現本機代碼符號提供程式,請使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2>介面。

## <a name="see-also"></a>另請參閱
- [如何︰使用物件管理員註冊程式庫](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [如何︰將程式庫提供的符號清單公開至物件管理員](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [如何︰識別程式庫中的符號](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
