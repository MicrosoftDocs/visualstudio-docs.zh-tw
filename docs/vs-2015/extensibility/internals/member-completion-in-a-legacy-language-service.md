---
title: 舊版語言服務中的成員自動完成 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b8b5940e473c639600c30e66e7dc0c732359322d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790979"
---
# <a name="member-completion-in-a-legacy-language-service"></a>舊版語言服務中的成員完成
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IntelliSense 成員自動完成會顯示一份可能的成員，例如類別、 結構、 列舉型別或命名空間的特定範圍的工具提示。 比方說，在 C# 中，如果使用者輸入"this"，後面接著句號，類別或結構，在目前的範圍內的所有成員的清單會顯示使用者可以從中選取的清單中。  
  
 Managed 的 package framework (MPF) 提供的工具提示和支援管理工具提示; 中的清單它只需要為合作提供出現在清單中的資料剖析器。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新的方式是使用 MEF 擴充功能。 若要深入了解，請參閱[擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 盡。 這會改善您的語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="how-it-works"></a>它的運作方式  
 以下是在其成員的清單會顯示使用 MPF 類別的兩種方法：  
  
- 定位在的識別項或成員完成字元之後的插入號，然後選取**列出成員**從**IntelliSense**功能表。  
  
- <xref:Microsoft.VisualStudio.Package.IScanner>掃描器會偵測成員完成字元，並設定語彙基元的觸發程序的<xref:Microsoft.VisualStudio.Package.TokenTriggers>該字元。  
  
  成員完成字元表示的類別、 結構或列舉成員遵循。 例如，在 C# 或 Visual Basic 中的成員完成字元是`.`，而 c + + 中的字元是其中一個`.`或`->`。 成員選取字元會掃描時，會設定觸發程序的值。  
  
### <a name="the-intellisense-member-list-command"></a>IntelliSense 成員 List 命令  
 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>命令會起始呼叫<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法<xref:Microsoft.VisualStudio.Package.Source>類別和<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法，轉而呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法的剖析器，剖析原因為<xref:Microsoft.VisualStudio.Package.ParseReason>。  
  
 剖析器會判斷目前的位置，以及在或之前的目前位置的權杖內容。 根據這個語彙基元，會顯示宣告的清單。 例如，在 C# 中，如果您放置在類別成員，然後選取插入號**列出成員**，取得一份類別的所有成員。 如果您插入號後面的物件變數的句點之後，您會取得一份類別的物件所代表的所有成員。 請注意，是否插入號位於成員顯示成員清單時，從清單中選取成員會取代插入號位於與清單中的成員。  
  
### <a name="the-token-trigger"></a>語彙基元的觸發程序  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers>觸發程序開始呼叫<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法<xref:Microsoft.VisualStudio.Package.Source>類別和<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>方法，再轉而呼叫的剖析器，剖析原因為<xref:Microsoft.VisualStudio.Package.ParseReason>(如果語彙基元的觸發程序也包含<xref:Microsoft.VisualStudio.Package.TokenTriggers>旗標，剖析的原因是<xref:Microsoft.VisualStudio.Package.ParseReason>合併成員選取和大括號反白顯示)。  
  
 剖析器會判斷目前的內容以及成員選取字元之前具有已輸入的位置。 這項資訊，剖析器會建立一份要求的範圍中的所有成員。 這份清單的宣告會儲存在<xref:Microsoft.VisualStudio.Package.AuthoringScope>會從傳回的物件<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法。 如果未傳回任何宣告，成員完成會顯示工具提示。 執行個體所管理的工具提示<xref:Microsoft.VisualStudio.Package.CompletionSet>類別。  
  
## <a name="enabling-support-for-member-completion"></a>啟用成員自動完成的支援  
 您必須擁有`CodeSense`能夠支援所有 IntelliSense 作業設定為 1 的登錄項目。 此登錄項目可以設定使用具名參數，傳遞至<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>語言套件相關聯的使用者屬性。 語言服務類別讀取此登錄項目的值從<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>屬性上的<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別。  
  
 如果您的掃描器傳回的語彙基元的觸發程序<xref:Microsoft.VisualStudio.Package.TokenTriggers>，和您剖析器會傳回一份宣告，則成員完成清單隨即顯示。  
  
## <a name="supporting-member-completion-in-the-scanner"></a>在掃描器上的支援成員自動完成  
 掃描器必須能夠偵測成員完成字元，並設定的語彙基元的觸發程序<xref:Microsoft.VisualStudio.Package.TokenTriggers>剖析該字元時。  
  
### <a name="example"></a>範例  
 以下是偵測成員完成字元，並設定適當的簡化的範例<xref:Microsoft.VisualStudio.Package.TokenTriggers>旗標。 這個範例是僅供示範用途。 它會假設您的掃描器，包含方法`GetNextToken`的識別，並從文字行，傳回權杖。 範例程式碼只需設定觸發程序，每當它看見正確類型的字元。  
  
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
  
## <a name="supporting-member-completion-in-the-parser"></a>剖析器中支援的成員自動完成  
 成員自動完成，如<xref:Microsoft.VisualStudio.Package.Source>類別會呼叫<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>方法。 您必須從衍生類別中實作清單<xref:Microsoft.VisualStudio.Package.Declarations>類別。 請參閱<xref:Microsoft.VisualStudio.Package.Declarations>如需詳細資訊，您必須實作的方法相關的類別。  
  
 剖析器會呼叫具有<xref:Microsoft.VisualStudio.Package.ParseReason>或<xref:Microsoft.VisualStudio.Package.ParseReason>成員選取的字元型別。 指定的位置<xref:Microsoft.VisualStudio.Package.ParseRequest>物件會立即在成員選取字元之後。 剖析器必須收集可以出現在該特定的時間點的原始碼在成員清單中的所有成員的名稱。 然後，剖析器必須剖析目前這一行來判斷使用者想要的成員選取字元相關聯的範圍。  
  
 成員選取字元之前，此範圍根據識別項型別。 例如，在 C# 中，指定的成員變數`languageService`具有一種`LanguageService`、 輸入**languageService。** 產生的所有成員的清單`LanguageService`類別。 也在 C# 中，輸入**這。** 會產生一份目前範圍中之類別的所有成員。  
  
### <a name="example"></a>範例  
 下列範例示範一種方式填入<xref:Microsoft.VisualStudio.Package.Declarations>清單。 此程式碼假設剖析器建構宣告，並將它新增至清單中，藉由呼叫`AddDeclaration`方法`TestAuthoringScope`類別。  
  
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

