---
title: 舊語言服務中的語法著色 |微軟文件
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
ms.openlocfilehash: 02723a09254255b98291cb921ae5ec091d8b9859
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704699"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>舊版語言服務中的語法上色
語法著色是一種功能,它會導致程式設計語言的不同元素以不同的顏色和樣式顯示在源檔中。 要支援此功能,您需要提供一個解析器或掃描器,用於標識檔中的詞法元素或權杖的類型。 許多語言通過以不同的方式著色關鍵字、分隔符(如括弧或大括弧)和註釋來區分它們。

 舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解更多資訊,請參閱[延伸編輯器和語言服務](../../extensibility/extending-the-editor-and-language-services.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將提高語言服務的性能,並允許您利用新的編輯器功能。

## <a name="implementation"></a>實作
 為了支援著色,託管包框架 (MPF) 包括<xref:Microsoft.VisualStudio.Package.Colorizer>實現<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>介面的 類。 類與交互<xref:Microsoft.VisualStudio.Package.IScanner>以確定權杖和顏色。 有關掃描器的詳細資訊,請參閱[舊語言服務解析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)。 然後<xref:Microsoft.VisualStudio.Package.Colorizer>,類使用顏色信息標記權杖的每個字元,並將該資訊返回給顯示源檔的編輯器。

 返回到編輯器的顏色資訊是可著色項清單中的索引。 每個可著色項指定顏色值和一組字體屬性,如粗體或粗體。 編輯器提供一組預設的可著色項,語言服務可以使用這些專案。 您只需為每個令牌類型指定適當的顏色索引。 但是,您可以提供一組自定義可著色項和為令牌提供的索引,並引用您自己的可著色項清單,而不是默認清單。 還必須將`RequestStockColors`註冊表項設置為 0(或`RequestStockColors`根本不指定 該條目)以支援自定義顏色。 您可以使用命名參數將此註冊表項設置為<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>使用者定義的屬性。 有關註冊語言服務並設定其選項的詳細資訊,請參閱[註冊舊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)。

## <a name="custom-colorable-items"></a>自訂可設定色彩的項目
 要提供您自己的自定義可著色項,必須重寫<xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A><xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A><xref:Microsoft.VisualStudio.Package.LanguageService>類 上的和方法。 第一種方法返回語言服務支援的自定義可著色項數,第二種方法按索引獲取自定義可著色項。 建立自定義可著色項的預設清單。 在語言服務的建構函數中,您只需為每個可著色項提供名稱。 Visual Studio 會自動處理使用者選擇一組不同的可著色項目的情況。 此名稱是「**選項**」對話框(可從可視化工作室**工具**選單)上的「**字型與顏色**」 屬性頁中顯示的名稱,此名稱確定使用者已覆蓋的顏色。 使用者的選擇存儲在註冊表中的緩存中,並由顏色名稱訪問。 **"字型和顏色**"屬性頁按字母順序出所有顏色名稱,因此您可以按語言名稱在每個顏色名稱之前對自定義顏色進行分組;例如,「**測試語言-註釋**」和「**測試語言-關鍵字**」。 或者,您可以按類型對可著色項目進行分組,"**註釋(測試語言)"** 和「**關鍵字(測試語言)」。** 首選按語言名稱分組。

> [!CAUTION]
> 強烈建議您在可著色項名稱中包括語言名稱,以避免與現有可著色項名稱發生衝突。

> [!NOTE]
> 如果在開發過程中更改了其中一種顏色的名稱,則必須重置 Visual Studio 首次訪問顏色時創建的緩存。 您可以通過從可視化 Studio SDK 程式功能表中執行 **「重置實驗蜂巢**」命令來執行此操作。

 請注意,永遠不會引用可著色項清單中的第一項。 Visual Studio 始終提供該專案的預設文本顏色和屬性。 處理此問題的最簡單方法是將占位符著色為第一項。

### <a name="high-color-colorable-items"></a>高彩色可著色物品
 可著色項還可以通過<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>介面支援 24 位元或高顏色值。 MPF<xref:Microsoft.VisualStudio.Package.ColorableItem>類<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>支援 介面,24 位顏色與普通顏色一起在構造函數中指定。 如需其他詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Package.ColorableItem> 類別。 下面的範例展示如何為關鍵字和註釋設定 24 位元顏色。 當使用者的桌面上支援 24 位元顏色時,將使用 24 位元顏色;否則,將使用普通文本顏色。

 請記住,這些是語言的默認顏色;用戶可以將這些顏色更改為所需的任何顏色。

### <a name="example"></a>範例
 此範例顯示了使用 類聲明和填充自定義可著色項陣列<xref:Microsoft.VisualStudio.Package.ColorableItem>的一種方法。 本示例使用 24 位元顏色設定關鍵字和註釋顏色。

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
 基<xref:Microsoft.VisualStudio.Package.LanguageService>類具有實<xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A>例<xref:Microsoft.VisualStudio.Package.Colorizer>化 類的方法。 從方法返回的<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>掃描程式將傳遞<xref:Microsoft.VisualStudio.Package.Colorizer>給 類構造函數。

 必須在自己的<xref:Microsoft.VisualStudio.Package.LanguageService>類版本中<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>實現該方法。 類<xref:Microsoft.VisualStudio.Package.Colorizer>使用掃描器獲取所有權杖顏色資訊。

 掃描器需要為其找到的每個令牌<xref:Microsoft.VisualStudio.Package.TokenInfo>填充一個結構。 此結構包含諸如權杖佔用的跨度、要使用的顏色索引、令牌的類型和權杖觸發器(請參閱<xref:Microsoft.VisualStudio.Package.TokenTriggers>)等資訊。 <xref:Microsoft.VisualStudio.Package.Colorizer>類著色只需要範圍和顏色索引。

 存儲在結構中<xref:Microsoft.VisualStudio.Package.TokenInfo>的顏色索引通常是枚舉中的<xref:Microsoft.VisualStudio.Package.TokenColor>值 ,它提供與各種語言元素(如關鍵字和運算元)對應的命名索引。 如果自定義可著色項清單與枚舉中<xref:Microsoft.VisualStudio.Package.TokenColor>顯示的專案匹配,則只需將枚舉用作每個標記的顏色即可。 但是,如果您有其他可著色項,或者不希望按該順序使用現有值,則可以排列自定義可著色項清單以滿足您的需要,並將相應的索引返回到該清單中。 只需在<xref:Microsoft.VisualStudio.Package.TokenColor><xref:Microsoft.VisualStudio.Package.TokenInfo>結構中儲存索引時,請確保將索引轉換為[!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)]只能看到索引。

### <a name="example"></a>範例
 下面的範例顯示了掃描器如何識別三種權杖類型:數位、標點符號和識別碼(任何不是數位或標點符號)。 此示例僅用於說明目的,不表示全面的解析器和掃描器實現。 它假定有一個`Lexer``GetNextToken()`類,其方法返回字串。

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
- [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)
- [舊版語言服務的剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)
