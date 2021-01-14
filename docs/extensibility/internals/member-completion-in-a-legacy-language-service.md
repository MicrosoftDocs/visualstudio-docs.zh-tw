---
title: 舊版語言服務中的成員完成 |Microsoft Docs
description: 瞭解 IntelliSense 成員完成工具秘訣在舊版語言服務中的運作方式，以及受管理的封裝架構 (MPF) 的支援方式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4fbf88dab2f1ffad0b4a6e5dc6b2ad516c28afca
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205797"
---
# <a name="member-completion-in-a-legacy-language-service"></a>舊版語言服務中的成員完成

IntelliSense 成員完成是一種工具提示，會顯示特定範圍的可能成員清單，例如類別、結構、列舉或命名空間。 例如，在 c # 中，如果使用者輸入 "this"，後面接著句點，則在目前範圍的類別或結構的所有成員清單都會顯示在使用者可以選取的清單中。

受控封裝架構 (MPF) 提供工具提示的支援，以及管理工具提示中的清單;所需的一切都是從剖析器進行合作，以提供清單中顯示的資料。

舊版語言服務會實作為 VSPackage 的一部分，但是執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解，請參閱 [擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。

> [!NOTE]
> 建議您儘快開始使用新的編輯器 API。 這可改善您的語言服務效能，並讓您利用新的編輯器功能。

## <a name="how-it-works"></a>運作方式

以下是使用 MPF 類別顯示成員清單的兩種方式：

- 將插入號放在識別碼上或在成員完成字元之後，然後從 [ **IntelliSense** ] 功能表中選取 [**列出成員**]。

- <xref:Microsoft.VisualStudio.Package.IScanner>掃描器會偵測成員完成字元，並針對該字元設定 TokenTriggers 的 token 觸發程式[MemberSelect。](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)

成員完成字元表示要遵循類別、結構或列舉的成員。 例如，在 c # 或 Visual Basic 成員完成字元是 `.` ，而在 c + + 中，字元是 `.` 或 `->` 。 掃描成員 select 字元時，會設定觸發程式值。

### <a name="the-intellisense-member-list-command"></a>IntelliSense 成員清單命令

此 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 命令會起始對類別的 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 方法呼叫， <xref:Microsoft.VisualStudio.Package.Source> 而方法則會 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法剖析器，並使用 [ParseReason. DisplayMemberList](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>)的剖析原因。

剖析器會判斷目前位置的內容，以及目前位置或正下方或立即的標記。 根據此標記，會顯示宣告清單。 例如，在 c # 中，如果您將插入號放在類別成員上，然後選取 [ **清單成員**]，則會取得類別的所有成員清單。 如果您將插入號放在物件變數後面的句號之後，您會取得物件所代表之類別的所有成員清單。 請注意，當顯示成員清單時，如果插入號位於成員上，則從清單中選取成員時，會將插入號所在的成員取代為清單中的成員。

### <a name="the-token-trigger"></a>Token 觸發程式

[TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)觸發程式會起始對類別的方法呼叫，而方法則會呼叫剖析器，並 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 剖析原因為[ParseReason. MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>)。 如果 token 觸發程式也包含 [TokenTriggers. MatchBraces](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) 旗標，則剖析原因是 [ParseReason. MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>)，其中結合了成員選取範圍和大括弧反白顯示。

剖析器會判斷目前位置的內容，以及在成員選取字元之前輸入的內容。 在這項資訊中，剖析器會建立所要求範圍之所有成員的清單。 這份宣告清單儲存在方法所 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 傳回的物件中 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 。 如果傳回任何宣告，則會顯示成員完成工具提示。 工具提示是由類別的實例所管理 <xref:Microsoft.VisualStudio.Package.CompletionSet> 。

## <a name="enable-support-for-member-completion"></a>啟用成員完成的支援

您必須 `CodeSense` 將登錄專案設定為1，才能支援任何 IntelliSense 作業。 您可以使用傳遞至 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 與語言套件相關聯之使用者屬性的具名引數來設定這個登錄專案。 語言服務類別會從類別上的屬性讀取這個登錄專案的值 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 。

如果您的掃描器傳回 [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)的 token 觸發程式，而您的剖析器傳回宣告清單，則會顯示成員完成清單。

## <a name="support-member-completion-in-the-scanner"></a>掃描器中的支援成員完成

當剖析該字元時，掃描器必須能夠偵測成員完成字元，並設定 TokenTriggers 的 token 觸發程式[。](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)

### <a name="scanner-example"></a>掃描器範例

以下是一個簡單的範例，說明如何偵測成員完成字元並設定適當的 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 旗標。 此範例僅供說明之用。 它會假設您的掃描器包含一個方法 `GetNextToken` ，該方法會從文字行識別並傳回權杖。 範例程式碼只會在它看到正確種類的字元時，設定觸發程式。

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

## <a name="support-member-completion-in-the-parser"></a>解析程式中的支援成員完成

成員完成時， <xref:Microsoft.VisualStudio.Package.Source> 類別會呼叫 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> 方法。 您必須在衍生自類別的類別中執行清單 <xref:Microsoft.VisualStudio.Package.Declarations> 。 <xref:Microsoft.VisualStudio.Package.Declarations>如需您必須執行之方法的詳細資訊，請參閱類別。

當成員選取的字元具類型時，會使用 [ParseReason. MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) 或 [ParseReason](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) 來呼叫剖析器。 物件中提供的位置 <xref:Microsoft.VisualStudio.Package.ParseRequest> 緊接在成員選取字元之後。 剖析器必須收集所有成員的名稱，這些成員可出現在原始程式碼中該特定點的成員清單中。 然後剖析器必須剖析目前的行，以判斷使用者想要與成員選取字元相關聯的範圍。

此範圍是以成員選取字元之前的識別碼類型為基礎。 例如，在 c # 中，假設 `languageService` 具有類型的成員變數，則 `LanguageService` 輸入 **languageService。** 產生類別的所有成員清單 `LanguageService` 。 另外，在 c # 中輸入 **此。** 產生目前範圍中類別的所有成員清單。

### <a name="parser-example"></a>剖析器範例

下列範例示範一種填入清單的方法 <xref:Microsoft.VisualStudio.Package.Declarations> 。 這段程式碼假設剖析器會藉由呼叫類別上的方法，來建立宣告並將其加入至清單 `AddDeclaration` `TestAuthoringScope` 。

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
