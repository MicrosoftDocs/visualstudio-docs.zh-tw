---
title: 舊版語言服務中的程式碼片段支援 |Microsoft Docs
description: 瞭解舊版語言服務如何支援程式碼片段。 程式碼片段是插入原始程式檔中的一段程式碼。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 781633a995027ee9938a0c579af32373c06207c2
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876606"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>舊版語言服務中對程式碼片段的支援
程式碼片段是插入原始程式檔中的一段程式碼。 程式碼片段本身是以 XML 為基礎的範本，其中包含一組欄位。 這些欄位會在插入程式碼片段之後反白顯示，而且可以有不同的值，視插入程式碼片段的內容而定。 緊接在插入程式碼片段之後，語言服務可以格式化程式碼片段。

 程式碼片段會插入特殊的編輯模式，讓您可以使用 TAB 鍵來流覽程式碼片段的欄位。 這些欄位可以支援 IntelliSense 樣式的下拉式功能表。 使用者可以輸入 ENTER 或 ESC 鍵來認可來源檔案的程式碼片段。 若要深入瞭解程式碼片段，請參閱 [程式碼片段](../../ide/code-snippets.md)。

 舊版語言服務會實作為 VSPackage 的一部分，但是執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解，請參閱 [逐步解說：執行程式碼片段](../../extensibility/walkthrough-implementing-code-snippets.md)。

> [!NOTE]
> 建議您儘快開始使用新的編輯器 API。 這可改善您的語言服務效能，並讓您利用新的編輯器功能。

## <a name="managed-package-framework-support-for-code-snippets"></a>Managed Package Framework 對程式碼片段的支援
 受管理的封裝架構 (MPF) 支援大部分的程式碼片段功能，從讀取範本到插入程式碼片段並啟用特殊編輯模式。 支援是透過類別來管理 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 。

 當 <xref:Microsoft.VisualStudio.Package.Source> 類別具現化時， <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> 會呼叫類別中的方法來取得 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 物件 (請注意，基類一律會 <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 針對每個物件) 傳回新的物件 <xref:Microsoft.VisualStudio.Package.Source> 。

 MPF 不支援擴充功能。 擴充函式是內嵌于程式碼片段範本中的命名函式，會傳回一個或多個要放置在欄位中的值。 語言服務本身會透過物件傳回這些值 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 。 <xref:Microsoft.VisualStudio.Package.ExpansionFunction>物件必須由語言服務所執行，才能支援擴充函數。

## <a name="providing-support-for-code-snippets"></a>提供程式碼片段的支援
 若要啟用程式碼片段的支援，您必須提供或安裝程式碼片段，而且必須提供方法讓使用者插入這些程式碼片段。 啟用程式碼片段支援的步驟有三個：

1. 安裝程式碼片段檔案。

2. 啟用語言服務的程式碼片段。

3. 叫用 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 物件。

### <a name="installing-the-snippet-files"></a>安裝程式碼片段檔案
 語言的所有程式碼片段都會儲存為 XML 檔案中的範本，而每個檔案通常會有一個程式碼片段範本。 如需用於程式碼片段範本之 XML 架構的詳細資訊，請參閱 [程式碼片段架構參考](../../ide/code-snippets-schema-reference.md)。 每個程式碼片段範本都使用語言識別項來識別。 這個語言識別項是在登錄中指定，並放入 `Language` \<Code> 範本中標記的屬性。

 通常會儲存程式碼片段範本檔案的兩個位置： 1) 安裝語言的位置，以及使用者資料夾中的 2) 。 這些位置會新增至登錄，讓 Visual Studio **程式碼片段管理員** 可以找到程式碼片段。 使用者的資料夾是儲存使用者所建立之程式碼片段的位置。

 已安裝的程式碼片段範本檔案的一般資料夾配置如下所示： *[InstallRoot]* \\ *[TestLanguage]* \Snippets \\ *[LCID]* \Snippets。

 *[InstallRoot]* 是您的語言安裝所在的資料夾。

 *[TestLanguage]* 是您的語言名稱，作為資料夾名稱。

 *[LCID]* 是地區設定識別碼。 這是儲存程式碼片段當地語系化版本的方式。 例如，英文的地區設定識別碼是1033，因此 *[LCID]* 會由1033取代。

 您必須提供一個額外的檔案，而且這是索引檔案，通常稱為 SnippetsIndex.xml 或 ExpansionsIndex.xml (您可以使用以 .xml) 結尾的任何有效檔案名。 這個檔案通常會儲存在 *[InstallRoot]* \\ *[TestLanguage]* 資料夾中，並指定程式碼片段資料夾的確切位置，以及使用程式碼片段之語言服務的語言識別項和 GUID。 索引檔案的確切路徑會放入登錄中，如稍後的「安裝登錄專案」中所述。 以下是 SnippetsIndex.xml 檔案的範例：

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

 \<Language>標記會指定 (`Lang` 屬性) 和語言服務 GUID 的語言識別項。

 此範例假設您已在 Visual Studio 安裝資料夾中安裝語言服務。 % LCID% 會取代為使用者目前的地區設定識別碼。 您可以新增多個標籤 \<SnippetDir> ，每個不同的目錄和地區設定一個標記。 此外，程式碼片段資料夾可以包含子資料夾，其中每個都是在索引檔中，以 \<SnippetSubDir> 內嵌在標記中的標記來識別 \<SnippetDir> 。

 使用者也可以為您的語言建立自己的程式碼片段。 這些通常會儲存在使用者的 [設定] 資料夾中，例如 *[TestDocs]* \Code 程式碼片段 \\ *[TestLanguage]* \Test 程式碼片段，其中 *[TestDocs]* 是 Visual Studio 的使用者設定資料夾的位置。

 下列替代專案可以放在索引檔的標記所儲存的路徑中 \<DirPath> 。

|元素|描述|
|-------------|-----------------|
|LCID|地區設定識別碼。|
|%InstallRoot%|Visual Studio 的根安裝資料夾，例如 C:\Program Files\Microsoft Visual Studio 8。|
|%ProjDir%|包含目前專案的資料夾。|
|%ProjItem%|包含目前專案專案的資料夾。|
|%TestDocs%|使用者的 [設定] 資料夾中的資料夾，例如 C:\documents and 和 Settings \\ *[username]* \My Documents\Visual Studio\8。|

### <a name="enabling-code-snippets-for-your-language-service"></a>啟用語言服務的程式碼片段
 您可以將屬性新增至 VSPackage，以啟用語言服務的程式碼片段 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> (如需詳細資料，請參閱 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)) 。 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A>和 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> 參數是選擇性的，但您應該包含 `SearchPaths` 具名引數，以便通知 **程式碼片段管理員** 您的程式碼片段位置。

 以下是如何使用此屬性的範例：

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
 語言服務會控制任何程式碼片段的插入，以及叫用插入的方式。

## <a name="calling-the-expansion-provider-for-code-snippets"></a>呼叫程式碼片段的擴充提供者
 有兩種方式可叫用展開提供者：使用功能表命令或使用完成清單中的快捷方式。

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>使用功能表命令插入程式碼片段
 若要使用功能表命令來顯示程式碼片段瀏覽器，您可以新增功能表命令，然後在 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 介面中呼叫方法來回應該功能表命令。

1. 將命令和按鈕新增至 .vsct 檔案。 您可以在 [建立具有功能表命令的延伸](../../extensibility/creating-an-extension-with-a-menu-command.md)模組時找到相關指示。

2. 從類別衍生類別 <xref:Microsoft.VisualStudio.Package.ViewFilter> ，並覆寫 <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> 方法以表示支援新的功能表命令。 此範例一律會啟用功能表命令。

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

3. 覆寫 <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> 類別中的方法， <xref:Microsoft.VisualStudio.Package.ViewFilter> 以取得 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 物件並 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> 在該物件上呼叫方法。

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

     在 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 插入程式碼片段的過程中，Visual Studio 會依指定的順序呼叫類別中的下列方法：

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>呼叫方法之後，會插入程式碼片段，且 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 物件會處於特殊編輯模式，用來修改剛插入的程式碼片段。

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>使用快速鍵插入程式碼片段
 從完成清單中的快捷方式執行，會比執行功能表命令更加相關。 您必須先將程式碼片段快速鍵新增至 IntelliSense word 完成清單。 然後，您必須偵測在完成後插入程式碼片段快捷方式名稱的時間。 最後，您必須使用快速鍵名稱來取得程式碼片段標題和路徑，並將該資訊傳遞給 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 方法上的方法 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 。

 若要將程式碼片段快速鍵新增至 [自動完成] 清單，請將其加入至 <xref:Microsoft.VisualStudio.Package.Declarations> 類別中的物件 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 。 您必須確認可以將快捷方式識別為程式碼片段名稱。 如需範例，請參閱 [逐步解說：取得已安裝的程式碼片段清單 (舊版的執行) ](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)。

 您可以偵測在類別的方法中插入程式碼片段快捷方式 <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> <xref:Microsoft.VisualStudio.Package.Declarations> 。 因為程式碼片段名稱已經插入原始程式檔中，所以必須在插入擴充時移除。 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>方法會採用一個範圍來描述程式碼片段的插入點; 如果範圍在原始程式檔中包含整個程式碼片段名稱，則該名稱會取代為程式碼片段。

 以下是 <xref:Microsoft.VisualStudio.Package.Declarations> 類別的版本，它會根據指定的快捷方式名稱來處理程式碼片段插入。 <xref:Microsoft.VisualStudio.Package.Declarations>為了清楚起見，已省略類別中的其他方法。 請注意，這個類別的函式會採用 <xref:Microsoft.VisualStudio.Package.LanguageService> 物件。 這可從您的物件版本中傳入 <xref:Microsoft.VisualStudio.Package.AuthoringScope> (例如，您的類別實作為您 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 可能會在其函式中採用物件，並將 <xref:Microsoft.VisualStudio.Package.LanguageService> 該物件傳遞至類別的函式 `TestDeclarations`) 。

```csharp
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

 當語言服務取得快捷方式名稱時，會呼叫 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> 方法來取得檔案名和程式碼片段的標題。 然後，語言服務會呼叫 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 類別中的方法 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> ，以插入程式碼片段。 在 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 插入程式碼片段的過程中，下列方法會由類別中的指定順序 Visual Studio 呼叫：

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   如需有關為您的語言服務取得已安裝程式碼片段清單的詳細資訊，請參閱 [逐步解說：取得已安裝的程式碼片段清單 (舊版的執行) ](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)。

## <a name="implementing-the-expansionfunction-class"></a>執行 ExpansionFunction 類別
 擴充函式是內嵌于程式碼片段範本中的命名函式，會傳回一個或多個要放置在欄位中的值。 為了在您的語言服務中支援擴充功能，您必須從類別衍生類別 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> ，並執行 <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> 方法。 然後，您必須覆寫 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> 類別中的方法 <xref:Microsoft.VisualStudio.Package.LanguageService> ，以 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 針對您支援的每個擴充函數傳回類別版本的新具現化。 如果您支援來自擴充函數的可能值清單，您也必須覆寫 <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> 類別中的方法， <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 以傳回這些值的清單。

 接受引數或需要存取其他欄位的展開函式不應與可編輯的欄位相關聯，因為擴充提供者可能不會在呼叫擴充函數時完全初始化。 因此，擴充函數無法取得其引數或任何其他欄位的值。

### <a name="example"></a>範例
 以下是一個範例，說明如何叫用簡單的擴充函數 `GetName` 。 這個展開函式會在每次具現化擴充函式時，將一個數位附加至基類名稱， (對應到每次將關聯的程式碼片段插入) 。

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

## <a name="see-also"></a>請參閱
- [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)
- [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [程式碼片段](../../ide/code-snippets.md)
- [逐步解說：取得已安裝的程式碼片段 (舊版實作) 清單](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
