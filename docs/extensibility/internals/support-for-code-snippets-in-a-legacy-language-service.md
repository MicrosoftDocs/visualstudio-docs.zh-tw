---
title: "在舊版語言服務中的程式碼片段的支援 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式碼片段，支援的語言服務"
  - "程式碼片段，支援的語言服務 [受管理的封裝 framework]"
  - "支援的程式碼片段的語言服務 [受管理的封裝 framework]"
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# 在舊版語言服務中的程式碼片段的支援
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

程式碼片段是一段程式碼插入至原始程式檔。 程式碼片段本身是以 XML 為基礎的範本，內含一組欄位。 程式碼片段插入後可以有不同的值，根據在其中插入程式碼片段的內容，會反白顯示這些欄位。 立即插入程式碼片段後，語言服務可以格式化程式碼片段。  
  
 允許的欄位來使用 TAB 鍵巡覽程式碼片段的特殊的編輯模式中，插入程式碼片段。 欄位可以支援 IntelliSense 樣式下拉式功能表。 使用者認可到原始程式檔中程式碼片段輸入 ENTER 或 ESC 鍵。 若要深入了解程式碼片段，請參閱 [程式碼片段](../../ide/code-snippets.md)。  
  
 舊版的語言服務會實作成，VSPackage 的一部分，但實作語言服務功能的較新的方法是使用 MEF 延伸模組。 若要深入了解，請參閱 [逐步解說: 實作程式碼片段](../../extensibility/walkthrough-implementing-code-snippets.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會改善語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## Managed 程式碼片段的封裝 Framework 支援  
 受管理的封裝架構 \(MPF\) 支援大多數的程式碼片段功能，從讀取要插入程式碼片段的範本，並啟用特殊編輯模式。 支援透過管理 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 類別。  
  
 當 <xref:Microsoft.VisualStudio.Package.Source> 類別具現化， <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> 方法中的 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別呼叫以取得 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 物件 \(請注意，基底 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別一律會傳回新 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 物件給每個 <xref:Microsoft.VisualStudio.Package.Source> 物件\)。  
  
 MPF 不支援擴充函式。 擴充函式是內嵌在程式碼片段範本，並傳回放置在欄位中的一個或多個值的具名函式。 值會傳回所用的語言服務本身透過 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 物件。<xref:Microsoft.VisualStudio.Package.ExpansionFunction> 物件必須實作以支援擴充函式語言服務。  
  
## 提供支援的程式碼片段  
 若要啟用的程式碼片段支援，您必須提供，或安裝程式碼片段，您必須提供使用者將這些程式碼片段的方式。 有三個步驟來啟用程式碼片段的支援 ︰  
  
1.  安裝程式碼片段檔案。  
  
2.  啟用程式碼片段的語言服務。  
  
3.  叫用 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 物件。  
  
### 安裝程式碼片段檔案  
 所有的程式碼片段的語言會儲存為 XML 檔案中的範本通常一個程式碼片段範本每個檔案。 如需用於程式碼片段範本的 XML 結構描述的詳細資訊，請參閱 [程式碼片段結構描述參考](../../ide/code-snippets-schema-reference.md)。 識別每個程式碼片段範本的語言 id。 這個語言識別碼指定在登錄中，並置入 `Language` \< 代碼 \> 標記在範本中的屬性。  
  
 通常有兩個程式碼片段範本檔案儲存所在的位置 ︰ 1） 將您的語言已安裝而 2） 使用者的資料夾中。 這些位置會新增至登錄因此，Visual Studio **程式碼片段管理員** 可以尋找程式碼片段。 使用者的資料夾是由使用者所建立的程式碼片段的儲存位置。  
  
 已安裝的程式碼片段範本檔案的典型資料夾配置看起來像這樣 ︰ *\[InstallRoot\]*\\*\[TestLanguage\]*\\Snippets\\*\[LCID\]*\\Snippets。  
  
 *\[InstallRoot\]* 是安裝在您的語言的資料夾。  
  
 *\[TestLanguage\]* 是您的語言與資料夾名稱的名稱。  
  
 *\[LCID\]* 是地區設定識別碼。 這是如何當地語系化的版本的程式碼片段會儲存。 例如，英文的地區設定識別碼是 1033，所以 *\[LCID\]* 1033年取代。  
  
 必須提供一個額外的檔案，而這是一個索引的檔案，通常稱為 SnippetsIndex.xml 或 ExpansionsIndex.xml （您可以使用任何有效的檔名結尾.xml）。 這個檔案通常儲存在 *\[InstallRoot\]*\\*\[TestLanguage\]* 資料夾、 指定的程式碼片段資料夾，以及語言識別碼的確切位置，並使用程式碼片段之語言服務的 GUID。 索引檔案的確切路徑放登錄，如稍後所述 」 安裝的登錄項目 」。 SnippetsIndex.xml 檔案的範例如下 ︰  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<SnippetCollection>  
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">  
        <SnippetDir>  
            <OnOff>On</OnOff>  
            <Installed>true</Installed>  
            <Locale>1033</Locale>  
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>  
            <LocalizedName>Snippets</LocalizedName>  
        </SnippetDir>  
    </Language>  
</SnippetCollection>  
```  
  
 \< 語言 \> 標記指定的語言識別碼 \( `Lang` 屬性\) 和語言服務的 GUID。  
  
 這個範例假設您已安裝 Visual Studio 安裝資料夾中的語言服務。 %LCID%取代使用者的目前地區設定識別碼。 多個 \< SnippetDir \> 標記，可以加入另一個用於每個不同的目錄和地區設定。 此外，程式碼片段資料夾可以包含子資料夾，其中每個 \< SnippetDir \> 標記中內嵌的 \< SnippetSubDir \> 標記以識別在索引檔案。  
  
 使用者也可以建立自己的程式碼片段，您的語言。 這些通常儲存在使用者的 \[設定\] 資料夾，例如 *\[TestDocs\]*\\Code Snippets\\*\[TestLanguage\]*\\Test 程式碼片段，其中 *\[TestDocs\]* 是 Visual Studio 的使用者設定資料夾的位置。  
  
 下列替代項目可以放在儲存 \< DirPath \> 標記中的索引檔案的路徑。  
  
|項目|描述|  
|--------|--------|  
|%LCID%|地區設定識別碼。|  
|%Installroot%|Visual Studio 中，例如，C:\\Program Files\\Microsoft Visual Studio 8 中的根安裝資料夾。|  
|%Projdir%|包含目前專案的資料夾。|  
|%Projitem%|資料夾包含目前的專案項目。|  
|%Testdocs%|資料夾中的使用者設定\] 資料夾，例如，C:\\Documents and Settings\\*\[username\]*documents\\visual Studio\\8。|  
  
### 啟用程式碼片段的語言服務  
 您也可以新增語言服務啟用程式碼片段 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> VSPackage 屬性 \(請參閱 [註冊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md) 如需詳細資訊\)。<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> 和 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> 參數是選擇性，但您應納入 `SearchPaths` 具名參數，以便告知 **程式碼片段管理員** 的程式碼片段的位置。  
  
 如何使用這個屬性的範例如下 ︰  
  
```  
[ProvideLanguageCodeExpansion(  
         typeof(TestSnippetLanguageService),  
         "Test Snippet Language",          // Name of language used as registry key  
         0,                               // Resource ID of localized name of language service  
         "Test Snippet Language",        // Name of Language attribute in snippet template  
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index  
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets  
```  
  
### 呼叫擴充提供者  
 語言服務控制任何的插入程式碼片段，以及插入會叫用的方式。  
  
## 呼叫程式碼片段的擴充提供者  
 有兩種方式來叫用的擴充提供者 ︰ 使用功能表命令，或使用捷徑完成清單中的。  
  
### 使用功能表命令插入程式碼片段  
 若要使用的功能表命令以顯示程式碼片段瀏覽器中，加入功能表命令，然後呼叫 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> 方法中的 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 該功能表命令的回應中的介面。  
  
1.  .Vsct 檔加入命令和按鈕。 您可以找到在執行動作的指示 [逐步解說：使用 Visual Studio 封裝範本建立功能表命令](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md)。  
  
2.  自 <xref:Microsoft.VisualStudio.Package.ViewFilter> 類別並覆寫 <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> 方法，指出新的功能表命令的支援。 這個範例會永遠啟用功能表命令。  
  
    ```c#  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)  
                : base(mgr, view)  
            {  
            }  
  
            protected override int QueryCommandStatus(ref Guid guidCmdGroup,  
                                                      uint nCmdId)  
            {  
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);  
                // If the base class did not recognize the command then  
                // see if we can handle the command.  
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)  
                {  
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                    {  
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                        {  
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);  
                        }  
                    }  
                }  
                return hr;  
            }  
        }  
    }  
    ```  
  
3.  覆寫 <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> 方法中的 <xref:Microsoft.VisualStudio.Package.ViewFilter> 類別來取得 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 物件，然後呼叫 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> 方法，該物件。  
  
    ```c#  
    using Microsoft.VisualStudio.Package;  
  
    namespace TestLanguagePackage  
    {  
        class TestViewFilter : ViewFilter  
        {  
            public override bool HandlePreExec(ref Guid guidCmdGroup,  
                                               uint nCmdId,  
                                               uint nCmdexecopt,  
                                               IntPtr pvaIn,  
                                               IntPtr pvaOut)  
            {  
                if (base.HandlePreExec(ref guidCmdGroup,  
                                       nCmdId,  
                                       nCmdexecopt,  
                                       pvaIn,  
                                       pvaOut))  
                {  
                    // Base class handled the command.  Do nothing more here.  
                    return true;  
                }  
  
                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)  
                {  
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)  
                    {  
                        ExpansionProvider ep = this.GetExpansionProvider();  
                        if (this.TextView != null && ep != null)  
                        {  
                            bool bDisplayed = ep.DisplayExpansionBrowser(  
                                this.TextView,  
                                "TestLanguagePackage Snippet:",  
                                null,  
                                false,  
                                null,  
                                false);  
                        }  
                        return true;   // Handled the command.  
                    }  
                }  
                return false;   // Did not handle the command.  
            }  
        }  
    }  
  
    ```  
  
     下列方法 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 類別會呼叫 Visual Studio 中指定的順序插入程式碼片段的過程 ︰  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     之後 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> 方法呼叫，已插入程式碼片段和 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 物件是用來修改剛插入的程式碼片段以特殊的編輯模式。  
  
### 使用快速鍵來插入程式碼片段  
 捷徑完成清單中的實作會更加比實作功能表命令。 您必須先將程式碼片段捷徑，加入 IntelliSense word 完成清單。 然後，您必須偵測何時已完成的結果插入程式碼片段捷徑名稱。 最後，您必須在 \[取得的程式碼片段的標題和使用捷徑名稱的路徑，並傳遞該資訊 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 方法 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 方法。  
  
 若要自動完成清單中加入程式碼片段捷徑，將它們加入 <xref:Microsoft.VisualStudio.Package.Declarations> 物件存放至您 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 類別。 您必須先確定您可以識別做為程式碼片段名稱的捷徑。 如需範例，請參閱 [逐步解說︰ 開始安裝的程式碼片段 （舊版實作） 的清單](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)。  
  
 您可以偵測到的程式碼片段捷徑中插入 <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> 方法 <xref:Microsoft.VisualStudio.Package.Declarations> 類別。 因為程式碼片段名稱已插入至原始程式檔，必須移除插入擴充時。<xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 方法會描述程式碼片段的插入點的範圍; 如果範圍包含整個程式碼片段名稱在原始程式檔，該名稱會以程式碼片段取代。  
  
 這裡有一個版本的 <xref:Microsoft.VisualStudio.Package.Declarations> 處理插入程式碼片段捷徑名稱的類別。 中的其他方法 <xref:Microsoft.VisualStudio.Package.Declarations> 已省略類別為了清楚起見。 請注意，這個類別的建構函式接受 <xref:Microsoft.VisualStudio.Package.LanguageService> 物件。 這可以從您的版本傳遞中 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 物件 \(例如，您的實作 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 類別可能需要 <xref:Microsoft.VisualStudio.Package.LanguageService> 在其建構函式物件，並將該物件，以傳遞您 `TestDeclarations` 類別建構函式\)。  
  
```  
[C#]  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList       declarations;  
        private LanguageService languageService;  
        private TextSpan        commitSpan;  
  
        public TestDeclarations(LanguageService langService)  
            : base()  
        {  
            languageService = langService;  
            declarations = new ArrayList();  
        }  
  
        // This method is used to add declarations to the internal list.  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        // This method is called to get the string to commit to the source buffer.  
        // Note that the initial extent is only what the user has typed so far.  
        public override string OnCommit(IVsTextView textView,  
                                        string textSoFar,  
                                        char commitCharacter,  
                                        int index,  
                                        ref TextSpan initialExtent)  
        {  
            // We intercept this call only to get the initial extent  
            // of what was committed to the source buffer.  
            commitSpan = initialExtent;  
  
            return base.OnCommit(textView,  
                                 textSoFar,  
                                 commitCharacter,  
                                 index,  
                                 ref initialExtent);  
        }  
  
        // This method is called after the string has been committed to the source buffer.  
        public override char OnAutoComplete(IVsTextView textView,  
                                            string committedText,  
                                            char commitCharacter,  
                                            int index)  
        {  
            TestDeclaration item = declarations[index] as TestDeclaration;  
            if (item != null)  
            {  
                // In this example, TestDeclaration identifies types with a string.  
                // You can choose a different approach.  
                if (item.Type == "snippet")  
                {  
                    Source src = languageService.GetSource(textView);  
                    if (src != null)  
                    {  
                        ExpansionProvider ep = src.GetExpansionProvider();  
                        if (ep != null)  
                        {  
                            string title;  
                            string path;  
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;  
                            if (commitLength < committedText.Length)  
                            {  
                                // Replace everything that was inserted  
                                // so calculate the span of the full  
                                // insertion, taking into account what  
                                // was inserted when the commitSpan  
                                // was obtained in the first place.  
                                commitSpan.iEndIndex += (committedText.Length - commitLength);  
                            }  
  
                            if (ep.FindExpansionByShortcut(textView,  
                                                           committedText,  
                                                           commitSpan,  
                                                           true,  
                                                           out title,  
                                                           out path))  
                            {  
                                ep.InsertNamedExpansion(textView,  
                                                        title,  
                                                        path,  
                                                        commitSpan,  
                                                        false);  
                            }  
                        }  
                    }  
                }  
            }  
            return '\0';  
        }  
    }  
}  
```  
  
 當語言服務取得的捷徑名稱時，它會呼叫 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> 方法，以取得檔案名稱和程式碼片段的標題。 語言服務接著會呼叫 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 方法中的 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 類別來插入程式碼片段。 Visual Studio 會呼叫下列方法中指定的順序 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 插入程式碼片段的程序期間的類別 ︰  
  
1.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
 如需有關安裝的程式碼片段的清單取得語言服務的詳細資訊，請參閱 [逐步解說︰ 開始安裝的程式碼片段 （舊版實作） 的清單](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)。  
  
## 實作 ExpansionFunction 類別  
 擴充函式是內嵌在程式碼片段範本，並傳回放置在欄位中的一個或多個值的具名函式。 為了支援擴充函式語言服務中，您必須衍生自 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 類別，並實作 <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> 方法。 您接著必須覆寫 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> 方法中的 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別，以傳回您的版本的新具現化 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 您支援的每個擴充函式的類別。 如果您支援擴充函式的可能值的清單，您也必須覆寫 <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> 方法中的 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 類別，以傳回那些值的清單。  
  
 引數，或需要存取其他欄位的擴充函式不應該相關聯的可編輯的欄位，因為擴充提供者可能不會完全初始化擴充函式呼叫時。 如此一來，擴充函式不能以取得其引數或任何其他欄位的值。  
  
### 範例  
 以下是如何擴充簡單函式呼叫範例 `GetName` 可能的實作。 此擴充函式附加一個數字基底類別名稱到擴充函式具現化每次 （對應至每個時間相關聯的程式碼片段插入）。  
  
```c#  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private int classNameCounter = 0;  
  
        public override ExpansionFunction CreateExpansionFunction(  
            ExpansionProvider provider,  
            string functionName)  
        {  
            ExpansionFunction function = null;  
            if (functionName == "GetName")  
            {  
                ++classNameCounter;  
                function = new TestGetNameExpansionFunction(provider, classNameCounter);  
            }  
            return function;  
        }  
    }  
  
    internal class TestGetNameExpansionFunction : ExpansionFunction  
    {  
        private int nameCount;  
  
        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)  
            : base(provider)  
        {  
            nameCount = counter;  
        }  
  
        public override string GetCurrentValue()  
        {  
            string name = "TestClass";  
            name += nameCount.ToString();  
            return name;  
        }  
    }  
}  
```  
  
## 請參閱  
 [舊版的語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [註冊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [程式碼片段](../../ide/code-snippets.md)   
 [逐步解說︰ 開始安裝的程式碼片段 （舊版實作） 的清單](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)