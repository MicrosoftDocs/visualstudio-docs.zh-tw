---
title: "在舊版語言服務中的成員完成 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense、 成員完成工具提示"
  - "成員完成時，支援的語言服務 [受管理的封裝 framework]"
  - "語言服務 [受管理的封裝 framework] 成員的 IntelliSense 完成"
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# 在舊版語言服務中的成員完成
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

完成 IntelliSense 成員是會顯示一份可能的成員，例如類別、 結構、 列舉型別或命名空間的特定範圍的工具提示。 比方說，在 C\# 中，如果使用者輸入"this"，後面接著句點，類別或結構，在目前範圍內的所有成員的清單會顯示使用者可以從中選取的清單中。  
  
 受管理的封裝架構 \(MPF\) 提供支援的工具提示和管理清單中的工具提示。所需要的全部是由剖析器來提供資料出現在清單中的合作。  
  
 舊版的語言服務會實作成，VSPackage 的一部分，但實作語言服務功能的較新的方法是使用 MEF 延伸模組。 若要深入了解，請參閱 [擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會改善語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## 它的運作方式  
 以下是在其成員清單會顯示使用 MPF 類別的兩種方法︰  
  
-   識別項 （含） 之後成員完成字元位置插入號，然後選取 **列出成員** 從 **IntelliSense** 功能表。  
  
-   <xref:Microsoft.VisualStudio.Package.IScanner> 掃描器會偵測成員完成字元，並設定權杖觸發程序的 <xref:Microsoft.VisualStudio.Package.TokenTriggers> ，該字元。  
  
 成員完成字元表示的類別、 結構或列舉型別成員是遵循。 例如，在 C\# 或 Visual Basic 成員完成字元是 `.`, ，而 c \+ \+ 中的字元是其中 `.` 或 `->`。 成員選取字元會掃描時，會設定觸發程序的值。  
  
### IntelliSense 成員 List 命令  
 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 命令開始呼叫 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 方法 <xref:Microsoft.VisualStudio.Package.Source> 類別和 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 方法，接著呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法剖析器剖析原因為 <xref:Microsoft.VisualStudio.Package.ParseReason>。  
  
 剖析器會判斷目前的位置，以及在或之前的目前位置的語彙基元的內容。 根據這個語彙基元，會顯示宣告的清單。 例如，在 C\# 中，如果您的類別成員，然後選取插入號 **列出成員**, ，取得類別的所有成員的清單。 如果您插入號後面物件變數的句點之後，您會取得類別的物件所代表的所有成員的清單。 請注意，是否插入號位於成員顯示成員的清單時，從清單中選取的成員會取代插入號是一個清單中的成員。  
  
### 語彙基元的觸發程序  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 觸發程序開始呼叫 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 方法 <xref:Microsoft.VisualStudio.Package.Source> 類別和 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 方法，轉而呼叫的剖析器剖析原因為 <xref:Microsoft.VisualStudio.Package.ParseReason> \(如果語彙基元的觸發程序也包含 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 旗標，剖析的原因是 <xref:Microsoft.VisualStudio.Package.ParseReason> 其中結合了成員選取範圍和大括號反白顯示\)。  
  
 剖析器會判斷目前的內容以及成員選取字元之前具有已輸入位置。 這項資訊，從剖析器會建立要求的範圍中的所有成員的清單。 此宣告的清單儲存在 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 所傳回的物件 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法。 如果傳回的任何宣告，則會顯示成員完成工具提示。 執行個體所管理的工具提示 <xref:Microsoft.VisualStudio.Package.CompletionSet> 類別。  
  
## 啟用支援成員完成  
 您必須擁有 `CodeSense` 登錄項目設為 1，以支援 IntelliSense 的任何作業。 此登錄項目可以設定具名參數，傳遞至 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 語言套件相關聯的使用者屬性。 語言服務類別會讀取此登錄項目的值從 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 屬性 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 類別。  
  
 如果您的掃描器傳回的語彙基元的觸發程序 <xref:Microsoft.VisualStudio.Package.TokenTriggers>, ，和您剖析器會傳回一份宣告，就不會顯示成員的完成清單。  
  
## 掃描器的支援成員完成  
 掃描器必須能夠偵測成員完成字元及設定的語彙基元的觸發程序 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 剖析該字元時。  
  
### 範例  
 以下是一個簡單的例子，偵測成員完成字元，並設定適當的 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 旗標。 這個範例是僅供示範用途。 它會假設您的掃描器都包含一種方法 `GetNextToken` ，識別，並傳回權杖，從一行文字。 每當它看見正確類型的字元時，範例程式碼只需設定觸發程序。  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char memberSelectChar = '.';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (c == memberSelectChar)  
                {  
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;  
                }  
            }  
            return foundToken;  
        }  
    }  
}  
```  
  
## 剖析器中支援成員完成  
 成員完成 <xref:Microsoft.VisualStudio.Package.Source> 類別會呼叫 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> 方法。 您必須從衍生類別中實作清單 <xref:Microsoft.VisualStudio.Package.Declarations> 類別。 請參閱 <xref:Microsoft.VisualStudio.Package.Declarations> 類別必須實作的方法的相關詳細資料。  
  
 剖析器會以呼叫 <xref:Microsoft.VisualStudio.Package.ParseReason> 或 <xref:Microsoft.VisualStudio.Package.ParseReason> 成員選取的字元型別。 指定位置 <xref:Microsoft.VisualStudio.Package.ParseRequest> 物件後立即成員選取字元。 剖析器必須收集可以在原始程式碼中的特定點的成員清單中出現的所有成員的名稱。 然後，剖析器必須剖析目前這一行來決定使用者想要的成員選取字元相關聯的範圍。  
  
 成員選取字元之前，此範圍根據識別項的類型。 例如，在 C\# 中，指定的成員變數 `languageService` 具有一種 `LanguageService`, ，輸入 **languageService。** ，產生的所有成員的清單 `LanguageService` 類別。 也在 C\# 中，輸入 **這。** 會產生一份目前範圍中類別的所有成員。  
  
### 範例  
 下列範例將示範一種方式填入 <xref:Microsoft.VisualStudio.Package.Declarations> 清單。 此程式碼假設剖析器建構宣告，並將它加入至清單中，藉由呼叫 `AddDeclaration` 方法 `TestAuthoringScope` 類別。  
  
```c#  
using System.Collections;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclaration  
    {  
        public string Name;            // Name of declaration  
        public int     TypeImageIndex; // Glyph index  
        public string Description;     // Description of declaration  
  
        public TestDeclaration(string name, int typeImageIndex, string description)  
        {  
            this.Name = name;  
            this.TypeImageIndex = typeImageIndex;  
            this.Description = description;  
        }  
    }  
  
    //===================================================  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList declarations;  
  
        public TestDeclarations()  
            : base()  
        {  
            declarations = new ArrayList();  
        }  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        //////////////////////////////////////////////////////////////////////  
        // Declarations of class methods that must be implemented.  
        public override int GetCount()  
        {  
            // Return the number of declarations to show.  
            return declarations.Count;  
        }  
  
        public override string GetDescription(int index)  
        {  
            // Return the description of the specified item.  
            string description = "";  
            if (index >= 0 && index < declarations.Count)  
            {  
                description = ((TestDeclaration)declarations[index]).Description;  
            }  
            return description;  
        }  
  
        public override string GetDisplayText(int index)  
        {  
            // Determine what is displayed in the tool tip list.  
            string text = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                text = ((TestDeclaration)declarations[index]).Name;  
            }  
            return text;  
        }  
  
        public override int GetGlyph(int index)  
        {  
            // Return index of image to display next to the display text.  
            int imageIndex = -1;  
            if (index >= 0 && index < declarations.Count)  
            {  
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;  
            }  
            return imageIndex;  
        }  
  
        public override string GetName(int index)  
        {  
            string name = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                name = ((TestDeclaration)declarations[index]).Name;  
            }  
            return name;  
        }  
    }  
  
    //===================================================  
    public class TestAuthoringScope : AuthoringScope  
    {  
        private TestDeclarations declarationsList;  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            if (declaration != null)  
            {  
                if (declarationsList == null)  
                {  
                    declarationsList = new TestDeclarations();  
                }  
                declarationsList.AddDeclaration(declaration);  
            }  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return declarationsList;  
        }  
  
        /////////////////////////////////////////////////  
        // Remainder of AuthoringScope methods not shown.  
        /////////////////////////////////////////////////  
    }  
  
    //===================================================  
    class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            TestAuthoringScope scope = new TestAuthoringScope();  
            if (req.Reason == ParseReason.MemberSelect ||  
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)  
            {  
                // Gather list of declarations based on what the user  
                // has typed so far. In this example, this list is an array of  
                // MemberDeclaration objects (a helper class you might implement  
                // to hold member declarations).  
                // How this list is gathered is dependent on the parser  
                // and is not shown here.  
                MemberDeclarations memberDeclarations;  
                memberDeclarations = GetDeclarationsForScope();  
  
                // Now populate the Declarations list in the authoring scope.  
                // GetImageIndexBasedOnType() is a helper method you  
                // might implement to convert a member type to an index into  
                // the image list returned from the language service.  
                foreach (MemberDeclaration dec in memberDeclarations)  
                {  
                    scope.AddDeclaration(new TestDeclaration(  
                                             dec.Name,  
                                             GetImageIndexBasedOnType(dec.Type),  
                                             dec.Description));  
                }  
            }  
            return scope;  
        }  
    }  
}  
```