---
title: "在舊版語言服務中的成員完成 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e77511bdaaa96dc75f5be75c175b63fcd3cc3253
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="member-completion-in-a-legacy-language-service"></a>在舊版語言服務中的成員完成
IntelliSense 成員完成會顯示一份可能的成員，例如類別、 結構、 列舉型別或命名空間的特定範圍的工具提示。 例如，在 C# 中，如果使用者輸入"this"，後面接著句號，類別或結構目前範圍的所有成員的清單會以清單，使用者可以從中選取。  
  
 Managed 的 package framework (MPF) 提供支援的工具提示和管理的清單中的工具提示。所需要的就是提供出現在清單中的資料剖析器的合作。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新方法是使用 MEF 擴充功能。 若要深入了解，請參閱[擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會提升語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="how-it-works"></a>它的運作方式  
 以下是在其成員清單會顯示使用 MPF 類別的兩種方式：  
  
-   定位在識別項或成員完成字元之後的插入號，然後選取**列出成員**從**IntelliSense**功能表。  
  
-   <xref:Microsoft.VisualStudio.Package.IScanner>掃描器偵測成員完成字元，並設定語彙基元的觸發程序是<xref:Microsoft.VisualStudio.Package.TokenTriggers>，該字元。  
  
 成員完成字元表示的類別、 結構或列舉型別成員遵循。 例如，在 C# 或 Visual Basic 中的成員完成字元是`.`，而 c + + 中的字元是其中`.`或`->`。 成員選取字元會掃描時，會設定的觸發程序的值。  
  
### <a name="the-intellisense-member-list-command"></a>IntelliSense 成員 List 命令  
 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>命令會起始呼叫<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法<xref:Microsoft.VisualStudio.Package.Source>類別和<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法又呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法剖析器，剖析原因為<xref:Microsoft.VisualStudio.Package.ParseReason>。  
  
 剖析器會判斷目前的位置，以及下或在目前的位置之前立即之權杖的內容。 根據這個語彙基元，會顯示宣告的清單。 例如，在 C# 中，如果您放置在類別成員，並選取插入號**列出成員**，取得一份所有類別的成員。 如果您將插入號後面的物件變數的句點之後，您會取得類別的物件所代表的所有成員的清單。 請注意，是否插入號位於成員顯示成員清單時，從清單中選取成員取代插入號位於與一個清單中的成員。  
  
### <a name="the-token-trigger"></a>語彙基元的觸發程序  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers>觸發程序會起始呼叫<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法<xref:Microsoft.VisualStudio.Package.Source>類別和<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法又呼叫以剖析原因的剖析器<xref:Microsoft.VisualStudio.Package.ParseReason>(如果語彙基元的觸發程序也包含<xref:Microsoft.VisualStudio.Package.TokenTriggers>旗標剖析的原因是<xref:Microsoft.VisualStudio.Package.ParseReason>其中結合成員選取範圍和大括號反白顯示)。  
  
 剖析器會判斷目前的內容以及成員選取字元之前具有已輸入的位置。 這項資訊，剖析器會建立要求的範圍中的所有成員的清單。 這個宣告的清單儲存在<xref:Microsoft.VisualStudio.Package.AuthoringScope>從傳回的物件<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法。 如果傳回的任何宣告，則會顯示成員完成工具提示。 執行個體所管理的工具提示<xref:Microsoft.VisualStudio.Package.CompletionSet>類別。  
  
## <a name="enabling-support-for-member-completion"></a>啟用支援成員完成  
 您必須擁有`CodeSense`登錄項目設為 1，以支援 IntelliSense 的任何作業。 此登錄項目可以設定使用具名參數，傳遞至<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>語言套件相關聯的使用者屬性。 語言服務類別讀取此登錄項目的值從<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>屬性<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別。  
  
 如果您的掃描器傳回的語彙基元觸發程序<xref:Microsoft.VisualStudio.Package.TokenTriggers>，，而且您剖析器會傳回一份宣告，則會顯示成員完成清單。  
  
## <a name="supporting-member-completion-in-the-scanner"></a>支援於掃描器中的成員完成  
 掃描器必須能夠偵測成員完成字元及設定的語彙基元觸發程序<xref:Microsoft.VisualStudio.Package.TokenTriggers>當剖析該字元。  
  
### <a name="example"></a>範例  
 以下是偵測成員完成字元，並設定適當的簡化的範例<xref:Microsoft.VisualStudio.Package.TokenTriggers>旗標。 這個範例是僅供說明。 它會假設您的掃描器包含方法`GetNextToken`的識別，並傳回從文字行的語彙基元。 範例程式碼只需設定觸發程序，每當它看見正確類型的字元時。  
  
```csharp  
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
  
## <a name="supporting-member-completion-in-the-parser"></a>剖析器中支援成員完成  
 成員完成<xref:Microsoft.VisualStudio.Package.Source>類別會呼叫<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>方法。 您必須從衍生類別中實作清單<xref:Microsoft.VisualStudio.Package.Declarations>類別。 請參閱<xref:Microsoft.VisualStudio.Package.Declarations>類別必須實作的方法的相關詳細資料。  
  
 剖析器會呼叫具有<xref:Microsoft.VisualStudio.Package.ParseReason>或<xref:Microsoft.VisualStudio.Package.ParseReason>成員選取的字元型別。 給定的位置<xref:Microsoft.VisualStudio.Package.ParseRequest>物件後立即成員選取字元。 剖析器必須收集可以出現在原始程式碼中該特定點的成員清單中的所有成員的名稱。 然後，剖析器必須剖析目前這一行來決定使用者想要的成員選取字元相關聯的範圍。  
  
 成員選取字元之前，此範圍根據識別項的類型。 例如，在 C# 中，指定成員變數`languageService`具有一種`LanguageService`、 輸入**languageService。** 產生的所有成員的清單`LanguageService`類別。 也在 C# 中，輸入**這。** 產生的類別，在目前範圍中的所有成員的清單。  
  
### <a name="example"></a>範例  
 下列範例會示範其中一種方式填入<xref:Microsoft.VisualStudio.Package.Declarations>清單。 此程式碼假設剖析器建構宣告，並將它加入至清單中，藉由呼叫`AddDeclaration`方法`TestAuthoringScope`類別。  
  
```csharp  
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