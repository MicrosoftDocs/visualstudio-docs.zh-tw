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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19561363affada05154e15142bd32a30a5d051d0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722837"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>舊版語言服務中的語法上色
語法顏色標示功能會導致程式語言的不同元素以不同的色彩和樣式顯示在原始程式檔中。 若要支援這項功能，您必須提供剖析器或掃描器，以識別檔案中的詞法元素或 token 的類型。 許多語言會以不同的方式來區分關鍵字、分隔符號（例如括弧或大括弧）和批註。

 舊版語言服務會實作為 VSPackage 的一部分，但執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解，請參閱[擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將可改善語言服務的效能，並可讓您利用新的編輯器功能。

## <a name="implementation"></a>實作
 為了支援顏色標示，managed package framework （MPF）包含 <xref:Microsoft.VisualStudio.Package.Colorizer> 類別，它會執行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 介面。 這個類別會與 <xref:Microsoft.VisualStudio.Package.IScanner> 互動，以判斷權杖和色彩。 如需掃描器的詳細資訊，請參閱[舊版語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)。 @No__t_0 類別接著會以色彩資訊標示標記的每個字元，並將該資訊傳回給顯示原始程式檔的編輯器。

 傳回至編輯器的色彩資訊是可設定色彩專案清單中的索引。 每個可設定色彩專案都會指定色彩值和一組字型屬性，例如粗體或刪除線。 編輯器會提供一組您的語言服務可使用的預設可設定色彩專案。 您只需要為每個 token 類型指定適當的色彩索引。 不過，您可以提供一組自訂的可設定色彩專案，以及您為權杖提供的索引，並參考您自己的可設定色彩專案清單，而不是預設清單。 您也必須將 `RequestStockColors` 登錄專案設定為0（或不要指定 [`RequestStockColors` 專案]），以支援自訂色彩。 您可以使用名為的參數，將這個登錄專案設定為 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 使用者定義的屬性。 如需註冊語言服務和設定其選項的詳細資訊，請參閱[註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)。

## <a name="custom-colorable-items"></a>自訂可設定色彩的項目
 若要提供您自己的自訂可設定色彩專案，您必須覆寫 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別上的 <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> 和 <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> 方法。 第一個方法會傳回您的語言服務支援的自訂可設定色彩專案數目，第二個方法則會依索引取得自訂可設定色彩專案。 您可以建立自訂可設定色彩專案的預設清單。 在語言服務的函式中，您只需要提供每個具有名稱的可設定色彩專案。 Visual Studio 會自動處理使用者選取不同可設定色彩專案集的情況。 這個名稱會出現在 **選項** 對話方塊上的 字型**和色彩** 屬性頁中（可從 Visual Studio**工具** 功能表取得），而這個名稱會決定使用者已覆寫的色彩。 使用者的選擇會儲存在登錄中的快取中，並以色彩名稱來存取。 [字型**和色彩**] 屬性頁會以字母順序列出所有的色彩名稱，因此您可以在每個色彩名稱前面加上您的語言名稱，以分組您的自訂色彩。例如，「**TestLanguage-Comment**」和「**TestLanguage-關鍵字**」。 或者，您可以依類型、"**Comment （TestLanguage）** " 和 "**關鍵字（TestLanguage）** " 將可設定色彩專案分組。 偏好依語言名稱分組。

> [!CAUTION]
> 強烈建議您在可設定色彩專案名稱中包含語言名稱，以避免與現有的可設定色彩專案名稱發生衝突。

> [!NOTE]
> 如果您在開發期間變更其中一種色彩的名稱，就必須重設第一次存取您的色彩時 Visual Studio 所建立的快取。 若要這麼做，您可以從 [Visual Studio SDK 程式] 功能表執行 [**重設實驗 Hive** ] 命令。

 請注意，您可設定色彩專案清單中的第一個專案永遠不會被參考。 Visual Studio 一律會提供該專案的預設文字色彩和屬性。 最簡單的處理方式，就是提供預留位置可設定色彩專案作為第一個專案。

### <a name="high-color-colorable-items"></a>高彩可設定色彩專案
 可設定色彩專案也可以透過 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 介面來支援24位或高彩的值。 MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> 類別支援 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 介面，而24位色彩則是在此函式中指定，以及一般色彩。 如需其他詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Package.ColorableItem> 類別。 下列範例顯示如何設定關鍵字和批註的24位色彩。 當使用者的桌面支援24位色彩時，會使用24位色彩;否則，會使用一般文字色彩。

 請記住，這些是您語言的預設色彩;使用者可以將這些色彩變更為任何想要的色彩。

### <a name="example"></a>範例
 這個範例示範使用 <xref:Microsoft.VisualStudio.Package.ColorableItem> 類別來宣告和填入自訂可設定色彩專案陣列的一種方式。 這個範例會使用24位色彩來設定關鍵字和批註色彩。

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

## <a name="the-colorizer-class-and-the-scanner"></a>著色器類別和掃描器
 基底 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別具有可 instantiantes <xref:Microsoft.VisualStudio.Package.Colorizer> 類別的 <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> 方法。 從 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 方法傳回的掃描器會傳遞至 <xref:Microsoft.VisualStudio.Package.Colorizer> 類別的函式。

 您必須在自己的 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別版本中執行 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 方法。 @No__t_0 類別會使用掃描器來取得所有權杖色彩資訊。

 掃描器必須為它找到的每個權杖填入 <xref:Microsoft.VisualStudio.Package.TokenInfo> 結構。 此結構包含的資訊包括權杖佔用的範圍、要使用的色彩索引、權杖的類型，以及權杖觸發程式（請參閱 <xref:Microsoft.VisualStudio.Package.TokenTriggers>）。 @No__t_0 類別的顏色標示只需要 span 和色彩索引。

 儲存在 <xref:Microsoft.VisualStudio.Package.TokenInfo> 結構中的色彩索引通常是來自 <xref:Microsoft.VisualStudio.Package.TokenColor> 列舉的值，它提供了一些對應至各種語言元素（例如關鍵字和運算子）的命名索引。 如果您的自訂可設定色彩專案清單符合 <xref:Microsoft.VisualStudio.Package.TokenColor> 列舉中所呈現的專案，則您可以只使用列舉作為每個標記的色彩。 不過，如果您有其他可設定色彩專案，或不想使用該順序中的現有值，您可以安排自訂的可設定色彩專案清單以符合您的需求，並將適當的索引傳回該清單中。 在 <xref:Microsoft.VisualStudio.Package.TokenInfo> 結構中儲存索引時，請務必將其轉換為 <xref:Microsoft.VisualStudio.Package.TokenColor>。 [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] 只會看到索引。

### <a name="example"></a>範例
 下列範例會示範掃描器如何識別三種 token 類型：數位、標點符號和識別碼（不是數位或標點符號的任何專案）。 這個範例僅供說明之用，不代表完整的剖析器和掃描器執行。 它假設有一個 `Lexer` 類別，其中有一個會傳回字串的 `GetNextToken()` 方法。

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

## <a name="see-also"></a>請參閱
- [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)
- [舊版語言服務的剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)