---
title: "取得一份已安裝的程式碼片段 （舊版） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 50d5343d98bba8df79628d9bfdfa838aea9e27d8
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>逐步解說： 取得一份已安裝的程式碼片段 （舊版實作）
程式碼片段是一段程式碼，可以插入來源緩衝區 （可選擇安裝的程式碼片段的清單） 的功能表命令或藉由從 IntelliSense 完成清單中選取程式碼片段捷徑。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A>方法會取得特定語言 GUID 的所有程式碼片段。 這些程式碼片段的捷徑可以插入 IntelliSense 完成清單。  
  
 請參閱[舊版語言服務的程式碼片段支援](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)如需在 managed 的封裝架構 (MPF) 語言服務中實作程式碼片段詳細資訊。  
  
### <a name="to-retrieve-a-list-of-code-snippets"></a>若要擷取的程式碼片段的清單  
  
1.  下列程式碼會示範如何取得給定語言的程式碼片段的清單。 結果會儲存在陣列<xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion>結構。 這個方法會使用靜態<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>方法來取得<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>介面從<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>服務。 不過，您也可以使用提供給您的 VSPackage 和呼叫的服務提供者<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>方法。  
  
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
  
1.  下列方法示範如何呼叫`GetSnippets`在剖析作業完成的方法。 <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A>方法呼叫後已啟動，且原因的剖析作業<xref:Microsoft.VisualStudio.Package.ParseReason>。  
  
> [!NOTE]
>  `expansionsList`陣列 listis 快取，基於效能的考量。 程式碼片段的變更才會反映在清單中停止並重新載入語言服務 (例如，藉由停止再重新開始[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)])。  
  
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
  
1.  下列程式碼示範如何使用所傳回的程式碼片段資訊`GetSnippets`方法。 `AddSnippets`方法從回應剖析因故，用來填入的程式碼片段的清單中的剖析器呼叫。 完整剖析已完成第一次後，這就會發生。  
  
     `AddDeclaration`方法會建立稍後會顯示完成清單中宣告的清單。  
  
     `TestDeclaration`類別包含所有可以顯示完成清單與宣告的型別中的資訊。  
  
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
