---
title: "實作舊版語言 Service2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 20dc3cf7b4db090bf7fcd0086b3e72575d8490cd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-a-legacy-language-service"></a>實作舊版語言服務
若要實作語言服務使用 managed 的 package framework (MPF)，您必須衍生自<xref:Microsoft.VisualStudio.Package.LanguageService>類別並實作下列的抽象方法和屬性：  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 方法  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 方法  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> 屬性  
  
 實作這些方法和屬性，請參閱以下以取得詳細資料之適當章節。  
  
 若要支援其他功能，語言服務可能必須從一個 MPF 語言服務類別，衍生類別比方說，若要支援其他功能表命令，您必須衍生自<xref:Microsoft.VisualStudio.Package.ViewFilter>類別並覆寫數個處理方法的命令 (請參閱<xref:Microsoft.VisualStudio.Package.ViewFilter>如需詳細資訊)。 <xref:Microsoft.VisualStudio.Package.LanguageService>類別提供了一些方法呼叫來建立各種不同類別的新執行個體，而且您覆寫適當的建立方法以提供您類別的執行個體。 例如，您需要覆寫<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>方法中的<xref:Microsoft.VisualStudio.Package.LanguageService>類別，以傳回自己的執行個體<xref:Microsoft.VisualStudio.Package.ViewFilter>類別。 請參閱 < 具現化自訂類別 > 一節，如需詳細資訊。  
  
 語言服務也可以提供自己的圖示，在許多地方使用。 比方說，當 IntelliSense 完成清單會顯示，在清單中的每個項目可以有與其相關聯，將郵件標示為方法、 類別、 命名空間、 屬性、 圖示或任何需要您的語言。 這些圖示用在所有的 IntelliSense 清單**導覽列**，然後在**錯誤清單**工作 視窗。 請參閱 語言服務映像 「 下的一節以取得詳細資料。  
  
## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences 方法  
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>方法永遠都會傳回相同的執行個體<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別。 您可以使用基底<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別，如果您不需要任何額外的語言服務喜好設定。 MPF 語言服務類別假設存在最少為基底<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別。  
  
### <a name="example"></a>範例  
 這個範例示範典型實作<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>方法。 這個範例會使用基底<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別。  
  
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
 這個方法傳回的執行個體<xref:Microsoft.VisualStudio.Package.IScanner>掃描器用來取得權杖及其類型和觸發程序或資料列導向的剖析器會實作的物件。 用於此掃描器<xref:Microsoft.VisualStudio.Package.Colorizer>雖然掃描器也可用來取得語彙基元類型及觸發程序，為更複雜的剖析作業 prelude 顏色標示的類別。 您必須提供實作的類別<xref:Microsoft.VisualStudio.Package.IScanner>介面，而且您必須實作所有方法上<xref:Microsoft.VisualStudio.Package.IScanner>介面。  
  
### <a name="example"></a>範例  
 這個範例示範典型實作<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法。 `TestScanner`類別會實作<xref:Microsoft.VisualStudio.Package.IScanner>介面 （未顯示）。  
  
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
 剖析來源檔案，根據數個不同的原因。 這個方法給予<xref:Microsoft.VisualStudio.Package.ParseRequest>物件，描述特定的剖析作業有何預期。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法會叫用更複雜的剖析器會決定 token 的功能和領域。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法用於支援 IntelliSense 作業以及括號對稱。 即使您並不支援這類進階的操作，您仍然必須傳回有效<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件，且需要您建立類別，實作<xref:Microsoft.VisualStudio.Package.AuthoringScope>介面，並實作該介面上的所有方法。 您可以從所有方法傳回 null 值，但<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件本身不能為 null 值。  
  
### <a name="example"></a>範例  
 此範例中顯示的最小實作<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法和<xref:Microsoft.VisualStudio.Package.AuthoringScope>類別，可讓語言服務編譯並沒有實際支援更進階的任何的功能函式。  
  
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
 這個屬性傳回之語言服務的名稱。 這必須是已註冊之語言服務時提供的相同名稱。 這個名稱用於的多個地方，其中最重要的是<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別名稱用於存取登錄。 傳回這個屬性的名稱必須不會當地語系化，因為它正使用登錄中的登錄項目和索引鍵的名稱。  
  
### <a name="example"></a>範例  
 這個範例示範可能的實作<xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>屬性。 請注意，此處的名稱是硬式編碼： 應該從資源檔取得的實際名稱，因此可用於註冊語言服務 (請參閱[註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md))。  
  
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
 指定的類別中的下列方法會覆寫以提供您自己的版本，每個類別的執行個體。  
  
### <a name="in-the-languageservice-class"></a>LanguageService 類別中  
  
|方法|傳回類別|描述|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|若要支援自訂文字檢視新增項目。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|若要支援自訂文件屬性。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|若要支援**導覽列**。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|若要在程式碼片段範本支援函式。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|若要支援 （此方法通常不會覆寫） 的程式碼片段。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|若要支援自訂<xref:Microsoft.VisualStudio.Package.ParseRequest>（此方法通常不會覆寫） 的結構。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|若要支援格式化的原始碼，指定註解字元，以及自訂方法簽章。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|若要支援其他功能表命令。|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|若要支援語法反白顯示 （此方法通常不會覆寫）。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|若要支援的語言喜好設定的存取。 必須實作這個方法，但可能會傳回基底類別的執行個體。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|提供用來識別類型的語彙基元的一行的剖析器。 必須實作這個方法和<xref:Microsoft.VisualStudio.Package.IScanner>必須衍生自。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|提供用來識別功能與範圍內的整個原始程式檔的剖析器。 這個方法必須實作，而且必須傳回您版本的執行個體<xref:Microsoft.VisualStudio.Package.AuthoringScope>類別。 如果您想要支援會反白顯示語法 (這需要<xref:Microsoft.VisualStudio.Package.IScanner>從傳回的剖析器<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法)，您可以執行任何動作以外傳回此方法中的版本<xref:Microsoft.VisualStudio.Package.AuthoringScope>其方法全都會傳回 null 值的類別。|  
  
### <a name="in-the-source-class"></a>來源類別中  
  
|方法|傳回類別|描述|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|自訂 IntelliSense 完成清單 （此方法通常不會覆寫） 的顯示。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|支援標記錯誤清單中的工作清單。具體來說，支援開啟檔案並跳到造成錯誤的一行以外的功能。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|自訂 IntelliSense 參數諮詢工具提示的顯示。|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|支援註解的程式碼。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|收集期間，剖析作業的資訊。|  
  
### <a name="in-the-authoringscope-class"></a>AuthoringScope 類別中  
  
|方法|傳回類別|描述|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|提供例如成員或類型宣告的清單。 必須實作這個方法，但可能會傳回 null 值。 如果這個方法會傳回有效的物件的物件必須是您的版本的執行個體<xref:Microsoft.VisualStudio.Package.Declarations>類別。|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|針對指定的內容中提供方法簽章的清單。 必須實作這個方法，但可能會傳回 null 值。 如果這個方法會傳回有效的物件的物件必須是您的版本的執行個體<xref:Microsoft.VisualStudio.Package.Methods>類別。|  
  
## <a name="language-service-images"></a>語言服務映像  
 若要提供的圖示，以在整個語言服務的清單，覆寫<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>方法中的<xref:Microsoft.VisualStudio.Package.LanguageService>類別，並傳回<xref:System.Windows.Forms.ImageList>包含圖示。 基底<xref:Microsoft.VisualStudio.Package.LanguageService>類別會載入一組預設的圖示。 因為您需要圖示那些位置中指定的確切的影像索引，您要如何安排您自己的映像清單是完全由您。  
  
### <a name="images-used-in-intellisense-completion-lists"></a>IntelliSense 完成清單中使用的影像  
 IntelliSense 完成清單，請指定每個項目映像索引<xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A>方法<xref:Microsoft.VisualStudio.Package.Declarations>類別，您必須覆寫，如果您想要提供的映像索引。 從傳回的值<xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A>方法是提供給影像清單索引<xref:Microsoft.VisualStudio.Package.CompletionSet>從傳回的類別建構函式，也就是相同的影像清單<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>方法中的<xref:Microsoft.VisualStudio.Package.LanguageService>類別 （您可以變更哪一個影像清單用於<xref:Microsoft.VisualStudio.Package.CompletionSet>如果您覆寫<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>方法中的<xref:Microsoft.VisualStudio.Package.Source>類別，以提供不同的影像清單)。  
  
### <a name="images-used-in-the-navigation-bar"></a>導覽列中使用的影像  
 **導覽列**顯示類型和成員的清單，並可快速瀏覽可以顯示圖示。 這些圖示會取自<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>方法中的<xref:Microsoft.VisualStudio.Package.LanguageService>類別，並無法特別針對覆寫**導覽列**。 表示下拉式方塊的清單會填入時，會指定用於下拉式方塊中的每個項目的索引<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>方法中的<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>類別 (請參閱[導覽列舊版語言服務的支援](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). 這些映像索引將以某種方式取得來自剖析器，通常是透過您的版本<xref:Microsoft.VisualStudio.Package.Declarations>類別。 如何取得索引是完全由您。  
  
### <a name="images-used-in-the-error-list-task-window"></a>[錯誤清單工作] 視窗中使用的影像  
 每當<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法剖析器 (請參閱[舊版語言服務剖析器與掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) 遇到錯誤，並將傳遞至該錯誤<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>方法中的<xref:Microsoft.VisualStudio.Package.AuthoringSink>類別會報告錯誤**錯誤清單**工作 視窗。 圖示可以出現在 [工作] 視窗中的每個項目與相關聯，並且該圖示來自從傳回的相同影像清單<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>方法中的<xref:Microsoft.VisualStudio.Package.LanguageService>類別。 MPF 類別的預設行為是不會顯示錯誤訊息的映像。 然而，衍生類別中的覆寫這個行為<xref:Microsoft.VisualStudio.Package.Source>類別而且覆寫<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>方法。 該方法，在您建立新<xref:Microsoft.VisualStudio.Package.DocumentTask>物件。 傳回該物件之前，您可以使用<xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A>屬性<xref:Microsoft.VisualStudio.Package.DocumentTask>物件來設定的影像索引。 這會看起來像下列的範例。 請注意，`TestIconImageIndex`是列出所有的圖示，而且是此範例專屬的列舉。 您可能必須以不同的方式識別語言服務中的圖示。  
  
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
            TastPriority      priority,  
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
  
## <a name="the-default-image-list-for-a-language-service"></a>語言服務之預設影像清單  
 所提供的基底的 MPF 語言服務類別的預設影像清單包含一些較常見的語言項目相關聯的圖示。 大部分的這些圖示會排列在六個變化，存取公用、 內部、 和的概念 friend，受保護的、 私用快顯對應的集合。 例如，您可以有不同的圖示，根據是否公用、 受保護或私用方法。  
  
 下列的列舉型別會指定針對每個圖示集的一般名稱，並指定相關聯的索引。 例如，根據列舉型別，您可以指定做為受保護的方法的影像索引`(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`。 您可以變更視這個列舉型別中的名稱。  
  
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
  
## <a name="see-also"></a>請參閱  
 [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [舊版語言服務概觀](../../extensibility/internals/legacy-language-service-overview.md)   
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [舊版語言服務的剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)