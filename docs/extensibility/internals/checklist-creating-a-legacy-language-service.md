---
title: 檢查清單：建立舊版語言服務 |Microsoft Docs
description: 瞭解為 Visual Studio core 編輯器建立舊版語言服務所必須採取的基本步驟。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 905d81d49706c3ae5348d71c03189d6e036dd3e5
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189988"
---
# <a name="checklist-create-a-legacy-language-service"></a>檢查清單：建立舊版語言服務
下列檢查清單摘要說明為核心編輯器建立語言服務所必須採取的基本步驟 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 若要將您的語言服務整合至 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，您必須建立一個 debug 運算式評估工具。 如需詳細資訊，請參閱[Visual Studio 偵錯工具](../../extensibility/debugger/visual-studio-debugger-extensibility.md)擴充性中的[撰寫 CLR 運算式評估](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)工具。

## <a name="steps-to-create-a-language-service"></a>建立語言服務的步驟

1. 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 介面。

    - 在您的 VSPackage 中，執行 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 介面以提供語言服務。

    - 讓您的語言服務可用於整合式開發環境 (IDE) 在您的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 執行中。

2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>在主要語言服務類別中執行介面。

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>介面是核心編輯器與語言服務之間互動的起點。

### <a name="optional-features"></a>選用功能
 下列功能是選擇性的，可依任何循序執行。 這些功能會提高語言服務的功能。

- 語法標色

  實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 介面。 您應在剖析器資訊中執行此介面，以傳回適當的色彩資訊。

  方法會傳回 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 介面。 系統會為每個文字緩衝區建立個別的著色器實例，因此您應該 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 分別執行介面。 如需詳細資訊，請參閱 [舊版語言服務中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。

- 程式碼視窗

  執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 介面，讓語言服務在建立新的程式碼視窗時接收通知。

  方法會傳回 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 介面。 然後，語言服務就可以在的程式碼視窗中加入特殊的 UI <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> 。 語言服務也可以進行任何特殊處理，例如在中加入文字視圖篩選 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A> 。

- 文字視圖篩選

  若要在語言服務中提供 IntelliSense 語句完成，您必須攔截某些文字視圖會以其他方式處理的命令。 若要攔截這些命令，請完成下列步驟：

  - 實行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 以參與命令鏈並處理編輯器命令。

  - 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 方法並傳入您的 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 實作為。

  - <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A>當您從視圖卸離時呼叫方法，讓這些命令不再傳遞給您。

  必須處理的命令取決於所提供的服務。 如需詳細資訊，請參閱 [語言服務篩選的重要命令](../../extensibility/internals/important-commands-for-language-service-filters.md)。

  > [!NOTE]
  > <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>介面必須在與介面相同的物件上執行 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 。

- 陳述式完成

  實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 介面。

  支援語句完成命令 (也就是， <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) 並 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 在介面中呼叫方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ，並傳遞 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 介面。 如需詳細資訊，請參閱 [舊版語言服務中的語句完成](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)。

- 方法提示

  執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 介面以提供方法提示視窗的資料。

  安裝文字視圖篩選以適當地處理命令，讓您知道何時要顯示方法資料提示視窗。 如需詳細資訊，請參閱 [舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)。

- 錯誤標記

  實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 介面。

  建立會執行介面的錯誤標記物件， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 並呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> 方法，並傳遞 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 錯誤標記物件的介面。

  一般來說，每個錯誤標記都會在 [工作清單] 視窗中管理專案。

- 工作清單專案

  執行提供介面的工作專案類別 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> 。

  執行提供介面和介面的工作提供者類別 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> 。

  執行提供介面的工作列舉值類別 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> 。

  使用工作清單的方法註冊工作提供者 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> 。

  <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>使用服務 GUID 呼叫語言服務的服務提供者，以取得介面 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> 。

  <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> 當有新的或更新的工作時，請建立工作專案物件，並在介面中呼叫方法。

- 批註工作專案

  使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> 介面和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> 介面取得批註工作標記。

  <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>從服務取得介面 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> 。

  <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>從方法取得介面 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> 。

  執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> 介面，以接聽權杖清單中的變更。

- 大綱

  支援大綱的選項有好幾種。 例如，您可以支援 [折迭 **至定義** ] 命令、提供編輯器控制的大綱區域，或支援用戶端控制的區域。 如需詳細資訊，請參閱 [如何：在舊版語言服務中提供展開大綱支援](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)。

- 語言服務註冊

  如需如何註冊語言服務的詳細資訊，請參閱 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service2.md) 及 [管理 vspackage](../../extensibility/managing-vspackages.md)。

- 即時線上說明

  以下列其中一種方式提供編輯器的內容：

  - 藉由執行介面提供文字標記的內容 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> 。

  - 藉由執行介面來提供所有使用者內容 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> 。

## <a name="see-also"></a>另請參閱
- [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)
- [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
