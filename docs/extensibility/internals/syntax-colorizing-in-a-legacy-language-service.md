---
title: 舊版語言服務中的語法上色 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ba516701ec232cb49edfee9888625789b544d62
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948644"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>舊版語言服務中的語法上色
語法顏色標示是一項功能，會顯示在原始程式檔中不同的色彩和樣式的程式設計語言的不同項目。 若要支援這項功能，您需要提供剖析器或掃描器可以識別語彙項目或檔案中的權杖類型。 許多語言關鍵字、 分隔符號 （例如括號或大括號），來區分及註解標示這些色彩以不同的方式。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新的方式是使用 MEF 擴充功能。 若要深入了解，請參閱[擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 盡。 這會改善您的語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="implementation"></a>實作  
 為了支援顏色標示，managed 的封裝架構 (MPF) 包含<xref:Microsoft.VisualStudio.Package.Colorizer>類別，它會實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>介面。 這個類別互動<xref:Microsoft.VisualStudio.Package.IScanner>判斷語彙基元和色彩。 如需有關掃描器的詳細資訊，請參閱[舊版語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)。 <xref:Microsoft.VisualStudio.Package.Colorizer>類別然後標記的語彙基元的色彩資訊的每個字元，並傳回該項資訊到編輯器中顯示的原始程式檔。  
  
 傳回至編輯器的色彩資訊是可設定色彩的項目清單中的索引。 每個可設定色彩的項目指定色彩值和一組的字型屬性，例如粗體或刪除線。 編輯器提供一組語言服務可用的預設色彩項目。 您只需要已指定適當的色彩索引的每個語彙基元的型別。 不過，您可以為權杖，提供一組自訂色彩的項目和您提供的索引，並參考您自己的可設定色彩的項目，而不是預設清單的清單。 您也必須設定`RequestStockColors`為 0 的登錄項目 (或不指定`RequestStockColors`在所有的項目) 來支援自訂的色彩。 您可以設定此登錄項目，使用具名參數，以<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>使用者定義的屬性。 如需有關註冊語言服務，並設定其選項的詳細資訊，請參閱 <<c0> [ 註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)。  
  
## <a name="custom-colorable-items"></a>自訂可設定色彩的項目  
 若要提供您自己自訂的色彩項目，您必須覆寫<xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A>並<xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A>方法<xref:Microsoft.VisualStudio.Package.LanguageService>類別。 第一種方法會傳回您的語言服務支援的自訂色彩項目數目和第二個取得自訂色彩項目的索引。 您建立自訂的色彩項目的預設清單。 在您的語言服務的建構函式，您只需要會提供每個可設定色彩的項目名稱。 Visual Studio 會自動處理的情況下，使用者選取一組不同的可設定色彩的項目。 這個名稱是在顯示的內容**字型和色彩**屬性頁上的**選項** 對話方塊中 (在 Visual Studio 中使用**工具**功能表)，此名稱會決定哪一個使用者已覆寫的色彩。 使用者的選擇會儲存在登錄中的快取，而且色彩名稱來存取。 **字型和色彩**屬性頁面會列出所有的色彩名稱，依字母順序，因此您可以將您的自訂色彩分組的方法是使用您語言的名稱; 每一個色彩名稱，例如"**TestLanguage-註解**"和"**TestLanguage-關鍵字**"。 也可以依型別，您可設定色彩的項目 」**註解 (TestLanguage)**"和"**關鍵字 (TestLanguage)**"。 依語言名稱的群組時，偏好。  
  
> [!CAUTION]
>  強烈建議您避免與現有的色彩項目的名稱發生衝突的色彩項目的名稱包含語言名稱。  
  
> [!NOTE]
>  如果您變更其中一個色彩的名稱，在開發期間，您必須重設 Visual Studio 建立第一次存取您的色彩的快取。 則可以藉由執行**重設實驗性的 Hive**從 Visual Studio SDK 的 [程式] 功能表命令。  
  
 請注意，永遠不會參考可設定色彩的項目清單中第一個項目。 Visual Studio 一律會提供預設文字色彩和該項目的屬性。 與這個處理的最簡單的方式是提供預留位置色彩項目的第一個項目。  
  
### <a name="high-color-colorable-items"></a>高彩色彩的項目  
 可設定色彩的項目也可支援 24 位元或高的色彩值，透過<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>介面。 MPF<xref:Microsoft.VisualStudio.Package.ColorableItem>類別支援<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>正常的色彩以及建構函式中指定介面和 24 位元色彩。 如需其他詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Package.ColorableItem> 類別。 下列範例示範如何設定關鍵字和註解的 24 位元色彩。 使用者的桌面，支援 24 位元色彩時，會使用 24 位元色彩否則，會使用一般文字色彩。  
  
 請記住，這些是您的語言; 的預設色彩使用者可以變更這些色彩為他們想要的任何內容。  
  
### <a name="example"></a>範例  
 此範例示範一種方式宣告並填入使用自訂色彩項目的陣列<xref:Microsoft.VisualStudio.Package.ColorableItem>類別。 此範例會設定使用 24 位元色彩的關鍵字和註解色彩。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private ColorableItem[] m_colorableItems;  
  
        TestLanguageService() : base()  
        {  
            m_colorableItems = new ColorableItem[] {  
                new ColorableItem("TestLanguage - Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage - Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage - Comment",  
                                  "Comment",  
                                  COLORINDEX.CI_DARKGREEN,  
                                  COLORINDEX.CI_LIGHTGRAY,  
                                  System.Drawing.Color.FromArgb(32,128,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT)  
                // ...  
                // Add as many colorable items as you want to support.  
            };  
        }  
    }  
}  
```  
  
## <a name="the-colorizer-class-and-the-scanner"></a>色彩標示器類別和掃描器  
 基底<xref:Microsoft.VisualStudio.Package.LanguageService>類別具有<xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A>方法，instantiantes<xref:Microsoft.VisualStudio.Package.Colorizer>類別。 傳回從掃描器<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法傳遞至<xref:Microsoft.VisualStudio.Package.Colorizer>類別建構函式。  
  
 您必須實作<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>自己的版本中的方法<xref:Microsoft.VisualStudio.Package.LanguageService>類別。 <xref:Microsoft.VisualStudio.Package.Colorizer>類別使用掃描器來取得語彙基元色彩的所有資訊。  
  
 掃描器必須填入<xref:Microsoft.VisualStudio.Package.TokenInfo>結構的每個權杖它找到。 此結構包含的資訊，例如權杖的範圍所佔據的色彩索引，若要使用，哪種類型是權杖和權杖的觸發程序 (請參閱<xref:Microsoft.VisualStudio.Package.TokenTriggers>)。 只有範圍和色彩索引所需的顏色標示<xref:Microsoft.VisualStudio.Package.Colorizer>類別。  
  
 在 儲存色彩索引<xref:Microsoft.VisualStudio.Package.TokenInfo>結構通常是從值<xref:Microsoft.VisualStudio.Package.TokenColor>列舉型別，可提供多個對應到各種不同的語言項目，例如關鍵字和運算子的具名索引。 如果您自訂色彩項目清單上的相符項目中呈現的項目<xref:Microsoft.VisualStudio.Package.TokenColor>列舉型別，則您可以只使用列舉型別做為色彩的每個語彙基元。 不過，如果您有其他可設定色彩的項目，或不想使用現有的值，依此順序，您可以排列您的自訂色彩的項目清單，以符合您的需求，並傳回適當的索引，該清單。 請務必要轉換的索引<xref:Microsoft.VisualStudio.Package.TokenColor>時將它儲存在<xref:Microsoft.VisualStudio.Package.TokenInfo>結構;[!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)]看到只有索引。  
  
### <a name="example"></a>範例  
 下列範例示範如何掃描器可能會識別三個語彙基元的型別： 數字、 標點符號及識別項 （任何項目不是數字或標點符號）。 這個範例是僅供示範用途，並不代表完整的剖析器和掃描器實作。 它會假設沒有`Lexer`類別搭配`GetNextToken()`方法會傳回字串。  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    private Lexer lex;  
  
    public class TestScanner : IScanner  
    {  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false;  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                char firstChar = token[0];  
                if (Char.IsPunctuation(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                }  
                else if (Char.IsNumber(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Literal;  
                    tokenInfo.Color = TokenColor.Number;  
                }  
                else  
                {  
                    tokenInfo.Type = TokenType.Identifier;  
                    tokenInfo.Color = TokenColor.Identifier;  
                }  
            }  
            return foundToken;  
        }  
```  
  
## <a name="see-also"></a>另請參閱  
 [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)   
 [舊版語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)