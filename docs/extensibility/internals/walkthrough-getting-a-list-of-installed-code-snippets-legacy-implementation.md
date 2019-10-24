---
title: 取得已安裝程式碼片段（舊版）的清單 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 072827bbb9676ba49df5ccd69f329ea9b04c78b2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721651"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>逐步解說︰取得已安裝程式碼片段 (舊版實作) 的清單
程式碼片段是一段程式碼，可以使用功能表命令（可在已安裝的程式碼片段清單中選擇），或從 IntelliSense 完成清單中選取程式碼片段快捷方式，插入來源緩衝區。

 @No__t_0 方法會取得特定語言 GUID 的所有程式碼片段。 這些程式碼片段的快捷方式可以插入 IntelliSense 完成清單中。

 如需在 managed package framework （MPF）語言服務中執行程式碼片段的詳細資訊，請參閱[支援舊版語言服務中的程式碼片段](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)。

### <a name="to-retrieve-a-list-of-code-snippets"></a>若要取出程式碼片段清單

1. 下列程式碼顯示如何取得指定語言的程式碼片段清單。 結果會儲存在 <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> 結構的陣列中。 這個方法會使用靜態 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 方法，從 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> 服務取得 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> 介面。 不過，您也可以使用提供給 VSPackage 的服務提供者，並呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 方法。

    ```csharp
    using System;
    using System.Collections;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Package;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.TextManager.Interop;

    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service
    namespace TestLanguage
    {
        class TestLanguageService : LanguageService
        {
            private void GetSnippets(Guid languageGuid,
                                     ref ArrayList expansionsList)
            {
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));
                if (textManager != null)
                {
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;
                    if (textManager2 != null)
                    {
                        IVsExpansionManager expansionManager = null;
                        textManager2.GetExpansionManager(out expansionManager);
                        if (expansionManager != null)
                        {
                            // Tell the environment to fetch all of our snippets.
                            IVsExpansionEnumeration expansionEnumerator = null;
                            expansionManager.EnumerateExpansions(languageGuid,
                            0,     // return all info
                            null,    // return all types
                            0,     // return all types
                            1,     // include snippets without types
                            0,     // do not include duplicates
                            out expansionEnumerator);
                            if (expansionEnumerator != null)
                            {
                                // Cache our expansions in a VsExpansion array
                                uint count   = 0;
                                uint fetched = 0;
                                VsExpansion expansionInfo = new VsExpansion();
                                IntPtr[] pExpansionInfo   = new IntPtr[1];

                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));

                                expansionEnumerator.GetCount(out count);
                                for (uint i = 0; i < count; i++)
                                {
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);
                                    if (fetched > 0)
                                    {
                                        // Convert the returned blob of data into a structure that can be read in managed code.
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));

                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))
                                        {
                                            expansionsList.Add(expansionInfo);
                                        }
                                    }
                                }
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);
                            }
                        }
                    }
                }
            }
        }
    }
    ```

### <a name="to-call-the-getsnippets-method"></a>呼叫 GetSnippets 方法

1. 下列方法顯示如何在剖析作業完成時呼叫 `GetSnippets` 方法。 在以 <xref:Microsoft.VisualStudio.Package.ParseReason> 原因啟動的剖析作業之後，會呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A> 方法。

> [!NOTE]
> 基於效能考慮，會快取 `expansionsList` 陣列清單。 程式碼片段的變更不會反映在清單中，直到語言服務停止並重載為止（例如，藉由停止並重新啟動 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]）。

```csharp
class TestLanguageService : LanguageService
{
    private ArrayList expansionsList;

    public override void OnParseComplete(ParseRequest req)
    {
        if (this.expansionsList == null)
        {
            this.expansionsList = new ArrayList();
            GetSnippets(this.GetLanguageServiceGuid(),
                ref this.expansionsList);
        }
    }
}
```

### <a name="to-use-the-snippet-information"></a>使用程式碼片段資訊

1. 下列程式碼顯示如何使用 `GetSnippets` 方法所傳回的程式碼片段資訊。 會從剖析器呼叫 `AddSnippets` 方法，以回應用來填入程式碼片段清單的任何剖析原因。 這應該在第一次完成完整剖析之後才會發生。

     @No__t_0 方法會建立稍後在完成清單中顯示的宣告清單。

     @No__t_0 類別包含可以在完成清單中顯示的所有資訊，以及宣告的類型。

    ```csharp
    class TestAuthoringScope : AuthoringScope
    {
        public void AddDeclarations(TestDeclaration declaration)
        {
            if (m_declarations == null)
                m_declarations = new List<TestDeclaration>();
            m_declarations.Add(declaration);
         }
    }
    class TestDeclaration
    {
        private string m_name;
        private string m_description;
        private string m_type;

        public TestDeclaration(string name, string desc, string type)
        {
            m_name = name;
            m_description = desc;
            m_type = type;
        }

    class TestLanguageService : LanguageService
    {
        internal void AddSnippets(ref TestAuthoringScope scope)
        {
            if (this.expansionsList != null && this.expansionsList.Count > 0)
            {
                int count = this.expansionsList.Count;
                for (int i = 0; i < count; i++)
                {
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,
                         expansionInfo.description,
                         "snippet"));
                }
            }
        }
    }

    ```

## <a name="see-also"></a>請參閱
- [舊版語言服務中對程式碼片段的支援](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)