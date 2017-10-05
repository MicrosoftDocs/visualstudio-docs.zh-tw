---
title: "語法色彩標示在舊版語言服務 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 1ec6732b511d437a24149d9cd4b20e593a13a8f0
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>語法色彩標示在舊版語言服務
語法顏色標示是會導致不同的項目要顯示不同的色彩和樣式原始程式檔中的程式語言的功能。 若要支援這項功能，您需要提供剖析器或掃描器可以識別語彙項目或檔案中的語彙基元的類型。 許多語言來標示它們色彩不同的方式區分關鍵字、 分隔符號 （例如括號或大括號） 和註解。  
  
 舊版語言服務會實作成 VSPackage 的一部分，但實作語言服務功能的較新方法是使用 MEF 擴充功能。 若要深入了解，請參閱[擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。  
  
> [!NOTE]
>  我們建議您開始使用新的編輯器 API 儘速。 這會提升語言服務的效能，並可讓您充分利用新編輯器功能。  
  
## <a name="implementation"></a>實作  
 為了支援顏色標示，managed 的封裝架構 (MPF) 包含<xref:Microsoft.VisualStudio.Package.Colorizer>類別，它會實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>介面。 這個類別會與互動<xref:Microsoft.VisualStudio.Package.IScanner>判斷語彙基元和色彩。 如需掃描器的詳細資訊，請參閱[舊版語言服務剖析器與掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)。 <xref:Microsoft.VisualStudio.Package.Colorizer>類別標記的語彙基元的色彩資訊的每個字元，然後返回編輯器 中顯示的原始程式檔中的該資訊。  
  
 傳回至編輯器的色彩資訊是色彩的項目清單中的索引。 每個色彩的項目指定色彩值與一系列的字型屬性，例如粗體或刪除線。 編輯器提供一組預設色彩的項目可以使用您語言的服務。 您只需要為指定適當的色彩索引，針對每個語彙基元的類型。 不過，您可以提供一組自訂色彩項目和索引，您提供的權杖，並參考您自己的色彩而不是預設清單的項目清單。 您也必須設定`RequestStockColors`登錄項目為 0 (或不要指定`RequestStockColors`所有項目) 來支援自訂色彩。 您可以設定具名參數，以與此登錄項目<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>使用者定義的屬性。 如需有關註冊語言服務及設定其選項的詳細資訊，請參閱[註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)。  
  
## <a name="custom-colorable-items"></a>自訂色彩項目  
 若要提供您自己自訂的色彩項目，您必須覆寫<xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A>和<xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A>方法<xref:Microsoft.VisualStudio.Package.LanguageService>類別。 第一種方法傳回的語言服務支援的自訂色彩項目數目，第二個取得自訂色彩項目的索引。 您建立預設的自訂色彩項目清單。 在語言服務的建構函式，您只需要為提供每個色彩項目的名稱。 Visual Studio 會自動處理的情況，使用者在選取一組不同的色彩項目。 此名稱都會顯示於**字型和色彩**屬性頁上的**選項**對話方塊 (可從 Visual Studio**工具**功能表)，此名稱會決定哪一個使用者已覆寫的色彩。 儲存在登錄中的快取且色彩名稱來存取使用者的選擇。 **字型和色彩**屬性頁面會列出所有的色彩名稱，依字母順序，因此您可以使用您語言的名稱; 每個色彩名稱前面來群組您的自訂色彩，例如"**TestLanguage 註解**"和"**TestLanguage 關鍵字**"。 您可以分組您色彩項目類型，或者"**註解 (TestLanguage)**"和"**關鍵字 (TestLanguage)**"。 最好使用群組依據語言名稱。  
  
> [!CAUTION]
>  強烈建議您避免與現有的色彩項目的名稱衝突的色彩項目的名稱包含語言名稱。  
  
> [!NOTE]
>  如果您變更其中一個色彩名稱在開發期間，您必須重設 Visual Studio 建立第一次存取您的色彩的快取。 您可以藉由執行**重設實驗登錄區**從 Visual Studio SDK 程式功能表命令。  
  
 請注意色彩的項目清單中的第一個項目從未參考。 Visual Studio 一律會提供的預設文字色彩及該項目的屬性。 最簡單的方式來處理這是提供做為第一個項目預留位置色彩項目。  
  
### <a name="high-color-colorable-items"></a>高彩色彩的項目  
 色彩的項目也可支援透過 24 位元或高的色彩值<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>介面。 MPF<xref:Microsoft.VisualStudio.Package.ColorableItem>類別支援<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>介面和 24 位元色彩指定於建構函式，以及一般的色彩。 如需其他詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Package.ColorableItem> 類別。 下列範例會示範如何設定關鍵字和註解的 24 位元色彩。 當使用者的桌面上; 支援 24 位元色彩時使用的 24 位元色彩否則，會使用一般文字色彩。  
  
 請記住，這些是您的語言; 預設色彩使用者可以變更這些色彩為任何他們想要的結果。  
  
### <a name="example"></a>範例  
 這個範例會示範如何宣告及填入使用自訂色彩項目的陣列<xref:Microsoft.VisualStudio.Package.ColorableItem>類別。 此範例會設定使用 24 位元色彩的關鍵字和註解的色彩。  
  
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
 基底<xref:Microsoft.VisualStudio.Package.LanguageService>類別具有<xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A>方法該 instantiantes<xref:Microsoft.VisualStudio.Package.Colorizer>類別。 傳回從掃描器<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法傳遞至<xref:Microsoft.VisualStudio.Package.Colorizer>類別建構函式。  
  
 您必須實作<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>方法的版本中<xref:Microsoft.VisualStudio.Package.LanguageService>類別。 <xref:Microsoft.VisualStudio.Package.Colorizer>類別使用掃描器來取得所有語彙基元的色彩資訊。  
  
 掃描器必須填入<xref:Microsoft.VisualStudio.Package.TokenInfo>結構的每個權杖，會發現。 此結構包含的資訊，例如範圍語彙基元所佔的色彩索引，若要使用，哪種類型是語彙基元，和權杖的觸發程序 (請參閱<xref:Microsoft.VisualStudio.Package.TokenTriggers>)。 只有範圍和色彩索引所需的顏色標示所<xref:Microsoft.VisualStudio.Package.Colorizer>類別。  
  
 色彩索引儲存在<xref:Microsoft.VisualStudio.Package.TokenInfo>結構通常是從值<xref:Microsoft.VisualStudio.Package.TokenColor>列舉型別，提供多個對應至不同的語言項目，例如關鍵字和運算子的具名索引。 如果您自訂的色彩項目會列出符合的項目會出現在<xref:Microsoft.VisualStudio.Package.TokenColor>列舉型別，則您可以只使用列舉型別為色彩的每個語彙基元。 不過，如果您有其他色彩的項目，或您不想要使用的現有值的順序，您可以排列您的自訂色彩項目清單，來符合您的需求，並傳回適當的索引至該清單。 請務必將轉換的索引<xref:Microsoft.VisualStudio.Package.TokenColor>時儲存<xref:Microsoft.VisualStudio.Package.TokenInfo>結構;[!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)]看到只有索引。  
  
### <a name="example"></a>範例  
 下列範例示範如何將掃描器可能會識別三個語彙基元的型別： 數字、 標點符號和識別項 （任何項目不是數字或標點符號）。 此範例僅供說明之，並不代表完整的剖析器與掃描器實作。 它會假設沒有`Lexer`類別`GetNextToken()`方法會傳回字串。  
  
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
 [舊版語言服務剖析器與掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)
