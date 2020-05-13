---
title: 實現傳統語言服務2 |微軟文件
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
ms.openlocfilehash: e435af68a893c923eafef744762c9da8505c3fb7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707668"
---
# <a name="implementing-a-legacy-language-service"></a>實作舊版語言服務
要使用託管套件框架 (MPF) 實現語言服務,必須<xref:Microsoft.VisualStudio.Package.LanguageService>從 類派生一個類並實現以下抽象方法和屬性:

- <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 方法

- <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 方法

- <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法

- <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> 屬性

  有關實現這些方法和屬性的詳細資訊,請參閱以下相應部分。

  為了支援其他功能,您的語言服務可能必須從 MPF 語言服務類之一派生一個類;例如,為了支援其他功能表命令,必須從<xref:Microsoft.VisualStudio.Package.ViewFilter>類派生一個類並重寫多個命令處理方法(有關詳細資訊,請參閱)。 <xref:Microsoft.VisualStudio.Package.ViewFilter> 該<xref:Microsoft.VisualStudio.Package.LanguageService>類提供了許多方法,這些方法被調用以創建各種類的新實例,並重寫適當的創建方法以提供類的實例。 例如,您需要重寫<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A><xref:Microsoft.VisualStudio.Package.LanguageService>類中的方法以返回您<xref:Microsoft.VisualStudio.Package.ViewFilter>自己的 類的實例。 有關詳細資訊,請參閱"即時自定義類"部分。

  您的語言服務還可以提供自己的圖示,這些圖示在許多地方使用。 例如,當顯示 IntelliSense 完成清單時,清單中的每個項都可以具有與其關聯的圖示,將項標記為方法、類、命名空間、屬性或任何語言所需的任何內容。 這些圖示用於所有 IntelliSense 列表、**導航列**和**錯誤清單**工作視窗中。 有關詳細資訊,請參閱下面的"語言服務圖像"部分。

## <a name="getlanguagepreferences-method"></a>取得語言偏好設定方法
 該方法<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>始終<xref:Microsoft.VisualStudio.Package.LanguagePreferences>返回 類的相同實例。 如果不需要語言服務的任何其他<xref:Microsoft.VisualStudio.Package.LanguagePreferences>首選項,則可以使用基類。 MPF 語言服務類假定至少存在<xref:Microsoft.VisualStudio.Package.LanguagePreferences>基 類。

### <a name="example"></a>範例
 此示例顯示了<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>該方法的典型實現。 此示例使用基<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類。

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

## <a name="getscanner-method"></a>抓取掃描器方法
 此方法返回一個<xref:Microsoft.VisualStudio.Package.IScanner>物件的實例,該物件實現用於獲取令牌及其類型和觸發器的面向行解析器或掃描器。 此掃描器用於著色類,<xref:Microsoft.VisualStudio.Package.Colorizer>儘管掃描器還可用於獲取權杖類型和觸發器,作為更複雜的分析操作的前奏。 必須提供實現介面的<xref:Microsoft.VisualStudio.Package.IScanner>類,並且必須實現<xref:Microsoft.VisualStudio.Package.IScanner>介面上的所有方法。

### <a name="example"></a>範例
 此示例顯示了<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>該方法的典型實現。 類`TestScanner`<xref:Microsoft.VisualStudio.Package.IScanner>實現介面(未顯示)。

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

## <a name="parsesource-method"></a>解析來源方法
 基於許多不同的原因分析源檔。 此方法被賦予一個<xref:Microsoft.VisualStudio.Package.ParseRequest>物件,該物件描述特定分析操作的預期內容。 該方法<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>調用一個更複雜的解析器,用於確定令牌功能和範圍。 該方法<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>用於支援 IntelliSense 操作和大括弧匹配。 即使您不支援此類高級操作,您仍必須返回一個有效的<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件,並且需要創建一個<xref:Microsoft.VisualStudio.Package.AuthoringScope>實現介面並在該介面上實現所有方法的類。 可以從所有方法傳回 null<xref:Microsoft.VisualStudio.Package.AuthoringScope>值, 但物件本身不能為空值。

### <a name="example"></a>範例
 此示例顯示了<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法<xref:Microsoft.VisualStudio.Package.AuthoringScope>和 類的最小實現,足以允許語言服務編譯和運行,而無需實際支援任何更高級的功能。

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
 此屬性返回語言服務的名稱。 這必須與註冊語言服務時給出的名稱相同。 此名稱用於多個位置,其中最突出的是使用該名稱訪問註冊表的<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類。 此屬性返回的名稱不能當地語系化,因為它在註冊表中用於註冊表項和密鑰名稱。

### <a name="example"></a>範例
 此示例顯示<xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>屬性的一個可能實現。 請注意,此處的名稱是硬編碼的:實際名稱應從資源檔獲取,以便可用於註冊語言服務(請參閱[註冊舊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md))。

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

## <a name="instantiating-custom-classes"></a>實體化自訂類別
 可以重寫指定類中的以下方法,以提供每個類的自己版本的實例。

### <a name="in-the-languageservice-class"></a>在語言服務類別

|方法|返回的類|描述|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|支援對文本檢視的自定義添加。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|支援自定義文件屬性。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|支援**導覽列**。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|支援代碼段範本中的函數。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|支援代碼段(此方法通常不會重寫)。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|支援結構的<xref:Microsoft.VisualStudio.Package.ParseRequest>自定義(此方法通常不會重寫)。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|支援設定原始碼的格式,指定註釋字元和自定義方法簽名。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|支援其他功能表命令。|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|支援語法突出顯示(此方法通常不會重寫)。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|支持訪問語言首選項。 必須實現此方法,但可以返回基類的實例。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|提供用於標識行上權杖類型的解析器。 此方法必須實現,並且必須<xref:Microsoft.VisualStudio.Package.IScanner>派生自此方法。|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|提供用於標識整個源檔中的功能和範圍的解析器。 此方法必須實現,並且必須返回<xref:Microsoft.VisualStudio.Package.AuthoringScope>類版本的實例。 如果只想支援的只是語法突出顯示(這需要從<xref:Microsoft.VisualStudio.Package.IScanner><xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法返回的解析器),則除了<xref:Microsoft.VisualStudio.Package.AuthoringScope>返回 該方法都返回 null 值的類版本外,此方法中沒有任何操作。|

### <a name="in-the-source-class"></a>在源類中

|方法|返回的類|描述|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|要自訂 IntelliSense 完成清單的顯示(此方法通常不會重寫)。|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|有關錯誤清單工作列表中的支持標記;具體來說,除了打開檔和跳轉到導致錯誤的行之外,還支援功能。|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|用於自訂 IntelliSense 參數資訊工具提示的顯示。|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|用於支援註釋代碼。|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|用於在分析操作期間收集資訊。|

### <a name="in-the-authoringscope-class"></a>在創作範圍類別

|方法|返回的類|描述|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|提供聲明清單,如成員或類型。 必須實現此方法,但可以返回 null 值。 如果此方法返回有效物件,則該對象必須<xref:Microsoft.VisualStudio.Package.Declarations>是 類版本的實例。|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|提供給定上下文的方法簽名清單。 必須實現此方法,但可以返回 null 值。 如果此方法返回有效物件,則該對象必須<xref:Microsoft.VisualStudio.Package.Methods>是 類版本的實例。|

## <a name="language-service-images"></a>語言服務影像
 要提供整個語言服務中使用的圖示清單,請重寫<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A><xref:Microsoft.VisualStudio.Package.LanguageService>類中的方法並返回包含圖示的 圖<xref:System.Windows.Forms.ImageList>示。 基<xref:Microsoft.VisualStudio.Package.LanguageService>類載入一組預設的圖示。 由於在需要圖示的地方指定了確切的圖像索引,因此如何排列自己的圖像清單完全取決於您。

### <a name="images-used-in-intellisense-completion-lists"></a>在「感知完成清單」 中使用的影像
 對於 IntelliSense 完成清單<xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A><xref:Microsoft.VisualStudio.Package.Declarations>,為 類方法中的每個項指定了圖像索引,如果要提供圖像索引,則必須重寫該項。 從<xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A>方法返回的值是提供<xref:Microsoft.VisualStudio.Package.CompletionSet>給 類構造函數的圖像清單中的索引,<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A><xref:Microsoft.VisualStudio.Package.LanguageService>它是從 類中的方法返回的相同<xref:Microsoft.VisualStudio.Package.CompletionSet>圖像清單(<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A><xref:Microsoft.VisualStudio.Package.Source>如果重寫 類中的方法以提供不同的圖像清單,則可以更改要使用的圖像清單)。

### <a name="images-used-in-the-navigation-bar"></a>導覽列中使用的影像
 **導航列**顯示類型和成員的清單,用於快速導航可以顯示圖示。 這些圖示是從類中的方法<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>獲取的<xref:Microsoft.VisualStudio.Package.LanguageService>, 不能專門針對**導航欄**進行重寫。 當表示組合框的清單在<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A><xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>類中填充方法時,將指定用於組合框中每個專案的索引(請參閱[舊語言服務中導航欄的支援](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md))。 這些圖像索引以某種方式從解析器獲得,通常是通過<xref:Microsoft.VisualStudio.Package.Declarations>類的版本獲得的。 如何獲得指數完全由您決定。

### <a name="images-used-in-the-error-list-task-window"></a>錯誤清單工作視窗中使用的影像
 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>每當方法解析器(請參閱[舊語言服務解析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md))遇到錯誤並將該<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>錯誤<xref:Microsoft.VisualStudio.Package.AuthoringSink>傳遞給 類中的方法時,錯誤將在**錯誤列表**任務視窗中報告。 圖示可以與任務視窗中顯示的每個項相關聯,並且該圖示來自從<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A><xref:Microsoft.VisualStudio.Package.LanguageService>類中的方法返回的相同圖像清單。 MPF 類的默認行為是不顯示帶有錯誤消息的圖像。 但是,您可以通過<xref:Microsoft.VisualStudio.Package.Source>從 類派生類並重寫<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>方法來 重寫此行為。 在該方法中,您將創建一個新<xref:Microsoft.VisualStudio.Package.DocumentTask>物件。 在傳回該物件之前<xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A>,<xref:Microsoft.VisualStudio.Package.DocumentTask>可以使用 物件上的屬性來設置圖像索引。 這類似於下面的示例。 請注意,`TestIconImageIndex`這是一個枚舉,列出所有圖示,並特定於此示例。 您可能有不同的方法來識別語言服務中的圖示。

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

## <a name="the-default-image-list-for-a-language-service"></a>語言服務的預設映像清單
 基本 MPF 語言服務類附帶的預設映射清單包含許多與更常見語言元素關聯的圖示。 這些圖示的大部分排列在六種變體中,對應於公共、內部、朋友、受保護、私有和快捷方式的訪問概念。 例如,根據方法是公共圖示、受保護圖示還是私有圖示,可以為方法使用不同的圖示。

 以下枚舉為每個圖示集指定典型名稱,並指定關聯的索引。 例如,根據枚舉,可以將受保護方法的影像索引指定為`(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`。 您可以根據需要更改此枚舉中的名稱。

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
