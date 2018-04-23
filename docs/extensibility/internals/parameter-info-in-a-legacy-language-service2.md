---
title: 參數資訊，以舊版語言 Service2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6aaf8ba9be9e16eeb979b0d64d3e80e8d70b564f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="parameter-info-in-a-legacy-language-service"></a>在舊版語言服務中的參數資訊
IntelliSense 的 參數資訊是顯示在方法簽章，當使用者輸入的參數清單中的工具提示啟動方法參數清單的字元 （通常是左括號）。 當每個參數輸入和輸入參數分隔符號 （通常是逗號），工具提示會更新以顯示下一個參數以粗體顯示。  
  
 Managed 的封裝架構 (MPF) 類別來管理參數資訊工具提示提供支援。 剖析器必須偵測參數啟動參數接下來，及參數結尾字元，而且必須提供的方法簽章和其相關聯的參數清單。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新方法是使用 MEF 擴充功能。 若要深入了解，請參閱[擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會提升語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="implementation"></a>實作  
 剖析器應設定觸發程序值<xref:Microsoft.VisualStudio.Package.TokenTriggers>時找到的參數清單開頭字元 （通常一個左括號） 設定。 它應該設定<xref:Microsoft.VisualStudio.Package.TokenTriggers>發現參數分隔符號 （通常逗號） 時，觸發程序。 這會導致更新，而且以粗體顯示的下一個參數的參數資訊工具提示。 剖析器應設定觸發程序值<xref:Microsoft.VisualStudio.Package.TokenTriggers>時如果找到參數清單結尾字元 （通常右括號）。  
  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers>觸發值初始化呼叫<xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A>方法中，依序呼叫<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法剖析器剖析原因為<xref:Microsoft.VisualStudio.Package.ParseReason>。 如果剖析器會判斷參數清單開始字元之前的識別項是可辨識的方法名稱，它會傳回一份比對中的方法簽章<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件。 如果找不到任何方法簽章，參數資訊工具提示會顯示在清單中的第一個簽章。 依照簽章的多個輸入，然後會更新此工具提示。 參數清單結尾字元輸入時，參數資訊工具提示會從檢視中移除。  
  
> [!NOTE]
>  為了確保已正確格式化參數資訊工具提示，您必須覆寫的屬性上<xref:Microsoft.VisualStudio.Package.Methods>類別，以提供適當的字元。 基底<xref:Microsoft.VisualStudio.Package.Methods>類別假設 C#-樣式方法簽章。 請參閱<xref:Microsoft.VisualStudio.Package.Methods>如何完成的詳細資訊的類別。  
  
## <a name="enabling-support-for-the-parameter-info"></a>啟用支援的參數資訊  
 若要支援的參數資訊工具提示，您必須設定`ShowCompletion`具名參數的<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>至`true`。 語言服務會讀取此登錄項目的值從<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>屬性。  
  
 此外，<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A>屬性必須設定為`true`顯示參數資訊工具提示。  
  
### <a name="example"></a>範例  
 以下是一個簡單的例子偵測參數清單的字元，並設定適當的觸發程序。 這個範例是僅供說明。 它會假設您的掃描器包含方法`GetNextToken`的識別，並傳回從文字行的語彙基元。 範例程式碼只需設定觸發程序，每當它看見正確類型的字元時。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char parameterListStartChar = '(';  
        private const char parameterListEndChar   = ')';  
        private const char parameterNextChar      = ',';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (Char.IsPunctuation(c))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                    tokenInfo.EndIndex = index;  
  
                    if (c == parameterListStartChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;  
                    }  
                    else if (c == parameterListNextChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;  
                    else if (c == parameterListEndChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;  
                    }  
                }  
            return foundToken;  
        }  
    }  
}  
```  
  
## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>剖析器支援參數資訊工具提示  
 <xref:Microsoft.VisualStudio.Package.Source>類別可進行某些假設的內容<xref:Microsoft.VisualStudio.Package.AuthoringScope>和<xref:Microsoft.VisualStudio.Package.AuthoringSink>類別時的參數資訊工具提示會顯示，並且會更新。  
  
-   指定剖析器<xref:Microsoft.VisualStudio.Package.ParseReason>參數清單的開頭字元型別。  
  
-   給定的位置<xref:Microsoft.VisualStudio.Package.ParseRequest>物件後立即參數清單的起點字元。 剖析器必須收集的簽章在所有方法宣告的位置，並將其儲存在您的版本中的清單<xref:Microsoft.VisualStudio.Package.AuthoringScope>物件。 這份清單包含方法名稱、 方法類型 （或傳回型別），以及一份可能的參數。 這份清單稍後搜尋的方法簽章或簽章的參數資訊工具提示中顯示。  
  
 剖析器然後必須剖析由指定的行<xref:Microsoft.VisualStudio.Package.ParseRequest>物件來收集輸入的方法，以及距離沿著使用者的名稱是輸入參數。 這是藉由傳遞至方法的名稱<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A>方法<xref:Microsoft.VisualStudio.Package.AuthoringSink>物件，然後再呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>剖析方法的參數清單啟動字元時，呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>方法時的參數清單下一個字元會剖析，並且最後呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>方法剖析的參數清單結尾字元時。 這些方法呼叫的結果由<xref:Microsoft.VisualStudio.Package.Source>類別，以適當地更新參數資訊工具提示。  
  
### <a name="example"></a>範例  
 以下是文字的使用者可能輸入行。 這一行下方的數字表示的步驟由剖析器列 （假設剖析移左到右） 中的該位置。 此處的假設是之前, 的所有項目已經已剖析方法簽章，包括 「 testfunc"方法簽章。  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 剖析器接受的步驟如下所述：  
  
1.  剖析器呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A>以文字"testfunc"。  
  
2.  剖析器呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>。  
  
3.  剖析器呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>。  
  
4.  剖析器呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>。