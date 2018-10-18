---
title: 舊版語言服務中的程式碼片段的支援 |Microsoft Docs
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
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 71098c0dda7c06f446658c4970d0b6cf2e35e55e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49198506"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>舊版語言服務中對程式碼片段的支援
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

程式碼片段是一種插入至原始程式檔的程式碼。 程式碼片段本身是以 XML 為基礎的範本，內含一組欄位。 插入程式碼片段，並可以有不同的值，根據在其中插入程式碼片段的內容之後，會反白顯示這些欄位。 立即插入程式碼片段後，語言服務可以格式化程式碼片段。  
  
 允許使用 TAB 鍵巡覽程式碼片段欄位的特殊的編輯模式中，插入程式碼片段。 欄位可支援 IntelliSense 樣式的下拉式清單功能表。 使用者會輸入 ENTER 或 ESC 鍵認可至原始程式檔的程式碼片段。 若要深入了解程式碼片段，請參閱[程式碼片段](../../ide/code-snippets.md)。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新的方式是使用 MEF 擴充功能。 若要深入了解，請參閱[逐步解說： 實作程式碼片段](../../extensibility/walkthrough-implementing-code-snippets.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 盡。 這會改善您的語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="managed-package-framework-support-for-code-snippets"></a>Managed 封裝架構支援程式碼片段  
 Managed 的 package framework (MPF) 支援大部分的程式碼片段功能，讀取要插入程式碼片段的範本，並啟用特殊編輯模式。 支援透過管理<xref:Microsoft.VisualStudio.Package.ExpansionProvider>類別。  
  
 當<xref:Microsoft.VisualStudio.Package.Source>具現化類別，<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>方法中的<xref:Microsoft.VisualStudio.Package.LanguageService>類別呼叫以取得<xref:Microsoft.VisualStudio.Package.ExpansionProvider>物件 (請注意，基底<xref:Microsoft.VisualStudio.Package.LanguageService>類別一律會傳回新<xref:Microsoft.VisualStudio.Package.ExpansionProvider>物件給每個<xref:Microsoft.VisualStudio.Package.Source>物件）。  
  
 MPF 不支援擴充函式。 展開函式是內嵌在程式碼片段範本，並傳回放置在欄位中的一或多個值的具名函式。 值會傳回語言服務本身透過<xref:Microsoft.VisualStudio.Package.ExpansionFunction>物件。 <xref:Microsoft.VisualStudio.Package.ExpansionFunction>物件必須實作的語言服務，以支援擴充函式。  
  
## <a name="providing-support-for-code-snippets"></a>提供支援的程式碼片段  
 若要啟用程式碼片段的支援，您必須提供，或安裝程式碼片段，您必須提供使用者插入這些程式碼片段的方法。 有三個步驟，以啟用程式碼片段的支援：  
  
1.  安裝程式碼片段檔案。  
  
2.  啟用您的語言服務的程式碼片段。  
  
3.  叫用<xref:Microsoft.VisualStudio.Package.ExpansionProvider>物件。  
  
### <a name="installing-the-snippet-files"></a>安裝程式碼片段檔案  
 所有的程式碼片段語言會儲存為 XML 檔案中的範本通常一個程式碼片段範本每個檔案。 如需程式碼片段範本所使用的 XML 結構描述的詳細資訊，請參閱[程式碼片段結構描述參考](../../ide/code-snippets-schema-reference.md)。 每個程式碼片段範本具有語言識別碼。 此語言識別碼在登錄中指定，而且放入`Language`屬性的\<程式碼 > 範本中的標記。  
  
 通常有兩個程式碼片段範本檔案儲存所在的位置： 1） 已安裝您的語言，以及 2） 中使用者的資料夾。 這些位置會新增至登錄因此，Visual Studio**程式碼片段管理員**可以尋找程式碼片段。 使用者的資料夾是儲存使用者所建立的程式碼片段。  
  
 已安裝的程式碼片段範本檔案的一般資料夾版面配置看起來像這樣︰ *[InstallRoot]*\\ *[TestLanguage]* \Snippets\\ *[LCID]* \Snippets。  
  
 *[InstallRoot]* 是安裝在您的語言的資料夾。  
  
 *[TestLanguage]* 是您的語言，做為資料夾名稱的名稱。  
  
 *[LCID]* 是地區設定識別碼。 這是如何當地語系化的版本的程式碼片段會儲存。 例如，英文的地區設定識別碼是 1033，因此 *[LCID]* 1033年取代。  
  
 必須提供一個額外的檔案，這是索引檔案，通常稱為 SnippetsIndex.xml 或 ExpansionsIndex.xml （您可以使用任何有效的檔名以.xml 結尾）。 這個檔案通常儲存在 *[InstallRoot]*\\ *[TestLanguage]* 資料夾，並指定程式碼片段資料夾，以及語言識別碼的確切位置和語言的 GUID使用程式碼片段的服務。 索引檔案的確切的路徑會放入登錄中，稍後在 「 安裝的登錄項目 」 中所述。 以下是 SnippetsIndex.xml 檔案的範例：  
  
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
  
 \<語言 > 標記指定的語言識別碼 (`Lang`屬性) 和語言服務的 GUID。  
  
 這個範例假設您已安裝 Visual Studio 安裝資料夾中的語言服務。 %LCID%會取代使用者的目前地區設定識別碼。 多個\<SnippetDir > 標記，可以加入另一個用於每個不同的目錄和地區設定。 此外，程式碼片段資料夾可以包含子資料夾，其中每一個識別索引檔案中\<SnippetSubDir > 標記內嵌於\<SnippetDir > 標記。  
  
 使用者也可以建立自己的程式碼片段，您的語言。 這些通常儲存在使用者的 [設定] 資料夾，例如 *[TestDocs]* \Code 程式碼片段\\ *[TestLanguage]* \Test 程式碼片段，其中 *[TestDocs]* 是適用於 Visual Studio 使用者的 [設定] 資料夾的位置。  
  
 下列的替代項目可以放在儲存中的路徑\<DirPath > 標記中的索引檔案。  
  
|元素|描述|  
|-------------|-----------------|  
|%LCID%|地區設定識別碼。|  
|%Installroot%|Visual Studio 中，例如，C:\Program Files\Microsoft Visual Studio 8 的根安裝資料夾。|  
|%Projdir%|包含目前專案的資料夾。|  
|%Projitem%|資料夾包含目前的專案項目。|  
|%Testdocs%|在 [使用者設定] 資料夾，例如，C:\Documents and Settings 資料夾\\ *[username]* documents\visual Studio\8。|  
  
### <a name="enabling-code-snippets-for-your-language-service"></a>語言服務的啟用程式碼片段  
 您也可以新增語言服務的啟用程式碼片段<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>VSPackage 屬性 (請參閱 <<c2> [ 註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)如需詳細資訊)。 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A>並<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A>參數是選擇性的但您應該將包含`SearchPaths`具名參數，以通知**程式碼片段管理員**的程式碼片段的位置。  
  
 如何使用這個屬性的範例如下：  
  
```  
[ProvideLanguageCodeExpansion(  
         typeof(TestSnippetLanguageService),  
         "Test Snippet Language",          // Name of language used as registry key  
         0,                               // Resource ID of localized name of language service  
         "Test Snippet Language",        // Name of Language attribute in snippet template  
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index  
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets  
```  
  
### <a name="calling-the-expansion-provider"></a>呼叫擴充提供者  
 語言服務控制任何的插入程式碼片段，以及插入會叫用的方式。  
  
## <a name="calling-the-expansion-provider-for-code-snippets"></a>呼叫程式碼片段的擴充提供者  
 有兩種方式來叫用的擴充提供者： 使用功能表命令，或使用捷徑從完成清單。  
  
### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>使用功能表命令插入程式碼片段  
 若要使用的功能表命令，以顯示程式碼片段瀏覽器，您需要加入功能表命令，然後呼叫<xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A>方法中的<xref:Microsoft.VisualStudio.Package.ExpansionProvider>該功能表命令的回應中的介面。  
  
1.  加入.vsct 檔的命令和按鈕。 您可以找到在執行動作的指示[逐步解說： 建立功能表命令，使用 Visual Studio Package 範本](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)。  
  
2.  衍生的類別<xref:Microsoft.VisualStudio.Package.ViewFilter>類別並覆寫<xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A>方法，以指示新的功能表命令的支援。 這個範例中永遠啟用功能表命令。  
  
    ```csharp  
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
  
3.  覆寫<xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A>方法中的<xref:Microsoft.VisualStudio.Package.ViewFilter>類別來取得<xref:Microsoft.VisualStudio.Package.ExpansionProvider>物件，然後呼叫<xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A>該物件上的方法。  
  
    ```csharp  
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
  
     中的下列方法<xref:Microsoft.VisualStudio.Package.ExpansionProvider>類別由 Visual Studio 呼叫中指定的順序插入程式碼片段的程序期間：  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>  
  
5.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
6.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
7.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
8.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
     在後<xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>呼叫方法，已插入程式碼片段和<xref:Microsoft.VisualStudio.Package.ExpansionProvider>物件是用來修改剛插入的程式碼片段以特殊的編輯模式。  
  
### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>使用快速鍵來插入程式碼片段  
 實作從完成清單的捷徑會比實作功能表命令更為複雜。 您必須先將程式碼片段捷徑，加入 IntelliSense 文字自動完成清單。 然後，您必須偵測何時已完成的結果插入程式碼片段捷徑名稱。 最後，您必須在 取得程式碼片段的標題和使用捷徑名稱的路徑，並傳遞該項資訊給<xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>方法<xref:Microsoft.VisualStudio.Package.ExpansionProvider>方法。  
  
 若要加入文字自動完成清單中的程式碼片段捷徑，將其新增至<xref:Microsoft.VisualStudio.Package.Declarations>物件中您<xref:Microsoft.VisualStudio.Package.AuthoringScope>類別。 您必須確定您可以識別做為程式碼片段名稱的捷徑。 如需範例，請參閱[逐步解說： 取得清單的安裝程式碼片段 （舊版實作）](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)。  
  
 您可以偵測到的程式碼片段捷徑中插入<xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A>方法的<xref:Microsoft.VisualStudio.Package.Declarations>類別。 因為程式碼片段名稱已插入至原始程式檔，它必須先移除插入擴充時。 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>方法會採用描述程式碼片段的插入點的範圍; 如果範圍包含整個程式碼片段名稱的原始程式檔中，會以程式碼片段取代該名稱。  
  
 以下是版本<xref:Microsoft.VisualStudio.Package.Declarations>類別會處理指定的捷徑名稱插入程式碼片段。 中的其他方法<xref:Microsoft.VisualStudio.Package.Declarations>為了清楚起見已省略類別。 請注意，這個類別的建構函式接受<xref:Microsoft.VisualStudio.Package.LanguageService>物件。 這可以傳入從您的版本<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件 (例如，您的實作<xref:Microsoft.VisualStudio.Package.AuthoringScope>類別可能需要<xref:Microsoft.VisualStudio.Package.LanguageService>物件在其建構函式，並傳遞至該物件您`TestDeclarations`類別建構函式)。  
  
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
  
 當語言服務的捷徑名稱，它會呼叫<xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A>方法，以取得檔案名稱和程式碼片段的標題。 語言服務接著會呼叫<xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>方法中的<xref:Microsoft.VisualStudio.Package.ExpansionProvider>類別，以插入程式碼片段。 Visual Studio 會呼叫下列方法中指定的順序<xref:Microsoft.VisualStudio.Package.ExpansionProvider>程序期間的插入程式碼片段的類別：  
  
1.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>  
  
2.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>  
  
3.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>  
  
4.  <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>  
  
 如需有關如何取得一份已安裝的程式碼片段語言服務的詳細資訊，請參閱[逐步解說： 取得清單的安裝程式碼片段 （舊版實作）](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)。  
  
## <a name="implementing-the-expansionfunction-class"></a>實作 ExpansionFunction 類別  
 展開函式是內嵌在程式碼片段範本，並傳回放置在欄位中的一或多個值的具名函式。 為了支援擴充函式語言服務中，您必須衍生的類別<xref:Microsoft.VisualStudio.Package.ExpansionFunction>類別，並實作<xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A>方法。 您必須接著覆寫<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>方法中的<xref:Microsoft.VisualStudio.Package.LanguageService>類別，以傳回您的版本的新具現化<xref:Microsoft.VisualStudio.Package.ExpansionFunction>您支援每個擴充函式的類別。 如果您支援擴充函式的可能值的清單，您也必須覆寫<xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A>方法中的<xref:Microsoft.VisualStudio.Package.ExpansionFunction>類別，以傳回這些值的清單。  
  
 引數，或需要存取其他欄位的擴充函式不應該相關聯的可編輯的欄位，如擴充提供者可能未完全初始化呼叫擴充函式的時間。 如此一來，擴充函式不可以取得其引數或任何其他欄位的值。  
  
### <a name="example"></a>範例  
 以下是如何簡單的擴充函式呼叫範例`GetName`可能實作。 此擴充函式附加一個數字基底類別名稱的擴充函式具現化每個階段 （對應至每個時間相關聯的程式碼片段插入）。  
  
```csharp  
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
  
## <a name="see-also"></a>另請參閱  
 [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [程式碼片段](../../ide/code-snippets.md)   
 [逐步解說︰取得已安裝程式碼片段 (舊版實作) 的清單](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

