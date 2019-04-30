---
title: 使用舊版 API 提供的語言服務內容 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 66e8da821657dc1aefd8563f3826891cb75e1792
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62805960"
---
# <a name="provide-a-language-service-context-by-using-the-legacy-api"></a>使用舊版 API 提供的語言服務內容
有兩個選項，以提供使用者內容中使用的語言服務[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器： 提供文字標記的內容，或提供所有的使用者內容。 此處所述的每個之間的差異。

 如需有關如何提供連接到您自己的編輯器語言服務內容的詳細資訊，請參閱[How to:編輯器提供內容](../extensibility/how-to-provide-context-for-editors.md)。

## <a name="provide-text-marker-context-to-the-editor"></a>編輯器提供文字標記的內容
 若要提供的內容中的文字標記所指定的編譯器錯誤[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器，請實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>介面。 在此案例中，語言服務會提供內容，僅當游標位於文字標記。 這可讓編輯器提供至游標處關鍵字**動態說明**不含任何屬性 視窗。

## <a name="provide-all-user-context-to-the-editor"></a>提供所有的使用者內容編輯器
 如果您要建立語言服務，並使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器中，則您可以實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>介面，以針對您的語言服務提供的內容。

 實作的`IVsLanguageContextProvider`，內容封包 （集合） 會附加至編輯器中，也就是負責更新的內容封包。 當**動態說明**視窗呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A>介面上的閒置時間，內容包在此內容包查詢更新的編輯器。 編輯器會在它應該更新編輯器，並將指標傳遞至內容包，然後通知語言服務。 這是藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A>編輯器語言服務的方法。 使用的內容封包的指標，語言服務現在新增和移除屬性和關鍵字。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>。

 有兩種不同的方式來實作`IVsLanguageContextProvider`:

- 提供的內容封包的關鍵字

   若要更新的內容封包呼叫編輯器時，傳入適當的關鍵字和屬性，然後傳回`S_OK`。 這個傳回值會指示要保留關鍵字和屬性的內容，而不是提供的內容封包至游標處關鍵字的編輯器。

- 取得關鍵字的關鍵字，在游標處

   若要更新的內容封包呼叫編輯器時，傳入適當的屬性，然後傳回`E_FAIL`。 這個傳回值會指示要保留您的屬性中的內容封包，但更新的內容封包中的游標處關鍵字編輯器。

  下圖說明如何提供內容實作的語言服務以`IVsLanguageContextProvider`。

  ![LangServiceImplementation2 圖形](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")語言服務內容

  您可以在圖表中，看到[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心文字編輯器有內容包附加到它。 此內容包指向三個不同的子內容包： 語言服務，預設的編輯器與文字標記。 語言標記優先型服務和文字袋包含屬性和關鍵字的語言服務如果<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>介面實作，以及文字標記如果<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>介面的實作。 如果您不實作這些介面，編輯器會提供內容的預設編輯器子內容封包中的資料指標在關鍵字。

## <a name="context-guidelines-for-editors-and-designers"></a>內容的指導方針編輯器和設計工具
 設計工具和編輯器，必須提供的編輯器或設計工具視窗的一般關鍵字。 這麼做為了讓使用者按下時，將會顯示的設計工具或編輯器的泛型，但需要的說明主題**F1**。 編輯器必須，此外，提供在資料指標目前的關鍵字或提供關鍵詞彙，根據目前的選取項目。 這為了確保指向說明主題的文字或 UI 項目，或當使用者按下時，請選取顯示**F1**。 設計工具提供在設計工具，例如在表單上按鈕的選取項目內容。 編輯器和設計工具也必須連接到語言服務中所述[舊版語言服務的基本資訊](../extensibility/internals/legacy-language-service-essentials.md)。