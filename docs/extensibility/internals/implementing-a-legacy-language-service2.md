---
title: 執行舊版語言 Service2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df44b92cdf311689397a062b127d4c3e514a15e6
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238695"
---
# <a name="implementing-a-legacy-language-service-2"></a>執行舊版語言服務2
若要使用受管理的封裝架構 (MPF) 來執行語言服務，您必須從類別衍生類別， <xref:Microsoft.VisualStudio.Package.LanguageService> 並執行下列抽象方法和屬性：

- <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 方法

- <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 方法

- <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法

- <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> 屬性

  如需有關如何執行這些方法和屬性的詳細資訊，請參閱下面的適當章節。

  若要支援其他功能，您的語言服務可能必須從其中一個 MPF 語言服務類別衍生類別;例如，若要支援其他的功能表命令，您必須從類別衍生類別 <xref:Microsoft.VisualStudio.Package.ViewFilter> ，並覆寫數個命令處理方法 (參閱 <xref:Microsoft.VisualStudio.Package.ViewFilter> 以取得詳細資料) 。 <xref:Microsoft.VisualStudio.Package.LanguageService>類別提供數種方法，可供呼叫以建立各種類別的新實例，而且您會覆寫適當的建立方法，以提供類別的實例。 例如，您必須覆寫 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> 類別中的方法， <xref:Microsoft.VisualStudio.Package.LanguageService> 以傳回您自己的類別的實例 <xref:Microsoft.VisualStudio.Package.ViewFilter> 。 如需詳細資訊，請參閱「具現化自訂類別」一節。

  您的語言服務也可以提供自己的圖示，用於許多地方。 例如，當顯示 IntelliSense 完成清單時，清單中的每個專案都可以有與其相關聯的圖示、將專案標記為方法、類別、命名空間、屬性，或語言所需的內容。 這些圖示會用於所有 IntelliSense 清單、 **導覽**列，以及 [ **錯誤清單** 工作] 視窗中。 如需詳細資訊，請參閱下面的「語言服務映射」一節。

## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences 方法
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>方法一律會傳回類別的相同實例 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 。 <xref:Microsoft.VisualStudio.Package.LanguagePreferences>如果您的語言服務不需要任何額外的喜好設定，則可以使用基類。 MPF 語言服務類別會假設至少存在基類 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 。

### <a name="example"></a>範例
 這個範例會示範方法的一般執行 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 。 這個範例會使用基類 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 。

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(TestLanguageService).GUID,
                                                        this.Name );
                m_preferences.Init();
            }
            return m_preferences;
        }
    }
}
```

## <a name="getscanner-method"></a>GetScanner 方法
 這個方法會傳回物件的實例 <xref:Microsoft.VisualStudio.Package.IScanner> ，其會執行用來取得權杖及其類型和觸發程式的行導向剖析器或掃描器。 此掃描器會在類別中用於顏色標示， <xref:Microsoft.VisualStudio.Package.Colorizer> 不過掃描器也可以用來取得權杖類型和觸發程式，以序言更複雜的剖析作業。 您必須提供可實作為介面的類別， <xref:Microsoft.VisualStudio.Package.IScanner> 而且您必須在介面上執行所有方法 <xref:Microsoft.VisualStudio.Package.IScanner> 。

### <a name="example"></a>範例
 這個範例會示範方法的一般執行 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 。 `TestScanner`類別 <xref:Microsoft.VisualStudio.Package.IScanner> 會執行介面， (不會顯示) 。

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private TestScanner m_scanner;

        public override IScanner GetScanner(IVsTextLines buffer)
        {
            if (m_scanner == null)
            {
                m_scanner = new TestScanner(buffer);
            }
            return m_scanner;
        }
    }
}
    internal class TestScanner : IScanner
    {
        private IVsTextBuffer m_buffer;
        string m_source;

        public TestScanner(IVsTextBuffer buffer)
        {
            m_buffer = buffer;
        }

        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)
        {
            tokenInfo.Type = TokenType.Unknown;
            tokenInfo.Color = TokenColor.Text;
            return true;
        }

        void IScanner.SetSource(string source, int offset)
        {
            m_source = source.Substring(offset);
        }
    }

```

## <a name="parsesource-method"></a>ParseSource 方法
 根據幾個不同的原因剖析來源檔案。 這個方法會提供一個 <xref:Microsoft.VisualStudio.Package.ParseRequest> 物件，描述特定剖析作業預期的內容。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法會叫用更複雜的剖析器，以判斷權杖功能和範圍。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法是用來支援 IntelliSense 作業以及括弧對稱。 即使您不支援這類的 advanced 作業，仍然必須傳回有效的 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 物件，而且需要您建立一個類別來 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 執行介面，並在該介面上實作為所有方法。 您可以從所有方法傳回 null 值，但 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 物件本身不得為 null 值。

### <a name="example"></a>範例
 這個範例顯示方法和類別的最小化執行 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.AuthoringScope> ，足以讓語言服務編譯和運作，而不需要實際支援任何更先進的功能。

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            return new TestAuthoringScope();
        }
    }

    internal class TestAuthoringScope : AuthoringScope
    {
        public override string GetDataTipText(int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return null;
        }

        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Methods GetMethods(int line, int col, string name)
        {
            return null;
        }
}
```

## <a name="name-property"></a>Name 屬性
 這個屬性會傳回語言服務的名稱。 這必須是註冊語言服務時所指定的相同名稱。 這個名稱會用於數個地方，最重要的是 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 使用名稱來存取登錄的類別。 這個屬性所傳回的名稱不能當地語系化，因為它用於登錄專案和機碼名稱。

### <a name="example"></a>範例
 這個範例會顯示內容的一個可能的執行 <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> 。 請注意，此處的名稱是硬式編碼：您應該從資源檔取得實際名稱，以便用來註冊語言服務 (請參閱 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)) 。

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override string Name
        {
            get { return "Test Language"; }
        }
    }
}
```

## <a name="instantiating-custom-classes"></a>具現化自訂類別
 您可以覆寫指定類別中的下列方法，以提供您自己版本的每個類別的實例。

### <a name="in-the-languageservice-class"></a>在 LanguageService 類別中

|方法|傳回的類別|描述|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|支援文字視圖的自訂新增專案。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|支援自訂文件屬性。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|以支援 **巡覽列**。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|支援程式碼片段範本中的函式。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|若要支援程式碼片段 (這個方法通常不會) 覆寫。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|為了支援自訂 <xref:Microsoft.VisualStudio.Package.ParseRequest> 結構 (這個方法通常不會) 覆寫。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|支援格式化原始程式碼、指定批註字元，以及自訂方法簽章。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|以支援其他功能表命令。|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|若要支援語法反白顯示 (通常不會覆寫此方法) 。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|支援存取語言喜好設定。 這個方法必須實作為，但可以傳回基類的實例。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|提供剖析器，用於識別行上的權杖類型。 這個方法必須實作為，而且 <xref:Microsoft.VisualStudio.Package.IScanner> 必須衍生自。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|提供剖析器，用來識別整個原始程式檔中的功能和範圍。 這個方法必須實作為，而且必須傳回類別版本的實例 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 。 如果您想要支援的語法反白顯示 (需要 <xref:Microsoft.VisualStudio.Package.IScanner> 從方法傳回的剖析器 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>) ，您可以在這個方法中執行任何動作，而不是傳回類別的版本， <xref:Microsoft.VisualStudio.Package.AuthoringScope> 其方法全都會傳回 null 值。|

### <a name="in-the-source-class"></a>在來源類別中

|方法|傳回的類別|描述|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|若要自訂 IntelliSense 完成清單的顯示 (這個方法通常不會覆寫) 。|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|錯誤清單工作清單中的支援標記;具體而言，支援開啟檔案以外的功能，並跳至造成錯誤的那一行。|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|用於自訂 IntelliSense 參數資訊工具提示的顯示。|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|用於支援的批註程式碼。|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|用於在剖析作業期間收集資訊。|

### <a name="in-the-authoringscope-class"></a>在 AuthoringScope 類別中

|方法|傳回的類別|描述|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|提供宣告的清單，例如成員或類型。 這個方法必須實作為，但可以傳回 null 值。 如果這個方法傳回有效的物件，物件必須是您的類別版本的實例 <xref:Microsoft.VisualStudio.Package.Declarations> 。|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|提供給定內容的方法簽章清單。 這個方法必須實作為，但可以傳回 null 值。 如果這個方法傳回有效的物件，物件必須是您的類別版本的實例 <xref:Microsoft.VisualStudio.Package.Methods> 。|

## <a name="language-service-images"></a>語言服務映射
 若要提供整個語言服務所要使用的圖示清單，請覆寫 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> 類別中的方法， <xref:Microsoft.VisualStudio.Package.LanguageService> 並傳回 <xref:System.Windows.Forms.ImageList> 包含圖示的。 基類會 <xref:Microsoft.VisualStudio.Package.LanguageService> 載入一組預設的圖示。 因為您在需要圖示的位置上指定確切的影像索引，所以您要如何安排自己的影像清單，完全由您決定。

### <a name="images-used-in-intellisense-completion-lists"></a>IntelliSense 完成清單中使用的影像
 針對 IntelliSense 完成清單，會為類別的方法中的每個專案指定影像索引 <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> <xref:Microsoft.VisualStudio.Package.Declarations> ，如果您想要提供影像索引，則必須覆寫此索引。 從方法傳回的值 <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> 是提供給類別的函式之影像清單的索引 <xref:Microsoft.VisualStudio.Package.CompletionSet> ，而且是從類別中的方法所傳回的相同影像清單 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> (<xref:Microsoft.VisualStudio.Package.CompletionSet> 如果您覆寫 <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> 類別中的方法 <xref:Microsoft.VisualStudio.Package.Source> ，以提供不同的影像清單) ，則可以變更要用於的影像清單。

### <a name="images-used-in-the-navigation-bar"></a>導覽列中使用的影像
 **巡覽列**會顯示類型和成員的清單，並用於快速導覽，可以顯示圖示。 這些圖示是從 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> 類別中的方法取得 <xref:Microsoft.VisualStudio.Package.LanguageService> ，而且無法特別針對 **導覽**列加以覆寫。 當代表下拉式方塊的清單已填入類別中的方法時，會指定下拉式方塊中的每個專案所使用的索引， <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> (在 [舊版語言服務) 中查看對巡覽列的支援](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md) 。 這些影像索引是以某種方式從剖析器取得，通常是透過您的 <xref:Microsoft.VisualStudio.Package.Declarations> 類別版本。 取得索引的方式完全取決於您。

### <a name="images-used-in-the-error-list-task-window"></a>錯誤清單工作視窗中使用的影像
 每當方法剖析器 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> (看到 [舊版語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) 遇到錯誤，並將該錯誤傳遞至 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> 類別中的方法時 <xref:Microsoft.VisualStudio.Package.AuthoringSink> ，就會在 [ **錯誤清單** 工作] 視窗中報告錯誤。 圖示可以與出現在工作視窗中的每個專案相關聯，而該圖示來自于類別中的方法所傳回的相同影像清單 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> 。 MPF 類別的預設行為是不要顯示包含錯誤訊息的影像。 不過，您可以藉由從類別衍生類別並覆寫方法，來覆寫此行為 <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> 。 在該方法中，您會建立新的 <xref:Microsoft.VisualStudio.Package.DocumentTask> 物件。 傳回該物件之前，您可以使用 <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> 物件上的屬性 <xref:Microsoft.VisualStudio.Package.DocumentTask> 來設定影像索引。 這看起來會如下列範例所示。 請注意， `TestIconImageIndex` 是一個列舉，它會列出所有圖示，而且是此範例特有的。 在語言服務中，您可能會有不同的方式來識別圖示。

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestSource : Source
    {
        public override DocumentTask CreateErrorTaskItem(
            TextSpan          span,
            string            filename,
            string            message,
            TaskPriority      priority,
            TaskCategory      category,
            MARKERTYPE        markerType,
            TaskErrorCategory errorCategory)
        {
            DocumentTask taskItem = base.CreateErrorTaskItem(
                                           span,
                                           filename,
                                           message,
                                           priority,
                                           category,
                                           markerType,
                                           errorCategory);
            if (errorCategory == TaskErrorCategory.Error)
            {
                taskItem.ImageIndex = TestIconImageIndex.Error;
            }
            return taskItem;
        }
    }
}
```

## <a name="the-default-image-list-for-a-language-service"></a>語言服務的預設影像清單
 基底 MPF 語言服務類別所提供的預設影像清單，包含一些與較常見語言專案相關聯的圖示。 這些圖示大部分都是以六種不同的集合來排列，並對應至公用、內部、friend、protected、private 和快捷方式的存取概念。 例如，根據是公用、受保護或私用，您可以有不同的方法圖示。

 下列列舉會指定每個圖示集的一般名稱，並指定相關聯的索引。 例如，您可以根據列舉，將受保護方法的影像索引指定為 `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected` 。 您可以視需要變更此列舉型別中的名稱。

```csharp
public enum IconImageIndex
        {
            // access types
            AccessPublic = 0,
            AccessInternal = 1,
            AccessFriend = 2,
            AccessProtected = 3,
            AccessPrivate = 4,
            AccessShortcut = 5,

            Base = 6,
            // Each of the following icon type has 6 versions,
            //corresponding to the access types
            Class = Base + 0,
            Constant = Base + 1,
            Delegate = Base + 2,
            Enumeration = Base + 3,
            EnumMember = Base + 4,
            Event = Base + 5,
            Exception = Base + 6,
            Field = Base + 7,
            Interface = Base + 8,
            Macro = Base + 9,
            Map = Base + 10,
            MapItem = Base + 11,
            Method = Base + 12,
            OverloadedMethod = Base + 13,
            Module = Base + 14,
            Namespace = Base + 15,
            Operator = Base + 16,
            Property = Base + 17,
            Struct = Base + 18,
            Template = Base + 19,
            Typedef = Base + 20,
            Type = Base + 21,
            Union = Base + 22,
            Variable = Base + 23,
            ValueType = Base + 24,
            Intrinsic = Base + 25,
            JavaMethod = Base + 26,
            JavaField = Base + 27,
            JavaClass = Base + 28,
            JavaNamespace = Base + 29,
            JavaInterface = Base + 30,
            // Miscellaneous icons with one icon for each type.
            Error = 187,
            GreyedClass = 188,
            GreyedPrivateMethod = 189,
            GreyedProtectedMethod = 190,
            GreyedPublicMethod = 191,
            BrowseResourceFile = 192,
            Reference = 193,
            Library = 194,
            VBProject = 195,
            VBWebProject = 196,
            CSProject = 197,
            CSWebProject = 198,
            VB6Project = 199,
            CPlusProject = 200,
            Form = 201,
            OpenFolder = 202,
            ClosedFolder = 203,
            Arrow = 204,
            CSClass = 205,
            Snippet = 206,
            Keyword = 207,
            Info = 208,
            CallBrowserCall = 209,
            CallBrowserCallRecursive = 210,
            XMLEditor = 211,
            VJProject = 212,
            VJClass = 213,
            ForwardedType = 214,
            CallsTo = 215,
            CallsFrom = 216,
            Warning = 217,
        }
```

## <a name="see-also"></a>另請參閱
- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [舊版語言服務概觀](../../extensibility/internals/legacy-language-service-overview.md)
- [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [舊版語言服務的剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
