---
title: 逐步解說：取得一份已安裝的程式碼片段 （舊版實作） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef16552fbbb051a24d7b2e1fbe5b5266774ef13f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941637"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>逐步解說：取得已安裝的程式碼片段 (舊版實作) 清單
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

程式碼片段是一種程式碼，可以插入來源緩衝區 （可讓選擇的一份已安裝的程式碼片段） 的功能表命令或藉由從 IntelliSense 完成清單中選取的程式碼片段捷徑。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A>方法會取得所有的程式碼片段，針對特定語言的 GUID。 這些程式碼片段的捷徑可以插入的 IntelliSense 完成清單。  
  
 請參閱[舊版語言服務中的程式碼片段支援](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)的 managed 的封裝架構 (MPF) 語言服務中執行程式碼片段的相關詳細資料。  
  
### <a name="to-retrieve-a-list-of-code-snippets"></a>若要擷取的程式碼片段清單  
  
1.  下列程式碼示範如何取得給定語言的程式碼片段的清單。 結果會儲存在陣列<xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion>結構。 這個方法會使用靜態<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法來取得<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>介面從<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>服務。 不過，您也可以使用服務提供者提供給您的 VSPackage 和呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>方法。  
  
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
  
1.  下列方法示範如何呼叫`GetSnippets`方法的剖析作業中完成。 <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A>方法的剖析作業中所啟動的原因之後呼叫<xref:Microsoft.VisualStudio.Package.ParseReason>。  
  
> [!NOTE]
>  `expansionsList`陣列 listis 基於效能考量快取。 程式碼片段的變更才會反映清單中的語言服務停止並重新載入 (例如，藉由停止再重新開始[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)])。  
  
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
  
### <a name="to-use-the-snippet-information"></a>若要使用的程式碼片段資訊  
  
1.  下列程式碼示範如何使用傳回的程式碼片段資訊`GetSnippets`方法。 `AddSnippets`回應任何剖析的原因，用來填入程式碼片段的清單中的剖析器呼叫方法。 這應該之後進行完整的剖析作業完成第一次。  
  
     `AddDeclaration`方法建置之後顯示完成清單中宣告的清單。  
  
     `TestDeclaration`類別包含可以顯示完成清單，以及宣告的型別中的所有資訊。  
  
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
 [舊版語言服務中對程式碼片段的支援](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)
