---
title: 支援舊語言服務中的代碼段 |微軟文件
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
ms.openlocfilehash: ad871eb73341f6ab87229687e2a6df898ffda32d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704918"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>舊版語言服務中對程式碼片段的支援
代碼段是插入到源檔中的代碼段。 代碼段本身是一個基於 XML 的樣本,包含一組欄位。 這些欄位在插入代碼段後突出顯示,並根據插入代碼段的上下文的不同值。 插入代碼段後,語言服務可以立即格式化代碼段。

 程式碼段插入到特殊的編輯模式,允許使用 TAB 鍵導航代碼段的欄位。 這些欄位可以支援 IntelliSense 風格的下拉功能表。 用戶通過鍵入 ENTER 或 ESC 密鑰將代碼段提交到源檔。 要瞭解有關代碼段的更多,請參閱[程式碼段](../../ide/code-snippets.md)。

 舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解更多資訊,請參閱[演練:實現代碼代碼段](../../extensibility/walkthrough-implementing-code-snippets.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將提高語言服務的性能,並允許您利用新的編輯器功能。

## <a name="managed-package-framework-support-for-code-snippets"></a>程式碼段的託管套件框架支援
 託管包框架 (MPF) 支援大多數代碼段功能,從讀取範本到插入代碼段和啟用特殊編輯模式。 支援通過類<xref:Microsoft.VisualStudio.Package.ExpansionProvider>進行管理。

 實例化<xref:Microsoft.VisualStudio.Package.Source>類時,將調<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A><xref:Microsoft.VisualStudio.Package.LanguageService>用 類中的方法以<xref:Microsoft.VisualStudio.Package.ExpansionProvider>獲取物件 (請<xref:Microsoft.VisualStudio.Package.LanguageService>注意,基<xref:Microsoft.VisualStudio.Package.ExpansionProvider><xref:Microsoft.VisualStudio.Package.Source>類始終為每個 物件返回一個新物件)。

 MPF 不支援擴充功能。 擴展函數是嵌入在代碼段範本中的命名函數,並返回要放置在欄位中的一個或多個值。 這些值由語言服務本身通過<xref:Microsoft.VisualStudio.Package.ExpansionFunction>物件返回。 該<xref:Microsoft.VisualStudio.Package.ExpansionFunction>物件必須由語言服務實現以支援擴展函數。

## <a name="providing-support-for-code-snippets"></a>支援代碼段
 若要啟用對代碼段的支持,必須提供或安裝代碼段,並且必須為使用者提供插入這些代碼段的方法。 支援代碼段有三個步驟:

1. 安裝代碼段檔。

2. 為您的語言服務啟用代碼段。

3. 呼叫物件<xref:Microsoft.VisualStudio.Package.ExpansionProvider>。

### <a name="installing-the-snippet-files"></a>安裝程式碼段檔案
 語言的所有程式碼段都儲存在 XML 檔中的範本中,通常每個檔一個代碼段範本。 有關用於代碼段範本的 XML 架構的詳細資訊,請參閱[程式碼段架構參考](../../ide/code-snippets-schema-reference.md)。 每個程式碼段範本都使用語言 ID 標識。 此語言 ID 在註冊表中指定,並放入`Language`範\<本 中代碼>標記的屬性中。

 儲存代碼段範本檔的通常有兩個位置:1) 安裝語言的位置和 2) 在使用者的資料夾中。 這些位置將添加到註冊表中,以便可視化工作室**代碼代碼段管理器**可以找到代碼段。 使用者的資料夾是存儲使用者創建的代碼段的位置。

 已安裝的代碼段範本檔的典型資料夾佈局如下所示 *:[安裝Root]*\\ *[測試語言]*\\[代碼段 *[LCID]*[片段。

 *[安裝Root]* 是您的語言安裝的資料夾。

 *[測試語言]* 是您的語言的名稱作為資料夾名稱。

 *[LCID]* 是區域設置 ID。 這是存儲代碼段的當地語系化版本的方式。 例如,英語區域設置 ID 為 1033,因此 *[LCID]* 替換為 1033。

 必須提供一個附加檔,該檔是索引檔,通常稱為 SnippetsIndex.xml 或擴展索引.xml(您可以使用以 .xml 結尾的任何有效檔名)。 此檔案通常儲存在 *[InstallRoot]*\\ *[Test語言]* 資料夾中,並指定代碼段資料夾的確切位置以及使用代碼段的語言服務的語言 ID 和 GUID。 索引檔的確切路徑被放入註冊表中,如後面的"安裝註冊表條目"中所述。 下面是 SnippetsIndex.xml 檔的範例:

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

 語言\<>标记指定语言`Lang`ID( 屬性) 和語言服務 GUID。

 本示例假定您已在 Visual Studio 安裝資料夾中安裝了語言服務。 %LCID% 取代為使用者的當前區域設定 ID。 可以\<添加多個代碼段>標記,每個不同的目錄和區域設置一個。 此外,程式碼段資料夾可以包含子資料夾,每個子資料夾都標識在索引檔中,其中包含嵌入\<\<在代碼段>標記中的 SnippetSubDir> 標記。

 使用者還可以為您的語言創建自己的代碼段。 這些代碼通常儲存在使用者的設置資料夾中,例如 *[TestDocs]*[代碼\\代碼段 *]測試語言][* 測試代碼代碼片段],其中 *[TestDocs]* 是可視化工作室的使用者設置資料夾的位置。

 以下替換元素可以放置在索引檔中\<的 DirPath> 標記中儲存的路徑中。

|元素|描述|
|-------------|-----------------|
|%LCID%|區域設置識別碼。|
|%安裝根百分比|Visual Studio 的根安裝資料夾,例如,C:*程式檔\微軟可視化工作室 8。|
|%贊成率|包含當前項目的資料夾。|
|%ProjItem%|包含當前項目項的資料夾。|
|% 測試文件百分比|使用者設置資料夾中的資料夾,例如,C:\文檔和\\設置 *[使用者名]*[我的文檔]可視化工作室\8。|

### <a name="enabling-code-snippets-for-your-language-service"></a>為您的語言服務啟用代碼段
 您可以透過<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>將 屬性添加到 VSPackage 來啟用語言服務的程式碼段(有關詳細資訊,請參閱[註冊舊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md))。 和<xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A><xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A>參數是可選的,但應`SearchPaths`包含命名參數,以便通知**代碼段管理器**代碼段代碼段的位置。

 以下是如何使用此屬性的範例:

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
 語言服務控制任何代碼段的插入,以及調用插入的方式。

## <a name="calling-the-expansion-provider-for-code-snippets"></a>呼叫程式的程式
 有兩種方法可以調用擴展提供程式:通過使用功能表命令或使用完成清單中的快捷方式。

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>使用選單指令插入代碼段
 要使用功能表命令顯示代碼段瀏覽器,請添加功能表命令,然後在<xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A><xref:Microsoft.VisualStudio.Package.ExpansionProvider>介面中調用 方法以響應該功能表命令。

1. 向 .vsct 檔案添加命令和按鈕。 您可以在[使用選單指令建立擴充](../../extensibility/creating-an-extension-with-a-menu-command.md)時找到執行此操作的說明。

2. 從<xref:Microsoft.VisualStudio.Package.ViewFilter>類派生類並重<xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A>寫 方法以指示對新功能表命令的支援。 此示例始終啟用功能表命令。

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

3. 重寫類<xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A><xref:Microsoft.VisualStudio.Package.ViewFilter>中 的方法<xref:Microsoft.VisualStudio.Package.ExpansionProvider>以獲取 該物件,並調用<xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A>該物件上 的方法。

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

     在插入代碼段的過程中<xref:Microsoft.VisualStudio.Package.ExpansionProvider>,Visual Studio 按給定的順序呼叫類別中的以下方法:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     呼叫<xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>方法後,已插入代碼段,<xref:Microsoft.VisualStudio.Package.ExpansionProvider>並且物件處於用於修改剛剛插入的代碼段的特殊編輯模式。

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>使用快捷方式插入程式碼段
 從完成清單中實現快捷方式比實現功能表命令要涉及得多。 您必須首先將代碼段快捷方式添加到 IntelliSense 單詞完成清單中。 然後,您必須檢測何時由於完成而插入了代碼段快捷方式名稱。 最後,您必須使用快捷方式名稱獲取代碼段標題和路徑,並將該資訊傳遞給<xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A><xref:Microsoft.VisualStudio.Package.ExpansionProvider>方法上的方法。

 要將代碼段快捷方式添加到單詞完成清單中,請將它們添加到<xref:Microsoft.VisualStudio.Package.Declarations><xref:Microsoft.VisualStudio.Package.AuthoringScope>類中的物件。 您必須確保可以將快捷方式標識為代碼段名稱。 例如,請參閱[演練:獲取已安裝的代碼段清單(舊版實現)。](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 可以檢測類<xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A>方法中的代碼段快捷方式<xref:Microsoft.VisualStudio.Package.Declarations>的 插入。 由於代碼段名稱已插入到源檔中,因此在插入擴展時必須將其刪除。 該方法<xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>採用一個範圍來描述代碼段的插入點;如果範圍包含原始檔中的整個代碼段名稱,則該名稱將被代碼段替換。

 下面是一個<xref:Microsoft.VisualStudio.Package.Declarations>類的版本,該類處理具有快捷方式名稱的代碼段插入。 為了清楚起見,<xref:Microsoft.VisualStudio.Package.Declarations>省略了類中的其他方法。 請注意,此類的建構函式採用物件<xref:Microsoft.VisualStudio.Package.LanguageService>。 這可以從<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件的版本傳入(例如<xref:Microsoft.VisualStudio.Package.AuthoringScope>, 類的實現可能會在其構造函數<xref:Microsoft.VisualStudio.Package.LanguageService>中獲取 物件並將該物件`TestDeclarations`傳遞給類 構造函數)。

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

 當語言服務獲取快捷方式名稱時,它將調用<xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A>方法以獲取檔名和代碼段標題。 然後,<xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>語言服務<xref:Microsoft.VisualStudio.Package.ExpansionProvider>在 類中調用 方法以插入代碼段。 在插入代碼段的過程中,Visual <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Studio 在類中的給定順序調用了以下方法:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   有關獲取語言服務已安裝的代碼段清單的詳細資訊,請參閱[演練:獲取已安裝的代碼段清單(舊版實現)。](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

## <a name="implementing-the-expansionfunction-class"></a>實現擴充功能類別
 擴展函數是嵌入在代碼段範本中的命名函數,並返回要放置在欄位中的一個或多個值。 為了支援語言服務中的擴展函數,必須從<xref:Microsoft.VisualStudio.Package.ExpansionFunction>類派生一個類並實現方法<xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A>。 然後,<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>必須重寫類<xref:Microsoft.VisualStudio.Package.LanguageService>中 的方法,以便返回對所支援的每個擴展函<xref:Microsoft.VisualStudio.Package.ExpansionFunction>數的類版本的新實例化。 如果支援擴展函數中可能的值清單,則還必須重寫<xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A><xref:Microsoft.VisualStudio.Package.ExpansionFunction>類中的方法以返回這些值的清單。

 獲取參數或需要訪問其他欄位的擴展函數不應與可編輯欄位關聯,因為在調用擴展函數時,擴展提供程式可能無法完全初始化。 因此,擴展函數無法獲得其參數或任何其他欄位的值。

### <a name="example"></a>範例
 下面是如何實現稱為`GetName`的簡單擴展函數的示例。 每次實例化擴展函數時,此擴展函數都會將一個數位追加到基類名稱(這與每次插入關聯的代碼段時都對應)。

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
- [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)
- [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [代碼段](../../ide/code-snippets.md)
- [逐步解說︰取得已安裝程式碼片段 (舊版實作) 的清單](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
