---
title: 檢查清單︰ 建立舊版語言服務 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d45ad596b3aaea97773eb06b2e853d6c628ca97
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816653"
---
# <a name="checklist-creating-a-legacy-language-service"></a>檢查清單︰建立舊版語言服務
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

下列檢查清單摘要說明您必須採取才能建立語言服務的基本步驟[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]核心編輯器。 若要整合到您的語言服務[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]，您必須建立偵錯運算式評估工具。 如需詳細資訊，請參閱 <<c0> [ 撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)中[Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)。  
  
## <a name="steps-for-creating-a-language-service"></a>建立語言服務的步驟  
  
1.  實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 介面。  
  
    -   在 VSPackage，實作<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>介面，以提供語言服務。  
  
    -   提供整合式的開發環境 (IDE)，以在您的語言服務您<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>實作。  
  
2.  實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>主要語言服務類別中的介面。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>介面是核心編輯器和語言服務之間互動的起點。  
  
### <a name="optional-features"></a>選用功能  
 下列功能是選擇性的而且可以實作以任何順序。 這些功能會增加您的語言服務的功能。  
  
- 語法標色  
  
   實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 介面。 此介面的實作應該傳回適當的色彩資訊的剖析器資訊。  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>方法會傳回<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>介面。 因此，您應該實作針對每個文字緩衝區，建立不同的色彩標示器執行個體<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>個別介面。 如需詳細資訊，請參閱 <<c0> [ 語法著色舊版語言服務中](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。  
  
- 程式碼視窗  
  
   實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>介面，可讓語言服務，以接收通知時建立新的程式碼視窗。  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>方法會傳回<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>介面。 語言服務接著可以新增至程式碼 視窗中的特殊 UI <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>。 語言服務也可以執行任何特殊處理，例如新增文字檢視篩選器中的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>。  
  
- 文字檢視篩選條件  
  
   若要提供語言服務中的完成 IntelliSense 陳述式，您必須攔截一些文字檢視會處理命令。 若要攔截這些命令，完成下列步驟：  
  
  - 實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>參與命令鏈結並處理編輯器命令。  
  
  - 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法並傳入您<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>實作。  
  
  - 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A>方法，當您中斷連結從檢視使這些命令不會再傳送給您。  
  
    必須處理的命令取決於所提供的服務。 如需詳細資訊，請參閱 <<c0> [ 語言服務篩選器的重要命令](../../extensibility/internals/important-commands-for-language-service-filters.md)。  
  
  > [!NOTE]
  >  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>介面必須實作的相同物件上<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。  
  
- 陳述式完成  
  
   實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 介面。  
  
   支援的陳述式完成命令 (也就是<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>)，並呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>方法中的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>介面，並傳遞<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>介面。 如需詳細資訊，請參閱 <<c0> [ 舊版語言服務中的陳述式完成](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)。  
  
- 方法秘訣  
  
   實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>以提供資料給方法提示視窗的介面。  
  
   安裝適當地處理命令文字檢視篩選條件，讓您知道何時要顯示方法的資料提示視窗。 如需詳細資訊，請參閱 <<c0> [ 舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)。  
  
- 錯誤標記  
  
   實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 介面。  
  
   建立錯誤標記物件，可實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面並呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>方法，傳遞<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>錯誤標記物件的介面。  
  
   通常每個錯誤標記會管理 [工作清單] 視窗中的項目。  
  
- 工作清單項目  
  
   實作工作項目類別提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem>介面。  
  
   實作工作提供者類別提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider>介面和<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>介面。  
  
   實作工作列舉值類別提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems>介面。  
  
   向工作清單中的工作提供者<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A>方法。  
  
   取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>藉由呼叫的服務 GUID 的語言服務的服務提供者介面<xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>。  
  
   建立工作項目物件並呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A>方法中的<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>介面時新增或更新工作。  
  
- 註解工作項目  
  
   使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>介面和<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>介面，以取得註解工作語彙基元。  
  
   取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>介面從<xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>服務。  
  
   取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>介面從<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A>方法。  
  
   實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents>接聽的變更在語彙基元清單中的介面。  
  
- 大綱  
  
   有數個選項，以支援大綱。 例如，您可以支援**摺疊至定義**命令，請提供編輯器控制項的大綱區域，或支援用戶端控制的區域。 如需詳細資訊，請參閱 <<c0> [ 如何： 提供展開大綱中的支援舊版語言服務](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)。  
  
- 語言服務登錄  
  
   如需如何註冊語言服務的詳細資訊，請參閱[註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service2.md)並[管理 Vspackage](../../extensibility/managing-vspackages.md)。  
  
- 即時線上說明  
  
   提供至編輯器的內容，在下列方面：  
  
  -   提供文字標記的內容，方法是實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>介面。  
  
  提供所有的使用者內容，方法是實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>介面。  
  
## <a name="see-also"></a>另請參閱  
 [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

