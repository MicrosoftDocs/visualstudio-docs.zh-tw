---
title: "實作傳統語言 Service2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "實作語言服務 [受管理的封裝 framework]"
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# 實作傳統語言服務
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

若要實作使用受管理的封裝架構 \(MPF\) 語言服務，您必須衍生類別，以從<xref:Microsoft.VisualStudio.Package.LanguageService>類別並實作下列抽象方法和屬性：  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> 方法  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 方法  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> 屬性  
  
 在實作這些方法和屬性，請參閱下面適當的小節如需詳細資訊。  
  
 若要支援額外的功能，您語言的服務可能需要從 MPF 語言服務的類別 ； 其中一項衍生類別 比方說，若要支援其他的功能表命令，您必須衍生一個類別，從<xref:Microsoft.VisualStudio.Package.ViewFilter>類別並覆寫數個命令處理方法 \(請參閱<xref:Microsoft.VisualStudio.Package.ViewFilter>如需詳細資訊\)。  <xref:Microsoft.VisualStudio.Package.LanguageService>類別會提供多個稱為 「 若要建立的各種類別的新執行個體的方法，並覆寫適當的建立方式，提供您類別的執行個體。  例如，您需要覆寫<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>中的方法<xref:Microsoft.VisualStudio.Package.LanguageService>類別以傳回您自己的執行個體<xref:Microsoft.VisualStudio.Package.ViewFilter>類別。  請參閱 「 自訂類別的執行個體化 」 如需詳細資訊。  
  
 語言服務也可以提供自己的圖示，使用在許多地方。  比方說，當 IntelliSense 完成清單會顯示，清單中的每個項目可以有與其相關聯，將郵件標示為方法、 類別、 命名空間、\] 屬性中的圖示，或項目，即所需的程式語言。  這些圖示用在所有的 IntelliSense 清單中， **導覽列**，並在 **錯誤清單**工作\] 視窗。  請參閱"語言服務映像 」 一節下方，如需詳細資訊。  
  
## GetLanguagePreferences 方法  
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>方法一定會傳回相同的執行個體的<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別。  您可以使用基底<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別，如果您不需要語言服務的任何其他偏好設定。  MPF 語言服務類別會假設最少的基底<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別。  
  
### 範例  
 這個範例會示範典型的實作中的<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>方法。  這個範例會使用基底<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別。  
  
```c#  
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
  
## GetScanner 方法  
 這個方法會傳回執行個體的<xref:Microsoft.VisualStudio.Package.IScanner>實作的行導向的剖析器或掃瞄器取得語彙基元、 其型別和引動程序所使用的物件。  此掃描器使用在<xref:Microsoft.VisualStudio.Package.Colorizer>類別的顏色標示，雖然掃瞄器也可用於取得語彙基元型別和觸發程序，為更複雜的剖析作業的 prelude。  您必須提供實作的類別<xref:Microsoft.VisualStudio.Package.IScanner>介面，而且您必須實作所有方法在<xref:Microsoft.VisualStudio.Package.IScanner>介面。  
  
### 範例  
 這個範例會示範典型的實作中的<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法。  `TestScanner`類別實作<xref:Microsoft.VisualStudio.Package.IScanner> \(未顯示\) 的介面。  
  
```c#  
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
  
## ParseSource 方法  
 剖析原始程式檔，根據幾個不同的原因。  這個方法會提供<xref:Microsoft.VisualStudio.Package.ParseRequest>將告訴您預期從特定的剖析作業的物件。  <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法會叫用的更複雜的剖析器會決定語彙基元的功能和範圍。  <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法在支援用 IntelliSense 作業，以及括號對稱。  即使您並不支援這種進階的作業，您仍然必須傳回有效的<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件，並需要您建立一個類別，實作<xref:Microsoft.VisualStudio.Package.AuthoringScope>介面及實作該介面上的所有方法。  您可以從所有的方法會傳回 null 值，但<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件本身不能為 null 值。  
  
### 範例  
 本範例顯示的最少實作<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法，並<xref:Microsoft.VisualStudio.Package.AuthoringScope>類別，可讓語言服務来編譯並實際支援其他更進階的功能之後才能運作。  
  
```c#  
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
  
## Name 屬性  
 這個屬性會傳回值為目前語言服務。  這必須是相同的名稱，如果語言服務已登錄。  此名稱用於的多種情況，其中最顯著的是<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別的名稱用於存取登錄。  傳回這個屬性的名稱必須不得當地語系化，因為它用於在登錄中登錄項目和機碼名稱。  
  
### 範例  
 本範例顯示可能的實作<xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>屬性。  請注意此處的名稱是硬式編碼： 應該從資源檔取得實際的名稱，因此可用於註冊語言服務 \(請參閱[註冊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)\)。  
  
```c#  
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
  
## 具現化自訂類別  
 下列方法中指定的類別可以覆寫，以提供您自己版本的每個類別的執行個體。  
  
### LanguageService 類別中  
  
|方法|傳回的類別|描述|  
|--------|-----------|--------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|若要支援自訂文字檢視加入的項目。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|若要支援自訂的文件內容。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|若要支援**導覽列**。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|若要在程式碼片段範本支援函式。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|若要支援 \(此方法通常不會被覆寫\) 的程式碼片段。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|若要支援自訂的<xref:Microsoft.VisualStudio.Package.ParseRequest> \(這個方法通常不會被覆寫\) 的結構。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|若要支援格式化程式碼中，指定註解字元，以及自訂方法簽名碼。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|若要支援其他的功能表命令。|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|若要支援語法反白顯示 \(這個方法通常不會被覆寫\)。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|若要支援的語言喜好設定的存取。  必須實作這個方法，但可能會傳回的基底類別的執行個體。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|提供用來識別的上一條線的語彙基元的型別可剖析器。  必須實作這個方法，並<xref:Microsoft.VisualStudio.Package.IScanner>必須衍生自。|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|提供用來識別功能和範圍中的整個原始程式檔的剖析器。  這個方法必須進行實作，且必須傳回執行個體的安裝版本<xref:Microsoft.VisualStudio.Package.AuthoringScope>類別。  如果您想要支援語法反白顯示 \(這需要<xref:Microsoft.VisualStudio.Package.IScanner>剖析器所傳回的<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法\)，您可以執行任何動作在這個方法傳回以外的其他版本的<xref:Microsoft.VisualStudio.Package.AuthoringScope>其所有的方法會傳回 null 值的類別。|  
  
### 來源類別中  
  
|方法|傳回的類別|描述|  
|--------|-----------|--------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|用來自訂 IntelliSense 完成清單中 \(此方法通常不會被覆寫\) 的顯示方式。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|在 \[錯誤清單\] 工作清單中 ； 支援標記 具體來說，支援功能遠超過開啟檔案，並使其跳躍至造成錯誤的行。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|用來自訂的 IntelliSense 參數資訊工具提示顯示。|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|為支援 \[註解的程式碼。|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|收集在剖析作業期間的資訊。|  
  
### AuthoringScope 類別中  
  
|方法|傳回的類別|描述|  
|--------|-----------|--------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|提供一份成員或型別宣告。  必須實作這個方法，但可能會傳回 null 值。  如果這個方法會傳回有效的物件，物件必須是執行個體的安裝版本<xref:Microsoft.VisualStudio.Package.Declarations>類別。|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|指定的內容提供方法簽章的清單。  必須實作這個方法，但可能會傳回 null 值。  如果這個方法會傳回有效的物件，物件必須是執行個體的安裝版本<xref:Microsoft.VisualStudio.Package.Methods>類別。|  
  
## 語言服務映像  
 若要提供一份可用於整個語言服務的圖示，請覆寫<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>中的方法<xref:Microsoft.VisualStudio.Package.LanguageService>類別，並傳回<xref:System.Windows.Forms.ImageList>的圖示所在。  基底<xref:Microsoft.VisualStudio.Package.LanguageService>類別會載入一組預設的圖示。  因為您可以指定完全相同映像索引需要圖示的這些部分中，您如何排列您自己的影像清單是完全取決於您。  
  
### IntelliSense 完成清單中所使用的影像  
 IntelliSense 完成清單中，為影像索引已指定每個項目在<xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A>方法的<xref:Microsoft.VisualStudio.Package.Declarations>類別，您必須覆寫，如果您想要提供影像索引。  傳回的值<xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A>方法是提供給影像清單索引<xref:Microsoft.VisualStudio.Package.CompletionSet>類別建構函式，而這是相同的影像清單傳回<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>中的方法<xref:Microsoft.VisualStudio.Package.LanguageService>類別 \(您可以變更所使用的影像清單<xref:Microsoft.VisualStudio.Package.CompletionSet>如果您覆寫<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>中的方法<xref:Microsoft.VisualStudio.Package.Source>類別，以提供不同的影像清單\)。  
  
### 在 \[導覽列中使用的影像  
 **導覽列**會顯示清單的型別和成員，以及使用如快速巡覽可以顯示的圖示。  這些圖示取自<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>中的方法<xref:Microsoft.VisualStudio.Package.LanguageService>類別並不能將它覆寫，專門用來**導覽列**。  表示下拉式方塊的清單會填入時指定下拉式方塊中的每個項目所使用的索引<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>中的方法<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>類別 \(請參閱[在舊版語言服務中的導覽列的支援](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)\)。  這些影像的索引某種方式取得由剖析器，一般是透過您的版本<xref:Microsoft.VisualStudio.Package.Declarations>類別。  取得索引的方式是完全取決於您。  
  
### 在 \[錯誤清單\] 工作視窗中使用的影像  
 每當<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法剖析器 \(請參閱[舊版的語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)\) 發生錯誤，並將該錯誤<xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A>中的方法<xref:Microsoft.VisualStudio.Package.AuthoringSink>類別中，會報告錯誤**錯誤清單**工作\] 視窗。  圖示可以出現在 \[工作\] 視窗中的每個項目相關聯，而且該圖示是來自相同的影像清單所傳回的<xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A>中的方法<xref:Microsoft.VisualStudio.Package.LanguageService>類別。  MPF 類別的預設行為是不會顯示影像並出現錯誤訊息。  然而，藉由衍生類別中的覆寫這個行為<xref:Microsoft.VisualStudio.Package.Source>類別並覆寫<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>方法。  該方法，您建立新的<xref:Microsoft.VisualStudio.Package.DocumentTask>物件。  後再傳回該物件，您可以使用<xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A>屬性在<xref:Microsoft.VisualStudio.Package.DocumentTask>若要設定的影像索引的物件。  這會看起來如下列範例所示的項目。  請注意， `TestIconImageIndex` ，列出所有的圖示，並屬於本範例為列舉型別。  您可能需要以不同的方式，來識別您的語言服務中的圖示。  
  
```c#  
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
  
## 語言服務之預設影像清單  
 基底的 MPF 語言服務類別所提供的預設影像清單包含許多較常見的語言項目相關聯的圖示。  大部分這些圖示都被以組的六個的變化，對應到內部公用、 受保護、 私用的朋友和快顯存取概念。  比方說，您可以有不同的圖示，取決於它是公用、 受保護或私用方法。  
  
 下列列舉型別會指定每個圖示集的一般名稱，並指定相關的索引。  例如，列舉型別為基礎，您可以指定受保護的方法，做為影像索引`(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`。  您可以變更為您想要這個列舉型別中的名稱。  
  
```c#  
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
  
## 請參閱  
 [實作傳統語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [舊版的語言服務概觀](../../extensibility/internals/legacy-language-service-overview.md)   
 [註冊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [舊版的語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)