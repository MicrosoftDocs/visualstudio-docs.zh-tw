---
title: 舊版語言服務中的語法標示 |Microsoft Docs
description: 瞭解如何藉由提供可識別詞法元素或標記類型的剖析器或掃描器，來支援舊版語言服務中的語法顏色標示。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c51885e593fabffab80d11c930100f3cc719dff8
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877750"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>舊版語言服務中的語法上色
語法顏色標示是一種功能，可在不同的色彩和樣式的原始程式檔中顯示不同的程式設計語言元素。 若要支援這項功能，您必須提供剖析器或掃描器，以識別檔案中的詞法元素或標記類型。 許多語言會區分關鍵字、分隔符號 (例如括弧或大括弧) 和批註，方法是以不同方式標示它們。

 舊版語言服務會實作為 VSPackage 的一部分，但是執行語言服務功能的較新方法是使用 MEF 延伸模組。 若要深入瞭解，請參閱 [擴充編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。

> [!NOTE]
> 建議您儘快開始使用新的編輯器 API。 這可改善您的語言服務效能，並讓您利用新的編輯器功能。

## <a name="implementation"></a>實作
 為支援顏色標示，受管理的封裝架構 (MPF) 包含 <xref:Microsoft.VisualStudio.Package.Colorizer> 可實介面的類別 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 。 這個類別會與 <xref:Microsoft.VisualStudio.Package.IScanner> 進行互動，以判斷 token 和色彩。 如需有關掃描器的詳細資訊，請參閱 [舊版語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)。 <xref:Microsoft.VisualStudio.Package.Colorizer>類別接著會使用色彩資訊來標記標記的每個字元，並將該資訊傳回給顯示來源檔案的編輯器。

 傳回給編輯器的色彩資訊是可設定色彩專案清單中的索引。 每個可設定色彩專案都會指定一個色彩值和一組字型屬性，例如粗體或刪除線。 編輯器會提供一組可供您的語言服務使用的預設可設定色彩專案。 您只需要為每個權杖類型指定適當的色彩索引。 不過，您可以提供一組自訂的可設定色彩專案和您為權杖提供的索引，並參考您自己的可設定色彩專案清單，而不是預設清單。 您也必須將登錄 `RequestStockColors` 專案設定為 0 (或不指定 `RequestStockColors` 所有) 的專案，以支援自訂色彩。 您可以使用使用者定義屬性的具名引數來設定此登錄專案 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 。 如需註冊語言服務和設定其選項的詳細資訊，請參閱 [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)。

## <a name="custom-colorable-items"></a>自訂可設定色彩的項目
 若要提供您自己的自訂可設定色彩專案，您必須覆寫 <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> 類別上的和方法 <xref:Microsoft.VisualStudio.Package.LanguageService> 。 第一個方法會傳回語言服務支援的自訂可設定色彩專案數目，而第二個方法會依索引取得自訂可設定色彩專案。 您可以建立自訂可設定色彩專案的預設清單。 在您的語言服務的函式中，您只需要為每個可設定色彩專案提供名稱。 Visual Studio 會自動處理使用者選取一組不同可設定色彩專案的情況。 這個名稱會顯示在 [**選項**] 對話方塊的 [字型 **和色彩**] 屬性頁中， (可從 Visual Studio [**工具**] 功能表) ，而此名稱會決定使用者已覆寫的色彩。 使用者的選擇會儲存在登錄中的快取中，並以色彩名稱進行存取。 [字型 **和色彩** ] 屬性頁會依字母順序列出所有色彩名稱，因此您可以在每個色彩名稱之前加上您的語言名稱來分組自訂色彩;例如，"**TestLanguage-Comment**" 和 "**TestLanguage" 關鍵字**。 或者，您可以依類型、"**Comment (TestLanguage)**" 和 "**關鍵字 (TestLanguage)**" 來分組您的可設定色彩專案。 偏好依語言名稱分組。

> [!CAUTION]
> 強烈建議您在可設定色彩專案名稱中包含語言名稱，以避免與現有的可設定色彩專案名稱發生衝突。

> [!NOTE]
> 如果您在開發期間變更其中一個色彩的名稱，則必須重設 Visual Studio 第一次存取您的色彩時所建立的快取。 若要這麼做，您可以從 Visual Studio SDK 程式功能表中，執行 [ **重設實驗 Hive** ] 命令。

 請注意，您可設定色彩專案清單中的第一個專案絕對不會被參考。 Visual Studio 一律會提供該專案的預設文字色彩和屬性。 處理這項工作的最簡單方式，就是提供預留位置可設定色彩專案做為第一個專案。

### <a name="high-color-colorable-items"></a>高彩可設定色彩專案
 可設定色彩專案也可以透過介面支援24位或高的色彩值 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 。 MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> 類別支援 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 介面，而24位色彩則是在函式中指定，以及一般色彩。 如需其他詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Package.ColorableItem> 類別。 下列範例顯示如何設定關鍵字和批註的24位色彩。 當使用者的桌面上支援24位色彩時，會使用24位色彩;否則，會使用一般文字色彩。

 請記住，這些是您語言的預設色彩;使用者可以將這些色彩變更為任何想要的色彩。

### <a name="example"></a>範例
 這個範例示範使用類別來宣告和填入自訂可設定色彩專案陣列的一種方式 <xref:Microsoft.VisualStudio.Package.ColorableItem> 。 此範例會使用24位色彩來設定關鍵字和批註色彩。

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
 基類 <xref:Microsoft.VisualStudio.Package.LanguageService> 具有 <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> instantiantes 類別的方法 <xref:Microsoft.VisualStudio.Package.Colorizer> 。 從方法傳回的掃描器 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 會傳遞至類別的函式 <xref:Microsoft.VisualStudio.Package.Colorizer> 。

 您必須 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 在自己的類別版本中執行方法 <xref:Microsoft.VisualStudio.Package.LanguageService> 。 <xref:Microsoft.VisualStudio.Package.Colorizer>類別會使用掃描器來取得所有 token 色彩資訊。

 掃描器需要為 <xref:Microsoft.VisualStudio.Package.TokenInfo> 它找到的每個權杖填入結構。 此結構包含的資訊包括權杖佔用的範圍、要使用的色彩索引、權杖的類型，以及權杖觸發程式 (查看 <xref:Microsoft.VisualStudio.Package.TokenTriggers>) 。 只有範圍和色彩索引需要類別的顏色標示 <xref:Microsoft.VisualStudio.Package.Colorizer> 。

 儲存在結構中的色彩索引 <xref:Microsoft.VisualStudio.Package.TokenInfo> 通常是列舉中的值 <xref:Microsoft.VisualStudio.Package.TokenColor> ，可提供數個對應至各種語言專案（例如關鍵字和運算子）的命名索引。 如果您的自訂可設定色彩專案清單符合列舉中所呈現的專案 <xref:Microsoft.VisualStudio.Package.TokenColor> ，您可以只使用列舉作為每個標記的色彩。 但是，如果您有其他可設定色彩專案，或不想要使用該順序中的現有值，您可以排列自訂可設定色彩專案清單以符合您的需求，並將適當的索引傳回至該清單。 當將索引儲存在結構中時，請務必將索引轉換成， <xref:Microsoft.VisualStudio.Package.TokenColor> <xref:Microsoft.VisualStudio.Package.TokenInfo> [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] 只看到索引。

### <a name="example"></a>範例
 下列範例顯示掃描器識別三種權杖類型的方式：數位、標點符號和識別碼 (不是數位或標點符號的任何) 。 此範例僅供說明之用，並不代表完整的剖析器和掃描器執行。 它會假設有一個 `Lexer` 具有傳回字串之 `GetNextToken()` 方法的類別。

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
