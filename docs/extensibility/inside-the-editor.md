---
title: 深入探索編輯器
description: 瞭解編輯器的子系統和功能。 您可以擴充 Visual Studio 編輯器的功能。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c0d9d20000781980535259c0a739e03a47ae53e1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869540"
---
# <a name="inside-the-editor"></a>在編輯器內

編輯器是由數個不同的子系統所組成，其設計目的是要讓編輯器文字模型與文字視圖和使用者介面分開。

這些章節描述編輯器的不同層面：

- [子系統的總覽](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [文字模型](../extensibility/inside-the-editor.md#the-text-model)

- [文字視圖](../extensibility/inside-the-editor.md#the-text-view)

這些章節描述編輯器的功能：

- [標記和分類器](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [裝飾品](../extensibility/inside-the-editor.md#adornments)

- [投影](../extensibility/inside-the-editor.md#projection)

- [大綱](../extensibility/inside-the-editor.md#outlining)

- [滑鼠系結](../extensibility/inside-the-editor.md#mouse-bindings)

- [編輯器作業](../extensibility/inside-the-editor.md#editor-operations)

- [智慧](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>子系統的總覽

### <a name="text-model-subsystem"></a>文字模型子系統

文字模型子系統負責表示文字並啟用其操作。 文字模型子系統包含 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 介面，此介面描述編輯器要顯示的字元序列。 您可以透過許多方式來修改、追蹤和操作這個文字。 文字模型也提供下列各方面的類型：

- 這項服務會將文字與檔案產生關聯，並管理檔案系統中的讀取和寫入。

- 差異服務，可尋找兩個物件序列之間的最大差異。

- 一種系統，用來根據其他緩衝區中的文字子集來描述緩衝區中的文字。

文字模型子系統是 (UI) 概念的免費使用者介面。 例如，它不負責文字格式設定或文字版面配置，也不知道可能與文字相關聯的視覺效果裝飾。

文字模型子系統的公用類型包含在 *Microsoft.VisualStudio.Text.Data.dll* 和 *Microsoft.VisualStudio.CoreUtility.dll* 中，而這些類型只相依于 .NET Framework 基類庫和 Managed Extensibility Framework (MEF) 。

### <a name="text-view-subsystem"></a>文字視圖子系統

文字視圖子系統負責格式化和顯示文字。 此子系統中的型別會分割成兩個層級，取決於型別是否依賴 Windows Presentation Foundation (WPF) 。 最重要的型別是 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 和 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> ，它會控制要顯示的一組文字行，還有插入號、選取專案，以及使用 WPF UI 元素來裝飾文字的功能。 此子系統也提供文字顯示區域周圍的邊界。 這些邊界可以擴充，而且可以包含不同類型的內容和視覺效果。 邊界的範例包括行號顯示和捲軸。

文字視圖子系統的公用類型包含在 *Microsoft.VisualStudio.Text.UI.dll* 和 *Microsoft.VisualStudio.Text.UI.Wpf.dll* 中。 第一個元件包含與平臺無關的元素，而第二個元件包含 WPF 特定的元素。

### <a name="classification-subsystem"></a>分類子系統

分類子系統負責決定文字的字型屬性。 分類器會將文字分成不同的類別，例如「關鍵字」或「批註」。 分類格式對應會將這些類別與實際的字型屬性產生關聯，例如「Blue Consolas 10 pt」。 文字視圖會在格式化和轉譯文字時使用這項資訊。 標記（稍後在本主題稍後會詳細說明）可讓資料與文字範圍產生關聯。

分類子系統的公用類型包含在 Microsoft.VisualStudio.Text.Logic.dll 中，而且會與 Microsoft.VisualStudio.Text.UI.Wpf.dll 所包含之分類的視覺效果層面互動。

### <a name="operations-subsystem"></a>操作子系統

作業子系統會定義編輯器行為。 它可為 Visual Studio 編輯器命令和復原系統提供執行。

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>深入瞭解文字模型和文字視圖

### <a name="the-text-model"></a>文字模型

文字模型子系統包含不同的文字類型分組。 這些包括文字緩衝區、文字快照和文字範圍。

#### <a name="text-buffers-and-text-snapshots"></a>文字緩衝區和文字快照

<xref:Microsoft.VisualStudio.Text.ITextBuffer>介面代表使用 utf-16 編碼的 Unicode 字元序列，也就是 .NET Framework 中的型別所使用的編碼方式 `String` 。 文字緩衝區可保存為檔案系統檔，但這並非必要。

<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>用來建立空的文字緩衝區，或是從字串或的初始化的文字緩衝區 <xref:System.IO.TextReader> 。 文字緩衝區可保存在檔案系統中做為 <xref:Microsoft.VisualStudio.Text.ITextDocument> 。

任何執行緒都可以編輯文字緩衝區，直到執行緒透過呼叫取得文字緩衝區的擁有權為止 <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A> 。 之後，只有該執行緒可以執行編輯。

文字緩衝區可能會在其存留期內經過許多版本。 每次編輯緩衝區時，就會產生新的版本，而不可變的 <xref:Microsoft.VisualStudio.Text.ITextSnapshot> 表示該緩衝區版本的內容。 因為文字快照集是不可變的，所以您可以在任何執行緒上存取文字快照集，而不會有任何限制，即使它所代表的文字緩衝區仍繼續變更。

#### <a name="text-snapshots-and-text-snapshot-lines"></a>文字快照集和文字快照行

您可以將文字快照的內容視為一連串字元或一連串的行來查看。 字元和行都會從零開始編制索引。 空白文字快照包含零個字元和一個空白行。 行是以任何有效的 Unicode 分行符號序列或緩衝區的開頭或結尾分隔。 換行字元會在文字快照中明確表示，而文字快照中的分行符號則不一定相同。

> [!NOTE]
> 如需 Visual Studio 編輯器中換行字元的詳細資訊，請參閱 [編碼和分行符號](../ide/encodings-and-line-breaks.md)。

文字行是由 <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> 物件表示，可從特定行號或特定字元位置的文字快照取得。

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints、SnapshotSpans 和 NormalizedSnapshotSpanCollections

<xref:Microsoft.VisualStudio.Text.SnapshotPoint>表示快照中的字元位置。 此位置保證介於零和快照的長度之間。 <xref:Microsoft.VisualStudio.Text.SnapshotSpan>表示快照中的文字範圍。 它的結束位置保證介於零和快照的長度之間。 是 <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> 由相同快照集的一組物件所組成 <xref:Microsoft.VisualStudio.Text.SnapshotSpan> 。

#### <a name="spans-and-normalizedspancollections"></a>範圍和 NormalizedSpanCollections

<xref:Microsoft.VisualStudio.Text.Span>表示可以套用至文字快照中之文字範圍的間隔。 快照集位置以零為基底，因此範圍可以從任何位置開始，包括零。 `End`範圍的屬性等於其 `Start` 屬性和其屬性的總和 `Length` 。 不 `Span` 包含由屬性編制索引的字元 `End` 。 例如，具有 Start = 5 且 Length = 3 的範圍具有 End = 8，它包含位置5、6和7的字元。 此範圍的標記法為 [5. 8) 。

如果兩個範圍具有任何共同的位置（包括結束位置），則兩者交集。 因此，[3，5) 和 [2，7) 的交集是 [3，5) ，而 [3，5) 和 [5，7) 的交集是 [5，5) 。  (請注意，[5，5) 是空的範圍。 ) 

如果兩個範圍有共同的位置，則會重迭，但結束位置除外。 空白的範圍絕不會與任何其他範圍重迭，而且兩個範圍的重迭永遠不會是空的。

<xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>是跨越範圍開始屬性順序的範圍清單。 清單中會合並重迭或連續的範圍。 例如，假設有一組範圍 [5.. 9) ，[0]) 、[3. 6) 和 [9.. 10) ，則標準化的範圍清單是 [0 ..1) ，[3. 10) 。

#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit、TextVersion 和 text 變更通知

您可以使用物件來變更文字緩衝區的內容 <xref:Microsoft.VisualStudio.Text.ITextEdit> 。 使用) 的其中一種方法來建立這類物件 (`CreateEdit()` <xref:Microsoft.VisualStudio.Text.ITextBuffer> 會啟動由文字編輯所組成的文字交易。 每次編輯都會以字串取代緩衝區中的某些文字範圍。 當交易啟動時，每個編輯的座標和內容會相對於緩衝區的快照表示。 <xref:Microsoft.VisualStudio.Text.ITextEdit>物件會調整在相同交易中受其他編輯影響的編輯座標。

例如，請考慮包含此字串的文字緩衝區：

```
abcdefghij
```

套用包含兩個編輯的交易：有一個編輯會將範圍取代在 [2. 4) ，方法是使用字元 `X` 和第二個編輯，以使用字元取代 [6.. 9) 的範圍 `Y` 。 結果是這個緩衝區：

```
abXefYj
```

第二個編輯的座標是相對於交易開始時的緩衝區內容計算，在套用第一個編輯之前。

當 <xref:Microsoft.VisualStudio.Text.ITextEdit> 物件是藉由呼叫其方法來認可時，緩衝區的變更會生效 `Apply()` 。 如果至少有一個非空白的編輯，則會建立新的 <xref:Microsoft.VisualStudio.Text.ITextVersion> ，並會建立新的， <xref:Microsoft.VisualStudio.Text.ITextSnapshot> 並 `Changed` 引發一個事件。 每個文字版本都有不同的文字快照。 文字快照表示在編輯交易之後，文字緩衝區的完整狀態，但文字版本只會將快照集的變更描述至下一個快照。 一般情況下，文字快照集的目的是要使用一次，然後捨棄，而文字版本必須保持運作一段時間。

文字版本包含 <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection> 。 此集合描述套用至快照集時產生後續快照集的變更。 集合中的每個都 <xref:Microsoft.VisualStudio.Text.ITextChange> 包含變更的字元位置、取代的字串和取代字串。 針對基本的插入，取代的字串是空的，取代的字串是空的，用於基本刪除。 正規化的集合一律 `null` 為最新版本的文字緩衝區。

<xref:Microsoft.VisualStudio.Text.ITextEdit>每次只能為文字緩衝區具現化一個物件，而且必須在擁有文字緩衝區的執行緒上執行所有文字編輯， (是否已宣告擁有權) 。 您可以藉由呼叫其 `Cancel` 方法或其方法來放棄文字編輯 `Dispose` 。

<xref:Microsoft.VisualStudio.Text.ITextBuffer> 也提供 `Insert()` 、 `Delete()` 和 `Replace()` 方法，就像在介面上找到的一樣 <xref:Microsoft.VisualStudio.Text.ITextEdit> 。 呼叫這些與建立 <xref:Microsoft.VisualStudio.Text.ITextEdit> 物件、進行類似的呼叫，然後套用編輯，會有相同的效果。

#### <a name="tracking-points-and-tracking-spans"></a>追蹤點和追蹤範圍

<xref:Microsoft.VisualStudio.Text.ITrackingPoint>代表文字緩衝區中的字元位置。 如果緩衝區是以導致字元位置移位的方式進行編輯，則追蹤點會隨之移動。 例如，如果追蹤點參考緩衝區中的位置10，而且在緩衝區的開頭插入五個字元，則追蹤點會參考位置15。 如果插入作業正好在追蹤點所表示的位置上進行，其行為取決於其 <xref:Microsoft.VisualStudio.Text.PointTrackingMode> ，它可以是 `Positive` 或 `Negative` 。 如果追蹤模式是正面的，則追蹤點會參考相同的字元，這現在位於插入的結尾。 如果追蹤模式是負數，則追蹤點會參考原始位置的第一個插入的字元。 如果刪除追蹤點所代表位置上的字元，追蹤點會移至已刪除範圍之後的第一個字元。 例如，如果追蹤點參考位置5的字元，而且位置3到6的字元被刪除，則追蹤點會參考位置3的字元。

<xref:Microsoft.VisualStudio.Text.ITrackingSpan>代表字元的範圍，而不只是一個位置。 其行為取決於其行為 <xref:Microsoft.VisualStudio.Text.SpanTrackingMode> 。 如果範圍追蹤模式為 [SpanTrackingMode. EdgeInclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive)，則追蹤範圍會成長以合併在其邊緣插入的文字。 如果範圍追蹤模式是 [SpanTrackingMode EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive)，則追蹤範圍不會併入在其邊緣插入的文字。 但是，如果範圍追蹤模式是 [SpanTrackingMode EdgePositive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive)，則插入會將目前的位置推入開始，而且如果範圍追蹤模式是 [SpanTrackingMode. EdgeNegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative)，則插入會將目前的位置推到尾端。

您可以取得追蹤點的位置，或針對它們所屬之文字緩衝區的任何快照集的追蹤範圍的範圍。 追蹤點和追蹤範圍可以從任何執行緒安全地參考。

#### <a name="content-types"></a>內容類型

內容類型是一種機制，可定義不同類型的內容。 內容類型可以是檔案類型，例如 "text"、"code" 或 "binary"，或是 "xml"、"vb" 或 "c #" 之類的技術類型。 例如，"using" 這個字是 c # 和 Visual Basic 中的關鍵字，而不是其他程式設計語言。 因此，這個關鍵字的定義會限制為 "c #" 和 "vb" 內容類型。

內容類型可做為篩選準則的篩選準則，以及編輯器的其他元素。 許多編輯器功能和擴充點都是根據內容類型來定義。 例如，純文字檔、XML 檔案和 Visual Basic 原始程式碼檔的文字著色不同。 文字緩衝區通常會在建立時指派內容類型，而且可以變更文字緩衝區的內容類型。

內容類型可以多重繼承自其他內容類型。 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>可讓您將多個基底類型指定為指定內容類型的父系。

開發人員可以定義自己的內容類型，並使用來註冊它們 <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> 。 您可以使用，根據特定的內容類型來定義許多編輯器功能 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> 。 例如，您可以定義編輯器邊界、裝飾和滑鼠處理常式，使其僅適用于顯示特定內容類型的編輯器。

### <a name="the-text-view"></a>文字視圖

模型視圖控制器 (MVC) 模式的視圖部分會定義文字視圖、視圖的格式、圖形元素（例如捲軸）和插入號。 Visual Studio 編輯器的所有展示元素都是以 WPF 為基礎。

#### <a name="text-views"></a>文字視圖

<xref:Microsoft.VisualStudio.Text.Editor.ITextView>介面是與平臺無關的文字視圖標記法。 它主要用來在視窗中顯示文字檔，但也可以用於其他用途，例如，在工具提示中。

文字視圖參考不同類型的文字緩衝區。 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A>屬性所參考的物件會 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> 指向這三個不同的文字緩衝區：資料緩衝區，也就是最上層的資料層級緩衝區、編輯緩衝區、進行編輯的位置，以及視覺化緩衝區（顯示在文本視圖中的緩衝區）。

文字會根據附加至基礎文字緩衝區的分類器進行格式化，並使用附加至文字視圖本身的裝飾提供者進行裝飾。

#### <a name="the-text-view-coordinate-system"></a>文字視圖座標系統

文字視圖座標系統指定文字視圖中的位置。 在此座標系統中，x 值0.0 對應到所顯示文字的左邊緣，y 值0.0 則對應到所顯示文字的上邊緣。 X 座標從左至右增加，y 座標從上到下增加。

 (文字視窗中可見文字部分的某個區，) 無法以水準方向水準滾動的方式，以相同的方式進行滾動。 您可以藉由變更圖形的左座標來水準滾動區，讓它隨著繪圖介面移動。 不過，您只能藉由變更轉譯的文字（這會引發事件）來垂直捲動區 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> 。

座標系統中的距離對應于邏輯圖元。 如果顯示的文字呈現介面沒有縮放轉換，則文字轉譯座標系統中的一個單位會對應到顯示上的一個圖元。

#### <a name="margins"></a>邊界

<xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin>介面代表邊界，並可讓您控制邊界的可見度和其大小。 有四個預先定義的邊界，稱為「頂端」、「左」、「右」和「底部」，並附加至視圖的頂端、底部、左方或右邊緣。 這些邊界是可放置其他邊界的容器。 介面會定義方法，以傳回邊界的大小和邊界的可見度。 邊界是視覺元素，可提供其附加文字視圖的其他相關資訊。 例如，行號邊界會顯示文字視圖的行號。 圖像邊界會顯示 UI 元素。

<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>介面會處理邊界的建立和放置。 您可以根據其他邊界來排序邊界。 較高優先順序的邊界位於較接近文字視圖的位置。 例如，如果有兩個左邊界、邊界 A 和邊界 B，而邊界 B 的優先順序低於邊界 A，則邊界 B 會顯示在邊界 A 的左邊。

#### <a name="the-text-view-host"></a>Text view 主機

<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>介面包含文字視圖，以及與視圖伴隨的任何相鄰裝飾，例如捲軸。 文字視圖主控制項也包含附加至視圖框線的邊界。

#### <a name="formatted-text"></a>格式化文字

顯示在文字視圖中的文字是由物件所組成 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> 。 每個文字視圖線都對應到文字視圖中的一行文字。 基礎文字緩衝區中的長條可以是部分遮蔽 (如果未啟用自動換行) 或分成多個文字視圖線。 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>介面包含在座標和字元之間進行對應的方法和屬性，以及可能與該行相關聯之裝飾的方法和屬性。

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> 使用介面建立物件 <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> 。 如果您只在意目前顯示在視圖中的文字，您可以忽略格式設定來源。 如果您對未顯示在視圖中的文字格式有興趣 (例如，為了支援 rtf 文字剪下和貼上) ，您可以使用 <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> 來格式化文字緩衝區中的文字。

文字視圖會 <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> 一次格式化一個。

## <a name="editor-features"></a>編輯器功能

編輯器的功能的設計，是為了讓功能的定義與它的執行分開。 編輯器包含下列功能：

- 標記和分類器

- 裝飾品

- 投影

- 大綱

- 滑鼠和按鍵系結

- 作業和基本專案

- IntelliSense

### <a name="tags-and-classifiers"></a>標記和分類器

標記是與文字範圍相關聯的標記。 它們可以不同的方式呈現，例如使用文字著色、底線、圖形或快顯視窗。 分類器是一種標記。

其他類型的標記 <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> 適用于文字反白顯示、 <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> 大綱和 <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> 編譯錯誤。

#### <a name="classification-types"></a>分類類型

<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>介面代表等價類別，這是文字的抽象類別。 分類類型可以多重繼承自其他分類類型。 例如，程式設計語言分類可能包含「關鍵字」、「批註」和「識別碼」，這些都是繼承自「程式碼」。 自然語言分類類型可能包含「名詞」、「動詞」和「形容詞」，其全都繼承自「自然語言」。

#### <a name="classifications"></a>分類

分類是特定分類類型的實例，通常是透過一段文字。 <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan>用來表示分類。 您可以將分類範圍視為包含特定文字範圍的標籤，並告訴系統此範圍的文字屬於特定的分類類型。

#### <a name="classifiers"></a>分類

<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>是一種將文字分成一組分類的機制。 您必須針對特定內容類型定義分類器，並針對特定的文字緩衝區具現化。 用戶端必須實行 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> 以參與文字分類。

#### <a name="classifier-aggregators"></a>分類器匯總工具

分類器匯總工具是一種機制，可將一個文字緩衝區的所有分類器結合成一組分類。 例如，c # 分類器和英文語言分類器都可以在 c # 檔案中的批註上建立分類。 請考慮以下批註：

```
// This method produces a classifier
```

C # 分類器可能會將整個範圍標記為批註，而英文語言分類器可能會將 "產生" 分類為 "verb" 和 "method" 作為「名詞」。 匯總工具會產生一組非重迭的分類，而集合的型別則是以所有貢獻為基礎。

分類器也是分類器，因為它會將文字分成一組分類。 分類器匯總工具也可確保不會有重迭的分類，而且分類會排序。 個別的分類器可以任意順序傳回任何一組分類，並以任何方式進行重迭。

#### <a name="classification-formatting-and-text-coloring"></a>分類格式化和文字著色

文字格式是在文字分類上建立的功能範例。 文字視圖圖層會使用它來判斷應用程式中的文字顯示方式。 文字格式化區域相依于 WPF，但分類的邏輯定義則否。

分類格式是特定分類類型的一組格式化屬性。 這些格式繼承自分類類型的父系格式。

<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>是從分類類型到一組文字格式屬性的地圖。 編輯器中的格式對應的執行會處理所有分類格式的匯出。

### <a name="adornments"></a>裝飾品

裝飾是圖形效果，與文字視圖中的字元字型和色彩不直接相關。 例如，用來標示許多程式設計語言中非編譯器代碼的紅色波浪線是內嵌裝飾，而工具提示則是彈出裝飾。 裝飾衍生自 <xref:System.Windows.UIElement> 和實行 <xref:Microsoft.VisualStudio.Text.Tagging.ITag> 。 裝飾標記的兩個特製化類型是 <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> ，適用于佔用與視圖中文字相同空間的裝飾，以及用於波浪線底線的裝飾 <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> 。

內嵌裝飾是形成格式化文字視圖一部分的圖形。 它們會組織成不同的迭置順序層。 有三個內建的層級，如下所示：文字、插入號和選取專案。 不過，開發人員可以定義更多圖層，並將其放在彼此之間的相對順序。 內嵌裝飾的三種類型是文字相關裝飾 (會在文字移動時移動，並在刪除文字時刪除) 、視圖相對的裝飾 (必須使用 view) 的非文字部分，以及擁有者控制的裝飾， (開發人員必須管理其放置) 。

快顯裝飾是出現在文字視圖上方小視窗中的圖形，例如工具提示。

### <a name="projection"></a><a name="projection"></a> 投影

投射是一種技術，可用於建立不同類型的文字緩衝區，而不會實際儲存文字，而是結合其他文字緩衝區的文字。 例如，投射緩衝區可以用來串連兩個其他緩衝區中的文字，並將結果顯示為僅在一個緩衝區內，或隱藏一個緩衝區中的部分文字。 投射緩衝區可作為另一個投射緩衝區的來源緩衝區。 您可以使用許多不同的方式來建立一組與投射相關的緩衝區，以重新排列文字。  (這類的集合也稱為 *緩衝區圖形*。 ) 使用投影緩衝區來隱藏折迭的文字，就會執行 Visual Studio 文字大綱功能，而 ASP.NET 網頁的 Visual Studio 編輯器會使用投影來支援內嵌語言，例如 Visual Basic 和 c #。

<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>使用建立 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService> 。 投射緩衝區是由一系列已排序的 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> 物件（稱為 *來源範圍*）來表示。 這些範圍的內容會以一系列字元的形式呈現。 從中繪製來源範圍的文字緩衝區會命名為 *來源緩衝區*。 投射緩衝區的用戶端不需要注意它與一般文字緩衝區不同。

投射緩衝區會接聽來源緩衝區上的文字變更事件。 當來源範圍中的文字變更時，投射緩衝區會將已變更的文字座標組應至它自己的座標，並引發適當的文字變更事件。 例如，請考慮具有下列內容的來源緩衝區 A 和 B：

```
A: ABCDE
B: vwxyz
```

如果投射緩衝區 P 是由兩個文字範圍所組成，其中一個具有緩衝區 A，另一個具有緩衝區 B，則 P 會有下列內容：

```
P: ABCDEvwxyz
```

如果 `xy` 從緩衝區 B 中刪除子字串，則緩衝區 P 會引發事件，表示已刪除位置7和8的字元。

您也可以直接編輯投影緩衝區。 它會將編輯傳播到適當的來源緩衝區。 例如，如果字串插入至位置6的緩衝區 P () 字元 "v" 的原始位置，插入會在位置1傳播到緩衝區 B。

對投射緩衝區造成影響的來源範圍有一些限制。 來源範圍可能不會重迭;投射緩衝區中的位置無法對應至任何來源緩衝區中的多個位置，而且來源緩衝區中的位置無法對應至投射緩衝區中的一個以上位置。 來源緩衝區關聯性中不允許任何 circularities。

當投射緩衝區的一組來源緩衝區變更，以及一組來源範圍變更時，就會引發事件。
省略緩衝區是一種特殊的投射緩衝區。 它主要用於大綱和展開和折迭文字區塊的作業。 省略緩衝區只以一個來源緩衝區為基礎，而省略緩衝區中的範圍必須依照在來源緩衝區中的順序來排序。

#### <a name="the-buffer-graph"></a>緩衝區圖形

<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>介面可讓您在投影緩衝區圖形之間進行對應。 所有文字緩衝區和投影緩衝區都是以有向非循環圖表的方式收集，很像語言編譯器所產生的抽象語法樹狀結構。 圖形是由最上層的緩衝區（可以是任何文字緩衝區）所定義。 緩衝區圖形可以從最上層緩衝區中的某個點對應到來源緩衝區中的某個點，或從 top 緩衝區的某個範圍對應到來源緩衝區中的一組範圍。 同樣地，它可以將來源緩衝區的點或範圍對應到最上層緩衝區中的某個點。 緩衝區圖形是使用來建立 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService> 。

#### <a name="events-and-projection-buffers"></a>事件和投射緩衝區

修改投射緩衝區時，會從投射緩衝區將修改傳送至相依于該緩衝區的緩衝區。 所有緩衝區都經過修改之後，就會引發緩衝區變更事件，從最深的緩衝區開始。

### <a name="outlining"></a>大綱

大綱是在文本視圖中展開或折迭不同文字區塊的能力。 大綱定義為一種，與 <xref:Microsoft.VisualStudio.Text.Tagging.ITag> 定義裝飾的方式相同。 <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>是一個標記，可定義可展開或折迭的文字區域。 若要使用大綱，您必須匯入 <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> 以取得 <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> 。 大綱管理員會列舉、折迭和展開不同的區塊（以 <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> 物件表示），並據以引發事件。

### <a name="mouse-bindings"></a>滑鼠系結

滑鼠系結會將滑鼠手機連結至不同的命令。 滑鼠系結是使用所定義 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> ，而按鍵系結則是使用來定義 <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider> 。 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>會自動具現化所有系結，並將其連接到視圖中的滑鼠事件。

<xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor>介面包含不同滑鼠事件的前置處理和後置處理事件處理常式。 若要處理其中一個事件，您可以覆寫中的一些方法 <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> 。

### <a name="editor-operations"></a>編輯器作業

編輯器作業可以用來自動化與編輯器的互動，以進行腳本或其他用途。 您可以 <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> 在指定的上匯入存取作業 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 。 然後，您可以使用這些物件來修改選取專案、將其移至視野，或將插入點移至視圖的不同部分。

### <a name="intellisense"></a>IntelliSense

IntelliSense 支援語句完成、簽章說明 (也稱為參數資訊) 、快速諮詢和 light 燈泡。

語句完成會提供方法名稱、XML 專案和其他程式碼或標記專案可能完成的彈出列表。 一般情況下，使用者手勢會叫用完成會話。 會話會顯示潛在完成的清單，使用者可以選取其中一個或關閉清單。 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>負責建立和觸發 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> 。 會 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> 計算 <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> 會話完成專案的。

## <a name="see-also"></a>另請參閱

- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
- [編輯器匯入](../extensibility/editor-imports.md)
