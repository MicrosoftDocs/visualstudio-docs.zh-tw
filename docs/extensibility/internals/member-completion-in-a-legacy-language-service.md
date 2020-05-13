---
title: 舊語言服務中的成員完成 |微軟文件
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
ms.openlocfilehash: b6445aec4954590e4d361189f053592eebe7767e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707190"
---
# <a name="member-completion-in-a-legacy-language-service"></a>舊版語言服務中的成員完成

IntelliSense 成員完成是一個工具提示,用於顯示特定作用域(如類、結構、枚舉或命名空間)的可能成員的清單。 例如,在 C# 中,如果使用者鍵入"THIS"後跟句點,則在當前作用域中顯示類或結構的所有成員的清單,用戶可以從中選擇該清單。

託管包框架 (MPF) 支援工具提示和管理工具提示中的清單;只需要解析器提供清單中顯示的數據方面的合作。

舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解更多資訊,請參閱[延伸編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將提高語言服務的性能,並允許您利用新的編輯器功能。

## <a name="how-it-works"></a>運作方式

以下是使用 MPF 類顯示成員清單的兩種方式:

- 將 care 放在識別碼或成員完成字元之後,並從**IntelliSense**選單選擇 **「清單成員**」。

- 掃描器<xref:Microsoft.VisualStudio.Package.IScanner>檢測成員完成字元並設置[令牌觸發器](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)的權杖觸發器。

成員完成字元指示要遵循類、結構或枚舉的成員。 例如, 在 C# 或 Visual`.`Basic 中, 成員完成字`.`元為`->`,而在C++ 該字元為或 。 掃描成員選擇字元時設置觸發器值。

### <a name="the-intellisense-member-list-command"></a>感知成員清單指令

該<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><xref:Microsoft.VisualStudio.Package.Source.Completion%2A>命令<xref:Microsoft.VisualStudio.Package.Source>啟動對 類上方法<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>的調用 ,<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>該方法又使用[ParseReason.Display成員清單的](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>)解析原因調用方法解析器。

解析器確定當前位置的上下文以及當前位置下方或緊接於當前位置的權杖。 基於此令牌,將顯示聲明清單。 例如,在 C# 中,如果將 caret 放置在類成員上並選擇 **「列表成員」,** 則獲取類所有成員的清單。 如果在物件變數之後的句點之後放置 caret,則獲取物件表示的類的所有成員的清單。 請注意,如果在成員清單顯示時,該示者位於成員上,則從清單中選擇一個成員將該成員替換為清單中的成員。

### <a name="the-token-trigger"></a>權杖觸發器

[令牌觸發器.成員選擇](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>觸發器啟動<xref:Microsoft.VisualStudio.Package.Source>對 類上方法的調<xref:Microsoft.VisualStudio.Package.Source.Completion%2A>用, 而方法則使用[ParseReason](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>)的解析原因調用解析器。 如果權杖觸發器還包括[令牌觸發器.MatchBraces](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>)標誌,則解析原因是[ParseEE.成員選擇和高光,](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>)它結合了成員選擇和大括弧突出顯示。

解析器確定當前位置的上下文以及成員選擇字元之前鍵入的內容。 根據此資訊,解析器創建請求作用域的所有成員的清單。 此聲明清單儲存在從<xref:Microsoft.VisualStudio.Package.AuthoringScope><xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法傳回的物件中。 如果返回任何聲明,將顯示成員完成工具提示。 工具提示由<xref:Microsoft.VisualStudio.Package.CompletionSet>類的實例管理。

## <a name="enable-support-for-member-completion"></a>開啟對成員完成的支援

您必須將`CodeSense`註冊表項設置為 1 以支援任何 IntelliSense 操作。 此註冊表項可以使用傳遞給與語言包關聯的使用者屬性的<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>命名參數進行設置。 語言服務類從<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A><xref:Microsoft.VisualStudio.Package.LanguagePreferences>類的屬性中讀取此註冊表項的值。

如果掃描器返回[令牌觸發器的權杖觸發器.成員選擇](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>),並且解析器返回聲明清單,則會顯示成員完成清單。

## <a name="support-member-completion-in-the-scanner"></a>支援掃描器中的成員完成

掃描程式必須能夠檢測成員完成字元並設置[令牌觸發器](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)的權杖觸發器。

### <a name="scanner-example"></a>掃描器範例

下面是檢測成員完成字元和設置相應<xref:Microsoft.VisualStudio.Package.TokenTriggers>標誌的簡化範例。 此示例僅用於說明目的。 它假定掃描器包含一個標識和返回`GetNextToken`文本行中的權杖的方法。 範例代碼只要看到正確的字元類型,即可設置觸發器。

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

## <a name="support-member-completion-in-the-parser"></a>支援 Parser 的會員完成

對於成員完成,<xref:Microsoft.VisualStudio.Package.Source>類別調<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>用方法。 必須在派生自類的<xref:Microsoft.VisualStudio.Package.Declarations>類中實現該清單。 有關必須<xref:Microsoft.VisualStudio.Package.Declarations>實現的方法的詳細資訊,請參閱 該類。

解析器使用[ParseReason.成員選擇](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>)或[ParseReason 調用。成員選擇和突出顯示在](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>)成員選擇字元鍵入時。 <xref:Microsoft.VisualStudio.Package.ParseRequest>物件中給出的位置緊接成員選擇字元。 解析器必須收集可在原始碼中該特定點出現在成員清單中的所有成員的名稱。 然後,解析器必須分析當前行以確定使用者希望與成員選擇字元關聯的範圍。

此作用域基於成員選擇字元之前識別符的類型。 例如,在 C# 中,給`languageService``LanguageService`定具有類型的成員變數鍵入**語言服務。** 生成`LanguageService`類的所有成員的清單。 此外,在 C# 中,鍵入**此。** 生成當前作用域中類的所有成員的清單。

### <a name="parser-example"></a>分析器範例

下面的範例顯示了填充清單的一<xref:Microsoft.VisualStudio.Package.Declarations>種方法。 此代碼假定解析器建構一個聲明,並通過在`AddDeclaration``TestAuthoringScope`類上調用方法將其添加到清單中。

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
