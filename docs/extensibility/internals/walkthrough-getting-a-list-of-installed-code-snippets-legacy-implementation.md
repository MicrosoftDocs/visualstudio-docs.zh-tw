---
title: 取得已安裝的代碼段清單(舊代碼段) |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3d5ef857973555c4b2d201f98957bd2c39328b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703645"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>逐步解說︰取得已安裝程式碼片段 (舊版實作) 的清單
代碼段是一段代碼,可以使用菜單命令(允許在已安裝的代碼段清單中選擇)或從 IntelliSense 完成清單中選擇代碼段快捷方式,插入到源緩衝區中。

 該方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A>獲取特定語言 GUID 的所有代碼段。 這些程式碼段的快捷方式可以插入到 IntelliSense 完成清單中。

 有關在託管套件架構 (MPF) 語言服務中實現代碼段的詳細資訊,請參閱[舊語言服務中對程式碼段的支援](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)。

### <a name="to-retrieve-a-list-of-code-snippets"></a>檢索程式清單

1. 以下代碼演示如何獲取給定語言的代碼段清單。 結果儲存在結構陣列中<xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion>。 此方法使用靜態<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager><xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>從 服務獲取介面。 但是,您也可以使用提供給 VSPackage 的服務提供者並<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>調用 方法。

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

1. 以下方法演示如何在分析操作完成時`GetSnippets`調用該方法。 該方法<xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A>是在分析操作後呼叫的,該分析操作是啟動<xref:Microsoft.VisualStudio.Package.ParseReason>的原因 。

> [!NOTE]
> 出於`expansionsList`性能原因緩存陣列清單。 在停止並重新載入語言服務(例如,透過停止和重新啟動[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)])之前,對代碼段的更改不會反映在清單中。

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

### <a name="to-use-the-snippet-information"></a>使用代碼欄位資訊

1. 以下代碼演示如何使用`GetSnippets`方法返回的代碼段資訊。 該方法`AddSnippets`從解析器調用,以回應用於填充代碼段清單的任何分析原因。 這應該在首次完成完整分析後進行。

     該方法`AddDeclaration`生成一個聲明清單,該清單稍後顯示在完成清單中。

     該`TestDeclaration`類包含可在完成清單中顯示的所有資訊以及聲明類型。

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
