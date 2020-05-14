---
title: 清單:創建傳統語言服務 |微軟文件
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
ms.openlocfilehash: 11785dab63cbb6a95ab2d34c5edbfb4525ebf34c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709781"
---
# <a name="checklist-create-a-legacy-language-service"></a>檢查表:建立舊語言服務
以下檢查表總結了為[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]核心編輯器創建語言服務必須執行的基本步驟。 要將語言服務整合到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中,必須創建調試表達式賦值器。 有關詳細資訊,請參閱在[可視化工作室調試器擴展中](../../extensibility/debugger/visual-studio-debugger-extensibility.md)[編寫 CLR 運算式賦值](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)器 。

## <a name="steps-to-create-a-language-service"></a>建立語言服務的步驟

1. 實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 介面。

    - 在 VSPackage<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>中, 實現介面以提供語言服務。

    - 使語言服務可用於<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>實現中的整合式開發環境 (IDE)。

2. 在<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>主語言服務類中實現介面。

     介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>是核心編輯器與語言服務之間交互的起點。

### <a name="optional-features"></a>選用功能
 以下功能是可選的,可以按任意順序實現。 這些功能增加了語言服務的功能。

- 語法標色

  實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 介面。 此介面的實現應解析器資訊返回相應的顏色資訊。

  該方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>傳<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>回介面 。 為每個文本緩衝區創建單獨的著色器實例,因此應單獨實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>介面。 有關詳細資訊,請參閱[舊語言服務 中的語法著色](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。

- 程式碼視窗

  實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>介面,使語言服務能夠接收創建新代碼視窗的通知。

  該方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>傳<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>回介面 。 然後,語言服務可以將特殊 UI 添加<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>到中的代碼視窗。 語言服務還可以執行任何特殊處理,例如在中<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>添加文本視圖篩選器。

- 文字檢視篩選器

  要在語言服務中提供 IntelliSense 語句完成,必須攔截文本檢視將處理的某些命令。 要攔截這些命令,完成以下步驟:

  - 實現<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>參與命令鏈和處理編輯器命令。

  - 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法並傳遞實<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>作 。

  - 從檢視<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A>分離時調用 方法,以便不再將這些命令傳遞給您。

  必須處理的命令取決於提供的服務。 有關詳細資訊,請參閱[語言服務篩選器的重要命令](../../extensibility/internals/important-commands-for-language-service-filters.md)。

  > [!NOTE]
  > 介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>必須在與<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面相同的對象上實現。

- 陳述式完成

  實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 介面。

  支援語句<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>完成命令 (即<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A><xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>),並在介面中調用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>方法,傳遞介面。 有關詳細資訊,請參閱[舊語言服務中的語句完成](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)。

- 方法提示

  實現介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>以提供方法提示窗口的數據。

  安裝文字檢視篩選器以適當地處理命令,以便知道何時顯示方法數據提示視窗。 有關詳細資訊,請參閱[舊語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)。

- 錯誤標記

  實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 介面。

  創建實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面並調<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>用 方法的錯誤標記物件,傳遞錯誤標記<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>對象的介面。

  通常,每個錯誤標記都會管理任務列表視窗中的項。

- 工作清單項目

  實現提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem>介面的任務項類。

  實現提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider>介面和<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>介面的任務提供程式類。

  實現提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems>介面的任務枚舉器類。

  使用任務清單<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A>的方法註冊任務提供程式。

  通過使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>服務GUID<xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>調用語言服務的服務提供者來獲取介面。

  建立新任務或更新的任務時,<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A>建立工作<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>項 物件並在介面中調用 方法。

- 註解工作項目

  使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>介面和<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>介面獲取註釋任務權杖。

  從服務<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo><xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>獲取介面。

  從<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens><xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A>方法獲取介面。

  實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents>介面以偵聽權杖清單中的更改。

- 大綱

  有幾個選項可用於支援大綱。 例如,可以支援 **「摺疊到定義」** 命令、提供編輯器控制的大綱區域或支援用戶端控制的區域。 有關詳細資訊,請參閱[:在舊語言服務中提供擴展的大綱支援](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)。

- 語言服務註冊

  有關如何註冊語言服務的詳細資訊,請參閱[註冊舊語言服務](../../extensibility/internals/registering-a-legacy-language-service2.md)[和管理 VSPackages](../../extensibility/managing-vspackages.md)。

- 內容相依說明

  以下欄方式之一向編輯器提供上下文:

  - 通過實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>介面為文本標記提供上下文。

  - 通過實現介面提供<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>所有使用者上下文。

## <a name="see-also"></a>另請參閱
- [開發傳統語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)
- [編寫 CLR 表示式賦值器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
