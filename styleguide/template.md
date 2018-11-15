# <a name="metadata-and-markdown-template"></a>中繼資料和 Markdown 範本

此核心文件範本包含 Markdown 語法，以及設定中繼資料的指導。 若要善加利用它，您必須檢閱[原始的 Markdown (英文)](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) 和[轉譯後的檢視 (英文)](https://github.com/dotnet/docs/blob/master/styleguide/template.md) (例如，原始的 Markdown 會顯示中繼資料區塊，而轉譯後的檢視則不會)。

在建立 Markdown 檔案的時候，您應將此範本複製到新的檔案，填入下列指定的中繼資料，將上方的 H1 標題設為文章的標題，然後刪除內容。 


## <a name="metadata"></a>中繼資料 

完整的中繼資料區塊如上 (以[原始的 Markdown (英文)](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) 顯示)，其中分為必要欄位和選擇性欄位。 重點提示：

- 請「務必」在中繼資料項目的值和冒號 (:) 之間加上一個空格。
- 如果選擇性的中繼資料沒有值，請將它移除或使用 # 註解化 (請勿保留空白或使用 "na")；如果要在已經註解化的項目新增值，請務必移除 #。
- 在值中出現冒號 (例如標題) 會中斷中繼資料剖析器。 在此情況下，請使用雙引號括住標題 (例如，`title: "Writing .NET Core console apps: An advanced step-by-step guide"`)。
- **title**：此標題會出現在搜尋引擎的搜尋結果。 您可以加上垂直線符號 (|)，並在它之後加上產品名稱 (例如，`title: Developing Libraries with Cross Platform Tools | .NET Core`)。 該標題不需要與 H1 標題中的標題相同，且應包含小於或等於 65 個字元 (包括「| 產品名稱」)。
- **author**、**manager**、**ms.reviewer**：author 欄位應包含該作者的 **GitHub 使用者名稱**，而不是別名。  "manager" 和 "ms.reviewer" 欄位則應包含 Microsoft 別名。 ms.reviewer 指定與文章或功能相關的 PM/開發人員。
- **ms.devlang** 定義技術。 一些支援的值如：dotnet、cpp、csharp、fsha、vb 和 xml。
- **ms.assetid**：這是文章的 GUID，用於商業智慧 (BI) 等內部追蹤目的。 在建立新的 Markdown 檔案時，請從 [https://www.guidgenerator.com](https://www.guidgenerator.com) 取得 GUID。 

## <a name="basic-markdown-gfm-and-special-characters"></a>基本 Markdown、GFM 和特殊字元

支援所有基本和 GitHub Flavored Markdown (GFM)。 如需詳細資訊，請參閱：

- [基準 Markdown 語法 (英文)](https://daringfireball.net/projects/markdown/syntax)
- [GFM 文件 (英文)](https://guides.github.com/features/mastering-markdown)

Markdown 使用 \*、\` 和 \# 等特殊字元來設定格式。 如果要在內容中包含這些字元，請遵循下列其中一種作法：

- 在該特殊字元前面加上反斜線來將它「逸出」(例如，\* 逸出為 `\*`)
- 使用該字元的 [HTML 實體代碼 (英文)](http://www.ascii.cl/htmlcodes.htm) (例如，&#42; 為 `&#42;`)。

## <a name="file-name"></a>檔案名稱

檔案名稱使用下列規則︰
* 只包含小寫字母、數字和連字號。
* 不使用空格或標點符號。 使用連字號來分隔檔名中的文字和數字。
* 使用明確的動作動詞，例如 develop、buy、build、troubleshoot。 不使用 -ing 字詞。
* 不使用短字詞，例如 a、and、the、in、or 等等。
* 必須為 Markdown 格式且使用副檔名 .md。
* 盡可能保持檔名簡短。 它們會是文章 URL 的一部分。  



## <a name="headings"></a>標題

使用句子樣式的大寫。 下列情況一律大寫：
- 標題的第一個字。 
- 標題中冒號後的第一個字 (例如，"How to: Sort an array")。 

標題應使用 atx 樣式，也就是在行開頭以 1 至 6 個井字號 (#) 來表示標題，這會對應到 HTML 標題層級 H1 至 H6。 上面使用的是第一和第二層級標題的範例。 

請「務必」確定主題中只有一個第一層級標題 (H1)，該標題會顯示為頁面標題。

如果您的標題結尾是 `#` 字元，則您必須在結尾另外加上一個 `#` 以使標題正確轉譯。 例如，`# Async Programming in F# #`。     

第二層級的標題會產生頁面目錄，並顯示在頁面標題下的 [本文內容] 區段中。

### <a name="third-level-heading"></a>第三層級標題
#### <a name="fourth-level-heading"></a>第四層級標題
##### <a name="fifth-level-heading"></a>第五層級標題
###### <a name="sixth-level-heading"></a>第六層級標題
 
## <a name="text-styling"></a>文字樣式

「斜體」用於檔案、資料夾、路徑 (較長的項目請分割為各行) - 新詞彙 - URL (除非轉譯為連結，這是預設值)。

**粗體** 用於 UI 元素。

## <a name="links"></a>「連結」

### <a name="internal-links"></a>內部連結

若要連結到同一個 Markdown 檔案中的標題 (又稱錨點連結)，您需要找出該標題的識別碼。 若要確認識別碼，請檢視轉譯文章的原始程式碼，以找出該標題的識別碼 (例如，`id="blockquote"`)，然後使用「# + 識別碼」來連結 (例如，`#blockquote`)。
此識別碼是依據標題文字而自動產生。 舉例來說，若某章節名稱為 `## Step 2`，則識別碼會是 `id="step-2"`。

- 範例：[第 1 章](#chapter-1)

若要連結到同一個存放庫中的 Markdown 檔案，請使用[相對連結](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2)，且檔案名稱結尾包含 ".md"。

- 範例：[讀我檔案](../readme.md)
- 範例：[歡迎使用 .NET](../docs/welcome.md)

若要連結到相同存放庫中 Markdown 檔案內的標題，請使用「相對連結 + 井字號」來連結。

- 範例︰[.NET 社群](../docs/welcome.md#community)

### <a name="external-links"></a>外部連結

若要連結到外部檔案，請使用完整 URL 作為連結。

- 範例：[GitHub](http://www.github.com)

如果 Markdown 檔案中出現 URL，系統會將它轉換成可點擊的連結。

- 範例： http://www.github.com

### <a name="links-to-apis"></a>API 的連結

組建系統有些延伸模組可讓我們在不需使用外部連結的情況下，連結到 .NET Core API。  
當連結到 API 時，您可以使用從原始程式碼自動產生的唯一識別碼 (UID)。

您可以使用下列其中一個語法：
1. Markdown 連結：`[link_text](xref:UID)`
2. 自動連結︰`<xref:UID>`
3. 簡短格式：`@UID`

- 範例：`@System.String`
- 範例：`[String class](xref:System.String)` 

如需使用此標記法的詳細資訊，請參閱[使用交互參照 (英文)](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html#using-cross-reference)。

> 目前沒有簡單的方法可以尋找 UID。 尋找 UID 的最佳方法是在此存放庫中搜尋：[docascode/coreapi (英文)](https://github.com/docascode/coreapi)。 我們正努力讓系統變得更好。

當 UID 包含特殊字元 \`或 \# 時，該 UID 值必須分別編碼為 HTML 代碼 %60 和 %23，如下列範例：
- 範例：@System.Threading.Tasks.Task\`1 變成 `@System.Threading.Tasks.Task%601`
- 範例：@System.Exception.\#ctor 變成 `@System.Exception.%23ctor`

## <a name="lists"></a>清單

### <a name="ordered-lists"></a>排序清單

1. 這 
1. 是
1. 一個
1. 排序
1. 清單  


#### <a name="ordered-list-with-an-embedded-list"></a>包含內嵌清單的排序清單

1. 這裡
1. 有
1. 一個
1. 內嵌
    1. Miss Scarlett
    1. Professor Plum
1. 排序
1. 清單


### <a name="unordered-lists"></a>未排序清單

- 這個
- 是
- 一個
- 項目符號
- 清單


##### <a name="unordered-list-with-an-embedded-list"></a>包含內嵌清單的未排序清單

- 這個 
- 項目符號 
- 清單
    - Mrs. Peacock
    - Mr. Green
- 包含  
- 另一個
    1. Colonel Mustard
    1. Mrs. White
- 清單


## <a name="horizontal-rule"></a>水平線

---

## <a name="tables"></a>資料表

| 資料表        | 很           | 酷  |
| ------------- |:-------------:| -----:|
| 欄 3 為      | 靠右對齊 | $1600 |
| 欄 2 為      | 置中      |   $12 |
| 欄 1 為預設 | 靠左對齊     |    $1 |

您可以使用 [Markdown 表格產生工具 (英文)](http://www.tablesgenerator.com/markdown_tables) 來輕鬆產生表格。 

## <a name="code"></a>程式碼

包含程式碼的最佳方法是加入實際範例的程式碼片段。 請遵循[參與指南](../CONTRIBUTING.md#contributing-to-samples)中的指示來建立範例。

您可以使用包含語法來包含程式碼：

```
[!code-csharp[<title>](<pathToFile>#<RegionName)]
```

上面的範例是顯示 C# 語法，但也支援其他語言。
針對 F# 範例使用 `code-fsharp`；針對 Visual Basic 範例使用 `code-vbnet`。
支援的其他語言：
* C++：`code-cpp`
* HTML：`code-html`
* JavaScript：`code-javascript`
* Powershell：`code-ps`
* SQL：`code-sql`
* XML：`code-xml`



取代 `<title>` 的文字會在滑鼠指向該文字時顯示。 `<pathToFile>` 是來源檔案的路徑。 `<RegionName>` 應該是原始程式碼中應包含的區域。 使用 `#region` 和 `#endregion` 前置處理器語法來指定要包含的程式碼區域。

若發生無法使用區域的情況，請在單行註解中使用 XML 元素名稱來指定程式碼片段的開頭和結尾。 例如，您可以使用 C# 撰寫：

```csharp
// <CodeToInclude>
int j = 5;
int i ; 10;
int sum = i + j;
// </CodeToInclude>
```

對於其他語言，則使用該語言的註解語法。
最後，您可以使用行號：`#L1-L10` 會包含第 1 行至第 10 行。 不建議使用行號，因為此功能不盡完善。

包含來自完整程式的程式碼片段可確保所有程式碼都經過我們的持續整合 (CI) 系統。 不過，如果您需要顯示一些造成編譯時間或執行階段錯誤的程式碼，您可以使用內嵌程式碼區塊。

### <a name="inline-code-blocks-with-language-identifier"></a>具有語言識別碼的內嵌程式碼區塊

使用「三個反引號 (\`\`\`) + 語言識別碼」，來在程式碼區塊套用該語言的語法著色。 這裡有 [GFM 語言識別碼 (英文)](https://github.com/jmm/gfm-lang-ids/wiki/GitHub-Flavored-Markdown-(GFM)-language-IDs) 的完整清單。

##### <a name="c9839"></a>C&#9839;

```c#
using System;
namespace HelloWorld
{
    class Hello 
    {
        static void Main() 
        {
            Console.WriteLine("Hello World!");

            // Keep the console window open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```
#### <a name="python"></a>Python

```python
friends = ['john', 'pat', 'gary', 'michael']
for i, name in enumerate(friends):
    print "iteration {iteration} is {name}".format(iteration=i, name=name)
```
#### <a name="powershell"></a>PowerShell

```powershell
Clear-Host
$Directory = "C:\Windows\"
$Files = Get-Childitem $Directory -recurse -Include *.log `
-ErrorAction SilentlyContinue
```

### <a name="generic-code-block"></a>一般程式碼區快

使用三個反引號 (&#96;&#96;&#96;) 撰寫一般程式碼區塊。   

> 建議的做法是搭配語言識別碼使用程式碼區塊 (如上節所述)，以確保語法在文件網站上適當地醒目顯示。 必要時才使用一般程式碼區塊。

```
function fancyAlert(arg) {
    if(arg) {
        $.docs({div:'#foo'})
    }
}
```

### <a name="inline-code"></a>內嵌程式碼

針對 `inline code` 使用反引號 (&#96;)。 針對命令列命令、資料庫資料表和資料行的名稱，以及語言關鍵字使用內嵌程式碼。

## <a name="blockquotes"></a>引文

> The drought had lasted now for ten million years, and the reign of the terrible lizards had long since ended. Here on the Equator, in the continent which would one day be known as Africa, the battle for existence had reached a new climax of ferocity, and the victor was not yet in sight. In this barren and desiccated land, only the small or the swift or the fierce could flourish, or even hope to survive.

## <a name="images"></a>影像

### <a name="static-image-or-animated-gif"></a>靜態影像或動畫 GIF

![這是替代文字](../images/Logo_DotNet.png)

### <a name="linked-image"></a>連結影像

[![連結影像的替代文字](../images/Logo_DotNet.png)](https://dot.net) 

## <a name="videos"></a>影片

### <a name="channel-9"></a>Channel 9

<iframe src="https://channel9.msdn.com/Shows/On-NET/Shipping-NET-Core-RC2--Tools-Preview-1/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

### <a name="youtube"></a>YouTube

<iframe width="420" height="315" src="https://www.youtube.com/embed/g2a4W6Q7aRw" frameborder="0" allowfullscreen></iframe>

## <a name="docsmicrosoft-extensions"></a>docs.microsoft 延伸模組

docs.microsoft 為 GitHub Flavored Markdown 提供幾個額外的延伸模組。 

### <a name="alerts"></a>警示

請務必使用下列的警示樣式，這樣它們才能在文件網站中轉譯為適當的樣式。 不過，GitHub 的轉譯引擎無法分辨這些樣式。     

#### <a name="note"></a>注意事項

> [!NOTE]
> 這是「注意事項」

#### <a name="warning"></a>警告

> [!WARNING]
> 這是「警告」

#### <a name="tip"></a>提示

> [!TIP]
> 這是「提示」

#### <a name="important"></a>重要事項

> [!IMPORTANT]
> 這是「重要事項」

它們轉譯之後看起來像這樣：![警示樣式](../images/alerts.png)

### <a name="buttons"></a>按鈕

> [!div class="button"]
[按鈕連結](../docs/core/index.md)

您可以在 [Intune 文件](https://docs.microsoft.com/intune/get-started/choose-how-to-enroll-devices)中看到按鈕的實際範例。 

### <a name="selectors"></a>選取器

> [!div class="op_single_selector"]
- [macOS](../docs/core/tutorials/using-on-macos.md)
- [Windows](../docs/core/tutorials/using-on-windows.md)

您可以在 [Intune 文件](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune#how-your-end-users-get-their-apps)中看到選取器的實際範例。

### <a name="step-by-steps"></a>逐步執行

>[!div class="step-by-step"]
[上一步](../docs/csharp/expression-trees-interpreting.md)
[下一步](../docs/csharp/expression-trees-translating.md)

您可以在 [Advanced Threat Analytics 文件](https://docs.microsoft.com/advanced-threat-analytics/deploy-use/install-ata-step2)中看到逐步執行的實際範例。