---
title: "語言服務內容，使用提供的舊版應用程式開發介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4dbee7d2998170277369f48c3b912307d2c7e414
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>語言服務內容，使用提供的舊版應用程式開發介面
有兩個選項，以提供使用者內容中使用的語言服務[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器： 提供的文字標記的內容，或提供所有的使用者內容。 此處所述每之間的差異。  
  
 如需有關如何提供連接到您自己的編輯器語言服務內容的詳細資訊，請參閱[如何： 將內容提供編輯器](../extensibility/how-to-provide-context-for-editors.md)。  
  
## <a name="provide-text-marker-context-to-the-editor"></a>提供編輯器的文字標記內容  
 為文字標記中所指定的編譯器錯誤提供內容[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器，請實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>介面。 在此案例中，語言服務游標位於文字標記上時，才提供內容。 這可讓提供至游標處關鍵字編輯器**動態說明**視窗不含任何屬性。  
  
## <a name="provide-all-user-context-to-the-editor"></a>提供所有的使用者內容編輯器  
 如果您要建立語言服務，並使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器 中，則您可以實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>提供語言服務內容的介面。  
  
 實作`IVsLanguageContextProvider`，編輯器中，都會負責更新內容包附加的內容封包 （集合）。 當**動態說明**視窗呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A>上在閒置時，內容包此內容包介面查詢更新的編輯器。 編輯器 中，應該更新程式編輯器中，並將指標傳遞至內容屬性包，然後通知語言服務。 這是藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A>編輯器語言服務的方法。 使用內容屬性包的指標，語言服務現在新增和移除屬性和關鍵字。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>。  
  
 有兩種不同的方式實作`IVsLanguageContextProvider`:  
  
-   提供內容包關鍵字  
  
     若要更新的內容包呼叫編輯器時，傳入適當的關鍵字和屬性，然後傳回`S_OK`。 這個傳回值會指示編輯器中，以保留關鍵字和屬性的內容，而不是提供內容包在游標處關鍵字。  
  
-   取得游標的關鍵字  
  
     若要更新的內容包呼叫編輯器時，傳入適當的屬性，然後傳回`E_FAIL`。 這個傳回值會指示編輯器中，以保留您的屬性中的內容包，但更新內容屬性包中的游標處關鍵字。  
  
 下圖示範如何將內容提供語言服務實作`IVsLanguageContextProvider`。  
  
 ![LangServiceImplementation2 圖形](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
語言服務內容  
  
 您可以在圖表中，看到[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心文字編輯器有附加的內容封包。 此內容包指向三個不同的子內容包： 語言服務、 預設編輯器，以及文字標記。 語言服務及文字標記子內容包包含屬性和關鍵字，語言服務如果<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>實作介面時，以及文字標記如果<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>介面實作。 如果您不實作這些介面之一，編輯器會提供內容中的預設編輯器子內容的屬性包中的游標處關鍵字。  
  
## <a name="context-guidelines-for-editors-and-designers"></a>內容的指導方針編輯器和設計工具  
 設計工具和編輯器必須提供編輯器或設計工具視窗的一般關鍵字。 這麼做是為了讓使用者按下 F1 時，將會顯示的設計工具或編輯器的泛型，但需要的說明主題。 編輯器必須，此外，提供在資料指標目前的關鍵字或提供關鍵詞彙，根據目前的選取範圍。 這是為了確保指向說明 主題的文字或 UI 項目，或當使用者按下 F1 時，請選取顯示。 設計工具提供在設計工具中，例如在表單上按鈕的選取項目內容。 編輯器和設計工具也必須連接到語言服務中所述[舊版語言服務 Essentials](../extensibility/internals/legacy-language-service-essentials.md)。