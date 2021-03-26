---
title: 取得已安裝的程式碼片段清單 (舊版) |Microsoft Docs
description: 瞭解如何取得特定語言 GUID 的所有程式碼片段。 這些程式碼片段的快捷方式可以插入 IntelliSense 完成清單中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5f94d481a2884c64cb42b170d9d1abfa25c913a9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069136"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>逐步解說：取得已安裝的程式碼片段 (舊版實作) 清單
程式碼片段是一段程式碼，可以使用功能表命令 (可插入來源緩衝區，讓您可以選擇) 的已安裝程式碼片段清單，或從 IntelliSense 完成清單中選取程式碼片段快捷方式。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A>方法會取得特定語言 GUID 的所有程式碼片段。 這些程式碼片段的快捷方式可以插入 IntelliSense 完成清單中。

 請參閱 [舊版語言服務中的程式碼片段支援](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md) ，以取得在 managed package FRAMEWORK (MPF) Language Service 中執行程式碼片段的詳細資料。

### <a name="to-retrieve-a-list-of-code-snippets"></a>若要取得程式碼片段的清單

1. 下列程式碼示範如何取得指定語言的程式碼片段清單。 結果會儲存在結構陣列中 <xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion> 。 這個方法會使用靜態 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> 從服務取得介面 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> 。 不過，您也可以使用提供給 VSPackage 的服務提供者，並呼叫 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 方法。

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

### <a name="to-call-the-getsnippets-method"></a>若要呼叫 GetSnippets 方法

1. 下列方法顯示如何 `GetSnippets` 在剖析作業完成時呼叫方法。 <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A>方法是在使用原因啟動剖析作業之後呼叫 <xref:Microsoft.VisualStudio.Package.ParseReason> 。

> [!NOTE]
> 基於 `expansionsList` 效能考慮，會快取陣列清單。 程式碼段的變更不會反映在清單中，直到語言服務停止並重載 (例如，藉由停止和重新開機 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) 。

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

1. 下列程式碼顯示如何使用方法所傳回的程式碼片段資訊 `GetSnippets` 。 `AddSnippets`方法是從剖析器呼叫，以回應用來填入程式碼片段清單的任何剖析原因。 這應該會在第一次完成完整剖析之後進行。

     `AddDeclaration`方法會建立稍後在完成清單中顯示的宣告清單。

     `TestDeclaration`類別包含可在完成清單中顯示的所有資訊，以及宣告的類型。

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

## <a name="see-also"></a>另請參閱
- [舊版語言服務中對程式碼片段的支援](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)
