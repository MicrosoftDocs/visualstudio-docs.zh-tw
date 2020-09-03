---
title: 使用舊版 API 提供語言服務內容 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4471b71b612008ba7d0733c92286415cd3c3f6b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193857"
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>使用舊版 API 提供語言服務內容
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

有兩個選項可供語言服務使用核心編輯器來提供使用者內容 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ：提供文字標記內容，或提供所有使用者內容。 這兩者之間的差異如下所述。  
  
 如需有關將內容提供給連接到您專屬編輯器之語言服務的詳細資訊，請參閱 how [to：提供編輯器的內容](../extensibility/how-to-provide-context-for-editors.md)。  
  
## <a name="provide-text-marker-context-to-the-editor"></a>提供文本標記內容給編輯器  
 若要為核心編輯器中的文字標記所指定的編譯器錯誤提供內容 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ，請執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> 介面。 在此案例中，語言服務只會在資料指標位於文字標記時提供內容。 這可讓編輯器將游標處的關鍵字提供給 **動態** 說明視窗，而不含任何屬性。  
  
## <a name="provide-all-user-context-to-the-editor"></a>將所有使用者內容提供給編輯器  
 如果您要建立語言服務，並使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 核心編輯器，則可以執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> 介面以提供語言服務的內容。  
  
 在的執行 `IVsLanguageContextProvider` 中，會將內容包 (集合) 附加至編輯器，以負責更新內容包。 當 **動態** 說明視窗 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> 在閒置時間呼叫此內容包上的介面時，內容包會查詢編輯器以取得更新。 編輯器接著會通知語言服務應該更新編輯器，並傳遞內容包的指標。 這是藉由 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> 從編輯器呼叫語言服務的方法來完成。 使用內容包的指標，語言服務現在可以加入和移除屬性和關鍵字。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>。  
  
 有兩種不同的方法可以實現 `IVsLanguageContextProvider` ：  
  
- 提供關鍵字給內容包  
  
   當呼叫編輯器來更新內容包時，請傳入適當的關鍵字和屬性，然後再返回 `S_OK` 。 這個傳回值會指示編輯器保留您的關鍵字和屬性內容，而不是在資料指標上提供關鍵字給內容包。  
  
- 從資料指標的關鍵字取得關鍵字  
  
   當呼叫編輯器來更新內容包時，請傳入適當的屬性，然後再返回 `E_FAIL` 。 這個傳回值會指示編輯器將屬性保留在內容包中，但在游標處使用關鍵字來更新內容包。  
  
  下圖將示範如何為執行的語言服務提供內容 `IVsLanguageContextProvider` 。  
  
  ![LangServiceImplementation2 圖形](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
  語言服務的內容  
  
  如圖中所示， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 核心文字編輯器已附加內容包。 此內容包指向三個不同的子節點包：語言服務、預設編輯器和文字標記。 語言服務和文字標記的子內容包包含語言服務的屬性和關鍵字（如果 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> 已實作為介面），以及如果介面已實作為文字標記 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> 。 如果您未執行這些介面的任一個，則編輯器會在預設編輯器的子上下文包中，于游標處提供關鍵字的內容。  
  
## <a name="context-guidelines-for-editors-and-designers"></a>編輯器和設計工具的內容指導方針  
 設計工具和編輯器必須提供編輯器或設計工具視窗的一般關鍵字。 這樣做的目的是要讓設計工具或編輯器在使用者按下 F1 時顯示一般但適當的說明主題。 除了這個以外，編輯器還必須在游標處提供目前的關鍵字，或根據目前的選取專案提供索引鍵字詞。 這樣做的目的是要確保當使用者按下 F1 時，會顯示指向或選取之文字或 UI 元素的說明主題。 設計工具會提供在設計工具中選取之專案的內容，例如表單上的按鈕。 編輯器和設計工具也必須連接到語言服務，如 [舊版語言服務基本](../extensibility/internals/legacy-language-service-essentials.md)版所述。
