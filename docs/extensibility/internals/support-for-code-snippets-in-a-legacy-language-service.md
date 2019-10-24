---
title: 舊版語言服務中的程式碼片段支援 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d771db166baa66426c7a6d03b344c4bc7b74b27
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723101"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>舊版語言服務中對程式碼片段的支援
程式碼片段是插入原始程式檔中的一段程式碼。 程式碼片段本身是以 XML 為基礎的範本，具有一組欄位。 這些欄位會在插入程式碼片段後反白顯示，而且可以根據插入程式碼片段的內容而有不同的值。 插入程式碼片段之後，語言服務就會立即格式化程式碼片段。

 程式碼片段會以特殊的編輯模式插入，讓程式碼片段的欄位可以使用 TAB 鍵來流覽。 欄位可以支援 IntelliSense 樣式的下拉式功能表。 使用者可以輸入 ENTER 或 ESC 鍵，將程式碼片段認可至原始程式檔。 若要深入瞭解程式碼片段，請參閱[程式碼片段](../../ide/code-snippets.md)。

 舊版語言服務會實作為 VSPackage 的一部分，但執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解，請參閱[逐步解說：執行程式碼片段](../../extensibility/walkthrough-implementing-code-snippets.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將可改善語言服務的效能，並可讓您利用新的編輯器功能。

## <a name="managed-package-framework-support-for-code-snippets"></a>適用于程式碼片段的 Managed Package Framework 支援
 Managed package framework （MPF）支援大部分的程式碼片段功能，從讀取範本到插入程式碼片段，以及啟用特殊編輯模式。 支援是透過 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 類別來管理。

 當 <xref:Microsoft.VisualStudio.Package.Source> 類別具現化時，會呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別中的 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> 方法來取得 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 物件（請注意，基底 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別一律會針對每個 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 物件傳回新的 <xref:Microsoft.VisualStudio.Package.Source> 物件）。

 MPF 不支援擴充功能。 展開函式是內嵌在程式碼片段範本中的命名函數，會傳回一個或多個要放入欄位中的值。 語言服務本身會透過 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 物件來傳回值。 語言服務必須執行 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 物件，才能支援擴充功能。

## <a name="providing-support-for-code-snippets"></a>提供程式碼片段的支援
 若要啟用程式碼片段的支援，您必須提供或安裝程式碼片段，而且您必須提供方法讓使用者插入這些程式碼片段。 啟用程式碼片段的支援有三個步驟：

1. 安裝程式碼片段檔案。

2. 啟用語言服務的程式碼片段。

3. 叫用 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 物件。

### <a name="installing-the-snippet-files"></a>安裝程式碼片段檔案
 語言的所有程式碼片段都會儲存為 XML 檔案中的範本，而每個檔案通常會有一個程式碼片段範本。 如需用於程式碼片段範本之 XML 架構的詳細資訊，請參閱[程式碼片段架構參考](../../ide/code-snippets-schema-reference.md)。 每個程式碼片段範本都會以語言識別項識別。 此語言識別項是在登錄中指定，並放入範本中 \<Code > 標記的 `Language` 屬性。

 通常會在使用者的資料夾中儲存程式碼片段範本檔案的兩個位置：1）您的語言已安裝和2）。 這些位置會新增至登錄，讓 Visual Studio**程式碼片段管理員**可以找到程式碼片段。 使用者的資料夾是儲存使用者所建立之程式碼片段的位置。

 已安裝程式碼片段範本檔案的一般資料夾版面配置看起來像這樣： *[InstallRoot]* \\ *[TestLanguage]* \snippets < \\ *[LCID]* \snippets)

 *[InstallRoot]* 是您的語言安裝所在的資料夾。

 *[TestLanguage]* 是您的語言名稱，做為資料夾名稱。

 *[LCID]* 是地區設定識別碼。 這就是您的程式碼片段當地語系化版本的儲存方式。 例如，英文的地區設定識別碼是1033，因此 *[LCID]* 會取代為1033。

 必須提供一個額外的檔案，而且這是一個索引檔，通常稱為 SnippetsIndex 或 ExpansionsIndex （您可以使用任何以 .xml 結尾的有效檔案名）。 這個檔案通常會儲存在 *[InstallRoot]* \\ *[TestLanguage]* 資料夾中，並指定程式碼片段資料夾的確切位置，以及使用程式碼片段之語言服務的語言識別項和 GUID。 索引檔案的確切路徑會放入登錄中，如稍後的「安裝登錄專案」中所述。 以下是 SnippetsIndex 的範例：

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

 @No__t_0Language > 標記會指定語言識別項（`Lang` 屬性）和語言服務 GUID。

 這個範例假設您已在 Visual Studio 安裝資料夾中安裝語言服務。 % LCID% 會取代為使用者目前的地區設定識別碼。 可以新增多個 \<SnippetDir > 標記，每個不同的目錄和地區設定一個。 此外，程式碼片段資料夾可以包含子資料夾，其中每個都是在索引檔案中識別，而該檔案中的 \<SnippetSubDir > 標記內嵌在 \<SnippetDir > 標記中。

 使用者也可以為您的語言建立自己的程式碼片段。 這些通常會儲存在使用者的 [設定] 資料夾中，例如 *[TestDocs]* \Code 程式碼片段 \\ *[TestLanguage]* \Test 程式碼片段，其中 *[TestDocs]* 是使用者的 [設定] 資料夾中 Visual Studio 的位置。

 下列替代元素可以放在索引檔案中儲存于 \<DirPath > 標記的路徑中。

|項目|描述|
|-------------|-----------------|
|LCID|地區設定識別碼。|
|InstallRoot|Visual Studio 的根安裝資料夾，例如 C:\Program Files\Microsoft Visual Studio 8。|
|%ProjDir%|包含目前專案的資料夾。|
|%ProjItem%|包含目前專案專案的資料夾。|
|%TestDocs%|使用者的 [設定] 資料夾中的資料夾，例如 C:\documents and 和 Settings \\ *[username]* \My Documents\Visual Studio\8。|

### <a name="enabling-code-snippets-for-your-language-service"></a>為您的語言服務啟用程式碼片段
 您可以藉由將 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> 屬性新增至 VSPackage （如需詳細資訊，請參閱[註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)），為您的語言服務啟用程式碼片段。 @No__t_0 和 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> 參數是選擇性的，但您應該包含 `SearchPaths` 名為參數，才能通知**程式碼片段管理員**您的程式碼片段位置。

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
 語言服務會控制插入任何程式碼片段，以及叫用插入的方式。

## <a name="calling-the-expansion-provider-for-code-snippets"></a>呼叫程式碼片段的擴充提供者
 叫用展開提供者的方法有兩種：使用功能表命令，或使用完成清單中的快捷方式。

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>使用功能表命令插入程式碼片段
 若要使用功能表命令來顯示程式碼片段瀏覽器，您可以新增功能表命令，然後在 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 介面中呼叫 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> 方法，以回應該功能表命令。

1. 將命令和按鈕新增至您的 .vsct 檔案。 您可以在[使用功能表命令建立擴充](../../extensibility/creating-an-extension-with-a-menu-command.md)功能中找到這麼做的指示。

2. 從 <xref:Microsoft.VisualStudio.Package.ViewFilter> 類別衍生類別，並覆寫 <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> 方法，以表示支援新的功能表命令。 這個範例一律會啟用功能表命令。

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

3. 覆寫 <xref:Microsoft.VisualStudio.Package.ViewFilter> 類別中的 <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> 方法，以取得 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 物件，並在該物件上呼叫 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> 方法。

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

     在插入程式碼片段的過程中，Visual Studio 會依照指定的順序，在 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 類別中呼叫下列方法：

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     呼叫 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> 方法之後，就會插入程式碼片段，而 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 物件會處於用來修改剛插入之程式碼片段的特殊編輯模式。

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>使用快捷方式插入程式碼片段
 從完成清單中執行快捷方式比執行功能表命令更為複雜。 您必須先將程式碼片段快捷方式加入至 IntelliSense 文字自動完成清單。 接著，您必須偵測到當代碼段快捷方式名稱已插入為完成後的結果。 最後，您必須使用快捷方式名稱取得程式碼片段標題和路徑，並將該資訊傳遞給 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 方法上的 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 方法。

 若要將程式碼片段快捷方式加入至「自動完成」清單，請將它們新增至 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 類別中的 <xref:Microsoft.VisualStudio.Package.Declarations> 物件。 您必須確認可以將快捷方式識別為程式碼片段名稱。 如需範例，請參閱[逐步解說：取得已安裝程式碼片段（舊版執行）的清單](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)。

 您可以在 <xref:Microsoft.VisualStudio.Package.Declarations> 類別的 <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> 方法中偵測程式碼片段快捷方式的插入。 由於程式碼片段名稱已經插入原始程式檔中，因此在插入展開時，必須將它移除。 @No__t_0 方法會採用一個範圍來描述程式碼片段的插入點;如果範圍在原始程式檔中包含整個程式碼片段名稱，則該名稱會取代為程式碼片段。

 以下是一個 <xref:Microsoft.VisualStudio.Package.Declarations> 類別的版本，它會在指定快捷方式名稱的情況之下處理程式碼片段插入。 為了清楚起見，已省略 <xref:Microsoft.VisualStudio.Package.Declarations> 類別中的其他方法。 請注意，此類別的函式會採用 <xref:Microsoft.VisualStudio.Package.LanguageService> 物件。 這可以從您的 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 物件版本傳入（例如，您的 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 類別的執行可能會在其程式中採用 <xref:Microsoft.VisualStudio.Package.LanguageService> 物件，並將該物件傳遞至您的 `TestDeclarations` 類別的函式）。

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

 當語言服務取得快捷方式名稱時，它會呼叫 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> 方法，以取得檔案名和程式碼片段標題。 然後語言服務會呼叫 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 類別中的 <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> 方法，以插入程式碼片段。 在插入程式碼片段的程式期間，會以指定的順序在 <xref:Microsoft.VisualStudio.Package.ExpansionProvider> 類別中 Visual Studio 呼叫下列方法：

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   如需取得語言服務已安裝程式碼片段清單的詳細資訊，請參閱[逐步解說：取得已安裝程式碼片段（舊版執行）的清單](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)。

## <a name="implementing-the-expansionfunction-class"></a>執行 ExpansionFunction 類別
 展開函式是內嵌在程式碼片段範本中的命名函數，會傳回一個或多個要放入欄位中的值。 若要在您的語言服務中支援擴充功能，您必須從 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 類別衍生類別，並執行 <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> 方法。 接著，您必須覆寫 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別中的 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> 方法，以傳回您所支援之每個擴充功能的 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 類別版本的新具現化。 如果您支援來自擴充函數的可能值清單，您也必須覆寫 <xref:Microsoft.VisualStudio.Package.ExpansionFunction> 類別中的 <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> 方法，以傳回這些值的清單。

 接受引數或需要存取其他欄位的擴充函數不應該與可編輯的欄位相關聯，因為在呼叫擴充函數時，擴充提供者可能未完全初始化。 因此，擴充函數無法取得其引數或任何其他欄位的值。

### <a name="example"></a>範例
 以下範例示範如何執行稱為 `GetName` 的簡單擴充函數。 這個擴充函式會在每次具現化擴充函式時，將一個數位附加至基類名稱（這會對應到每次插入相關聯的程式碼片段）。

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
- [逐步解說︰取得已安裝程式碼片段 (舊版實作) 的清單](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)