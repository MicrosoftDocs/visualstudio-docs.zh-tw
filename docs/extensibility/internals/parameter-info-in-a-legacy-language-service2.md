---
title: "在舊版語言 Service2 參數資訊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense、 參數資訊工具提示"
  - "語言服務 [受管理的封裝 framework] IntelliSense 參數資訊"
  - "參數資訊 (IntelliSense)、 支援的語言服務 [受管理的封裝 framework]"
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# 在舊版語言服務中的參數資訊
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

當使用者輸入的參數清單會顯示方法的簽章的工具提示開始字元 （通常是左括號） 的方法參數清單是 IntelliSense 參數資訊。 每個參數輸入和輸入參數分隔符號 （通常是逗號），工具提示會更新以顯示下一個參數以粗體顯示。  
  
 受管理的封裝架構 \(MPF\) 類別來管理參數資訊工具提示提供支援。 剖析器必須偵測參數開始，參數接下來，而參數結尾字元，而且必須提供的方法簽章和其相關聯的參數清單。  
  
 舊版的語言服務會實作成，VSPackage 的一部分，但實作語言服務功能的較新的方法是使用 MEF 延伸模組。 若要深入了解，請參閱 [擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會改善語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## 實作  
 剖析器應設定觸發程序值 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 當它找到的參數清單開始字元 （通常左括號） 設定。 它應該設定 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 發現參數分隔符號 （通常逗號） 時，觸發程序。 這會導致更新，並以粗體顯示的下一個參數的參數資訊工具提示。 剖析器應設定觸發程序值 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 時如果尋找的參數清單結尾字元 （通常右括號）。  
  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 觸發值初始化呼叫 <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> 方法中，依序呼叫 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 方法剖析器剖析原因為 <xref:Microsoft.VisualStudio.Package.ParseReason>。 如果剖析器會決定參數清單開始字元之前的識別項是可辨識的方法名稱，它會傳回比對中的方法簽章 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 物件。 如果找不到任何方法簽章，參數資訊工具提示會顯示在清單中的第一個簽章。 依照多個簽章的輸入，然後會更新此工具提示。 當輸入參數清單結尾字元時，則會從檢視移除參數資訊工具提示。  
  
> [!NOTE]
>  為了確保已正確格式化的參數資訊工具提示，您必須覆寫的屬性上 <xref:Microsoft.VisualStudio.Package.Methods> 類別，以提供適當的字元。 基底 <xref:Microsoft.VisualStudio.Package.Methods> 類別假設 C\#\-樣式方法簽章。 請參閱 <xref:Microsoft.VisualStudio.Package.Methods> 類別，如需有關如何完成。  
  
## 啟用支援的參數資訊  
 若要支援的參數資訊工具提示，您必須設定 `ShowCompletion` 具名參數的 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 到 `true`。 語言服務會讀取此登錄項目的值從 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 屬性。  
  
 此外， <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> 屬性必須設為 `true` 參數資訊工具提示會顯示。  
  
### 範例  
 以下是一個簡單的例子，偵測參數清單的字元，並設定適當的觸發程序。 這個範例是僅供示範用途。 它會假設您的掃描器都包含一種方法 `GetNextToken` ，識別，並傳回權杖，從一行文字。 每當它看見正確類型的字元時，範例程式碼只需設定觸發程序。  
  
```c#  
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
  
## 剖析器支援參數資訊工具提示  
 <xref:Microsoft.VisualStudio.Package.Source> 類別會做出一些假設內容 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 和 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 類別時的參數資訊工具提示會顯示，並且會更新。  
  
-   指定剖析器 <xref:Microsoft.VisualStudio.Package.ParseReason> 參數清單的開頭字元型別。  
  
-   指定位置 <xref:Microsoft.VisualStudio.Package.ParseRequest> 物件後立即參數清單開始的字元。 剖析器必須收集的簽章可在所有的方法宣告的位置，並將它們儲存在您的版本中的清單 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 物件。 這份清單包含方法名稱，方法類型 （或傳回型別），以及可用的參數清單。 這份清單稍後搜尋的方法簽章或簽章的參數資訊工具提示中顯示。  
  
 剖析器必須剖析所指定的行 <xref:Microsoft.VisualStudio.Package.ParseRequest> 物件來收集輸入的方法以及程度沿著使用者的名稱是在輸入參數。 這可以藉由傳遞至方法的名稱 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> 方法 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 物件，然後再呼叫 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> 剖析方法的參數清單開始字元時，呼叫 <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> 方法會剖析參數清單的下一個字元，以及最後呼叫 <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> 方法的參數清單結尾字元剖析時。 這些方法呼叫的結果由 <xref:Microsoft.VisualStudio.Package.Source> 類別，以適當地更新參數資訊工具提示。  
  
### 範例  
 以下是文字的使用者可能輸入行。 在線條下方的數字表示的步驟由剖析器 （假設剖析移動左到右） 列在該位置。 此處的假設，就是，一切的一行之前已經已剖析方法簽章，包括 「 testfunc 」 方法簽章。  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 剖析器會採用的步驟說明如下︰  
  
1.  剖析器呼叫 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> 以文字"testfunc"。  
  
2.  剖析器呼叫 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>。  
  
3.  剖析器呼叫 <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>。  
  
4.  剖析器呼叫 <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>。