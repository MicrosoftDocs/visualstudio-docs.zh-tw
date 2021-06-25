---
title: 執行舊版語言 Service2 |Microsoft Docs
description: 瞭解如何使用 managed package framework (MPF) ，來實行支援擴充語言服務功能的舊版語言服務。 第2部，共2部。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fca2548ddb0c8281241b14de0ec470cfe22db1a1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900118"
---
# <a name="implementing-a-legacy-language-service-2"></a>執行舊版語言服務2
若要使用 managed package framework (MPF) 來執行語言服務，您必須從類別衍生類別， <xref:Microsoft.VisualStudio.Package.LanguageService> 並執行下列抽象方法和屬性：

- <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 方法

- <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 方法

- <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法

- <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> 屬性

  如需有關如何執行這些方法和屬性的詳細資訊，請參閱下列適當章節。

  為了支援其他功能，您的語言服務可能必須從其中一個 MPF 語言服務類別衍生類別;例如，若要支援其他的功能表命令，您必須從類別衍生類別 <xref:Microsoft.VisualStudio.Package.ViewFilter> ，並覆寫數個命令處理方法 (如需詳細資料，請參閱 <xref:Microsoft.VisualStudio.Package.ViewFilter>) 。 <xref:Microsoft.VisualStudio.Package.LanguageService>類別會提供一些方法，這些方法會呼叫以建立各種類別的新實例，而您會覆寫適當的建立方法以提供類別的實例。 例如，您需要覆寫 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> 類別中的方法， <xref:Microsoft.VisualStudio.Package.LanguageService> 以傳回您自己的類別的實例 <xref:Microsoft.VisualStudio.Package.ViewFilter> 。 如需詳細資訊，請參閱「具現化自訂類別」一節。

  您的語言服務也可以提供自己的圖示，這些圖示會在許多地方使用。 例如，當顯示 IntelliSense 完成清單時，清單中的每個專案都可以有相關聯的圖示，將專案標記為方法、類別、命名空間、屬性，或您的語言所需的專案。 這些圖示用於所有 IntelliSense 清單、 **導覽** 列，以及 [ **錯誤清單** ] 工作視窗。 如需詳細資訊，請參閱下面的「語言服務影像」一節。

## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences 方法
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>方法一律會傳回類別的相同實例 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 。 <xref:Microsoft.VisualStudio.Package.LanguagePreferences>如果您的語言服務不需要任何其他喜好設定，則可以使用基類。 MPF 語言服務類別假設至少存在基類 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 。

### <a name="example"></a>範例
 此範例顯示方法的一般實作為 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 方法。 這個範例會使用基類 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 。

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
 這個方法 <xref:Microsoft.VisualStudio.Package.IScanner> 會傳回物件的實例，此實例會執行用來取得權杖及其類型和觸發程式的行導向剖析器或掃描器。 <xref:Microsoft.VisualStudio.Package.Colorizer>雖然掃描器也可以用來取得權杖型別和觸發程式，以序言更複雜的剖析作業，但此掃描器會用於顏色標示。 您必須提供可執行介面的類別 <xref:Microsoft.VisualStudio.Package.IScanner> ，而且您必須在介面上執行所有方法 <xref:Microsoft.VisualStudio.Package.IScanner> 。

### <a name="example"></a>範例
 此範例顯示方法的一般實作為 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 方法。 `TestScanner`類別 <xref:Microsoft.VisualStudio.Package.IScanner> 會執行介面 (不會顯示) 。

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
 根據許多不同的原因來剖析來源檔案。 這個方法會提供一個 <xref:Microsoft.VisualStudio.Package.ParseRequest> 物件，描述特定剖析作業所預期的內容。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法會叫用更複雜的剖析器，以判斷 token 功能和範圍。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法是用來支援 IntelliSense 作業以及括弧對稱。 即使您不支援這類的 advanced 作業，仍然必須傳回有效的 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 物件，而且需要您建立可執行介面的類別， <xref:Microsoft.VisualStudio.Package.AuthoringScope> 並在該介面上執行所有方法。 您可以從所有方法傳回 null 值，但 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 物件本身不能是 null 值。

### <a name="example"></a>範例
 此範例顯示方法和類別的最基本實作為 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.AuthoringScope> ，足以讓語言服務編譯和運作，而不需要實際支援任何更先進的功能。

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
 這個屬性會傳回語言服務的名稱。 這必須與註冊語言服務時所指定的名稱相同。 這個名稱會用在許多地方，最顯著的是 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 名稱用來存取登錄的類別。 這個屬性所傳回的名稱不能當地語系化，因為它在登錄中用於登錄專案和索引鍵名稱。

### <a name="example"></a>範例
 此範例顯示內容的一個可能的執行 <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> 。 請注意，此處的名稱是硬式編碼：應從資源檔取得實際名稱，才能用來註冊語言服務 (請參閱) [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md) 。

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
 您可以覆寫指定類別中的下列方法，以提供您自己的每個類別版本的實例。

### <a name="in-the-languageservice-class"></a>在 LanguageService 類別中

|方法|傳回的類別|描述|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|支援文字視圖的自訂新增。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|支援自訂文件屬性。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|支援 **巡覽列**。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|支援程式碼片段範本中的函數。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|若要支援程式碼片段 (此方法通常不會覆寫) 。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|若要支援自訂 <xref:Microsoft.VisualStudio.Package.ParseRequest> 結構 (此方法通常不會覆寫) 。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|支援格式化原始程式碼、指定批註字元和自訂方法簽章。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|支援其他功能表命令。|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|為了支援語法醒目提示 (此方法通常不會覆寫) 。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|支援存取語言喜好設定。 您必須執行這個方法，但是可以傳回基類的實例。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|提供剖析器，用來識別一行上的權杖類型。 這個方法必須實作為，而且 <xref:Microsoft.VisualStudio.Package.IScanner> 必須衍生自。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|提供剖析器，用來識別整個原始程式檔中的功能和範圍。 您必須執行這個方法，且必須傳回類別版本的實例 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 。 如果您只想要支援語法醒目提示 (需要 <xref:Microsoft.VisualStudio.Package.IScanner> 從方法傳回的剖析器 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>) ，您可以在此方法中執行任何動作，而不是傳回 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 其方法都傳回 null 值的類別版本。|

### <a name="in-the-source-class"></a>在來源類別中

|方法|傳回的類別|描述|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|若要自訂 IntelliSense 完成清單的顯示 (此方法通常不會覆寫) 。|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|錯誤清單工作清單中的支援標記;具體而言，除了開啟檔案並跳到造成錯誤的那一行之外，還支援其他功能。|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|用於自訂 IntelliSense 參數資訊工具提示的顯示。|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|用於支援批註程式碼。|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|用於在剖析作業期間收集資訊。|

### <a name="in-the-authoringscope-class"></a>在 AuthoringScope 類別中

|方法|傳回的類別|描述|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|提供宣告的清單，例如成員或類型。 這個方法必須已完成，但可能會傳回 null 值。 如果這個方法傳回有效的物件，則物件必須是您的類別版本的實例 <xref:Microsoft.VisualStudio.Package.Declarations> 。|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|提供指定內容的方法簽章清單。 這個方法必須已完成，但可能會傳回 null 值。 如果這個方法傳回有效的物件，則物件必須是您的類別版本的實例 <xref:Microsoft.VisualStudio.Package.Methods> 。|

## <a name="language-service-images"></a>語言服務映射
 若要提供整個語言服務所要使用的圖示清單，請覆寫 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> 類別中的方法， <xref:Microsoft.VisualStudio.Package.LanguageService> 並傳回 <xref:System.Windows.Forms.ImageList> 包含圖示的。 基底 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別會載入一組預設的圖示。 由於您在需要圖示的地方指定確切的影像索引，所以您如何排列自己的影像清單，完全由您決定。

### <a name="images-used-in-intellisense-completion-lists"></a>IntelliSense 完成清單中使用的影像
 針對 IntelliSense 完成清單，會針對類別的方法中的每個專案指定影像索引 <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> <xref:Microsoft.VisualStudio.Package.Declarations> ，如果您想要提供影像索引，則必須覆寫此專案。 從方法傳回的值 <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> 是在提供給類別的函式之影像清單中的索引 <xref:Microsoft.VisualStudio.Package.CompletionSet> ，也就是從類別中的方法傳回的相同影像清單 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> (<xref:Microsoft.VisualStudio.Package.CompletionSet> 當您覆寫 <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> 類別中的方法 <xref:Microsoft.VisualStudio.Package.Source> ，以提供不同的影像清單) 時，您可以變更要用於的影像清單。

### <a name="images-used-in-the-navigation-bar"></a>在巡覽列中使用的影像
 **巡覽列** 會顯示類型和成員的清單，並用於快速導覽，可顯示圖示。 這些圖示是從 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> 類別中的方法取得 <xref:Microsoft.VisualStudio.Package.LanguageService> ，而且無法專門針對 **巡覽列** 覆寫。 當代表下拉式方塊的清單填入類別中的方法時，會指定用於下拉式方塊中每一個專案的索引， <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> (查看 [舊版語言服務中的導覽列支援](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)) 。 這些映射索引是從剖析器以某種方式取得，通常是透過您的 <xref:Microsoft.VisualStudio.Package.Declarations> 類別版本。 取得索引的方式完全由您決定。

### <a name="images-used-in-the-error-list-task-window"></a>錯誤清單工作視窗中所使用的影像
 每當方法剖析器 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> (看到 [舊版語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) 遇到錯誤，並將該錯誤傳遞給 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> 類別中的方法時，錯誤 <xref:Microsoft.VisualStudio.Package.AuthoringSink> **清單** 工作視窗中就會回報錯誤。 圖示可以與工作視窗中出現的每個專案產生關聯，而該圖示來自于類別中的方法所傳回的相同影像清單 <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> 。 MPF 類別的預設行為是不顯示包含錯誤訊息的影像。 不過，您可以從類別衍生類別並覆寫方法，以覆寫這個行為 <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> 。 在該方法中，您會建立新的 <xref:Microsoft.VisualStudio.Package.DocumentTask> 物件。 在傳回該物件之前，您可以使用 <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> 物件上的屬性 <xref:Microsoft.VisualStudio.Package.DocumentTask> 來設定影像索引。 這看起來會像下面的範例。 請注意， `TestIconImageIndex` 是一種列舉，其中會列出所有圖示，而且是此範例特有的。 您可能會有不同的方式來識別語言服務中的圖示。

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
 基底 MPF 語言服務類別所提供的預設影像清單包含一些與較常見語言元素相關聯的圖示。 大部分的圖示都是以六個變化的組合排列，對應至公用、內部、friend、受保護、私用和快捷方式的存取概念。 例如，您可以根據方法的公用、受保護或私用不同的圖示來使用不同的圖示。

 下列列舉會指定每個圖示集的一般名稱，並指定相關聯的索引。 例如，根據列舉，您可以將受保護方法的映射索引指定為 `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected` 。 您可以視需要變更此列舉中的名稱。

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
