---
title: 在編輯器內 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f85e7c6e4ba62842986db8e6090415d2e33f1c1
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498950"
---
# <a name="inside-the-editor"></a>在編輯器內
編輯器是由數個不同的子系統，設計用來將編輯器文字檢視和使用者介面文字模型分開的。  
  
 下列各節說明不同層面的編輯器：  
  
-   [子系統的概觀](../extensibility/inside-the-editor.md#overview-of-the-subsystems)  
  
-   [文字模型](../extensibility/inside-the-editor.md#the-text-model)  
  
-   [文字檢視](../extensibility/inside-the-editor.md#the-text-view)  
  
 下列各節說明編輯器的功能：  
  
-   [標記和分類器](../extensibility/inside-the-editor.md#tags-and-classifiers)  
  
-   [裝飾](../extensibility/inside-the-editor.md#adornments)  
  
-   [投影](../extensibility/inside-the-editor.md#projection)  
  
-   [大綱](../extensibility/inside-the-editor.md#outlining)  
  
-   [滑鼠繫結](../extensibility/inside-the-editor.md#mousebindings)  
  
-   [編輯器作業，](../extensibility/inside-the-editor.md#editoroperations)  
  
-   [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
## <a name="overview-of-the-subsystems"></a>子系統的概觀  
  
### <a name="text-model-subsystem"></a>文字模型子系統  
 文字模型子系統負責表示文字，並啟用其操作。 文字模型子系統包含<xref:Microsoft.VisualStudio.Text.ITextBuffer>介面，其中描述要編輯器所顯示的字元序列。 這段文字可以修改、 追蹤，並以其他方式操作在許多方面。 文字模型也會提供類型的下列層面：  
  
-   將文字檔案，並管理讀取和寫入檔案系統中的服務。  
  
-   差異服務，以尋找物件的兩個序列之間的最小差異。  
  
-   系統，用於描述方面的其他緩衝區中的文字子集的緩衝區中的文字。  
  
 文字模型子系統是免費的使用者介面 (UI) 的概念。 比方說，它不會負責設定格式化的文字或文字版面配置，以及它並不知道可能會使用文字產生關聯的視覺裝飾。  
  
 文字模型子系統的公用型別包含在*Microsoft.VisualStudio.Text.Data.dll*並*Microsoft.VisualStudio.CoreUtility.dll*，其中只相依於.NET Framework 基底類別庫與 Managed Extensibility Framework (MEF)。  
  
### <a name="text-view-subsystem"></a>文字檢視子系統  
 文字檢視子系統負責格式化和顯示文字。 此子系統中的類型可分為兩個層級，取決於型別是否需要在 Windows Presentation Foundation (WPF)。 最重要的類型是<xref:Microsoft.VisualStudio.Text.Editor.ITextView>和<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>，可控制要顯示的文字行的集合以及插入號、 選取項目和使用 WPF UI 項目來裝飾文字的功能。 此子系統也提供文字周圍的邊界會顯示區域。 這些邊界可加以擴充，而且可以包含不同類型的內容和視覺效果。 邊界的範例包括行數字的顯示和捲軸。  
  
 中包含的文字檢視子系統的公用型別*Microsoft.VisualStudio.Text.UI.dll*並*Microsoft.VisualStudio.Text.UI.Wpf.dll*。 第一個組件包含平台無關的項目，而第二個包含 WPF 特定項目。  
  
### <a name="classification-subsystem"></a>分類子系統  
 分類子系統負責決定文字的字型屬性。 分類器會將文字分成不同類別，例如 「 關鍵字 」 或 「 註解 」。 分類格式對應與這些類別實際的字型屬性，例如 「 藍色 Consolas 10pt"。 格式化和轉譯文字時，文字檢視使用這項資訊。 標記，稍後在本主題中的更詳細說明，這是讓資料得以與文字範圍相關聯。  
  
 分類子系統的公用類型會包含在 Microsoft.VisualStudio.Text.Logic.dll，而且它們與分類，其包含在 Microsoft.VisualStudio.Text.UI.Wpf.dll 的視覺效果互動。  
  
### <a name="operations-subsystem"></a>作業子系統  
 作業子系統定義編輯器的行為。 它提供 Visual Studio 編輯器命令的實作和復原系統。  
  
## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>仔細看看文字模型和文字檢視  
  
### <a name="the-text-model"></a>文字模型  
 文字模型子系統所組成的文字型別不同群組。 其中包括文字緩衝區、 文字快照集和文字範圍。  
  
#### <a name="text-buffers-and-text-snapshots"></a>文字緩衝區和文字快照集  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer>介面代表使用 utf-16，也就是編碼所使用的編碼的 Unicode 字元序列`String`.NET Framework 中的型別。 文字緩衝區可以保存為檔案系統的文件，但這並非必要。  
  
 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>用來建立空的文字緩衝區或從字串或初始化文字緩衝區<xref:System.IO.TextReader>。 文字緩衝區可以保存至檔案系統當做<xref:Microsoft.VisualStudio.Text.ITextDocument>。  
  
 文字緩衝區可以編輯由任何執行緒，直到執行緒取得文字緩衝的擁有權，藉由呼叫<xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>。 在那之後，只有該執行緒可以執行編輯。  
  
 文字緩衝區可以瀏覽許多版本，在其存留期間。 新的版本會產生每次緩衝區，以編輯和不可變<xref:Microsoft.VisualStudio.Text.ITextSnapshot>表示該版本的緩衝區的內容。 文字的快照集是不可變的因為您可以存取文字上的快照集任何執行緒，而沒有任何限制，即使它所代表的文字緩衝區持續變更。  
  
#### <a name="text-snapshots-and-text-snapshot-lines"></a>文字的快照集和文字的快照集行  
 為一連串的字元或一連串的行，您可以檢視文字快照集內容。 字元和行都是同時編製索引從零開始。 空白文字快照集包含零個字元和一個空白行。 任何有效 Unicode 換行字元序列，或是開頭或結尾的緩衝區，是以分隔列。 文字的快照集，以明確表示分行符號字元，並不是所有具有相同文字快照中的分行符號。  
  
> [!NOTE]
>  如需 Visual Studio 編輯器中的分行符號字元的詳細資訊，請參閱[編碼和分行符號](../ide/encodings-and-line-breaks.md)。  
  
 表示文字行<xref:Microsoft.VisualStudio.Text.ITextSnapshotLine>物件，可從文字的快照集的特定行號或特定的字元位置。  
  
#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints、 SnapshotSpans 和 NormalizedSnapshotSpanCollections  
 A<xref:Microsoft.VisualStudio.Text.SnapshotPoint>表示快照集內的字元位置。 保證介於零和長度的快照集之間的位置。 A<xref:Microsoft.VisualStudio.Text.SnapshotSpan>代表一段文字中的快照集。 介於零和長度的快照集之間保證其結束位置。 <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>組成的一組<xref:Microsoft.VisualStudio.Text.SnapshotSpan>從相同的快照集的物件。  
  
#### <a name="spans-and-normalizedspancollections"></a>範圍和 NormalizedSpanCollections  
 A<xref:Microsoft.VisualStudio.Text.Span>間隔會套用至一段文字快照集內的文字。 快照集位置都以零起始，因此範圍可以包含零的任何位置。 `End`範圍的屬性的總和等於其`Start`屬性並將其`Length`屬性。 A`Span`不包含由編製索引的字元`End`屬性。 例如，具有的起始範圍 = 5 且長度 = 3 的結束 = 8，而且它包含在位置 5、 6 和 7 個字元。 此範圍標記法是 5..8）。  
  
 兩個範圍有交集，如果其共有任何位置，包括結尾的位置。 因此，交集的 [3, 5) 和 [2, 7) 是 [3, 5) 和交集的 [3, 5) 和 [5, 7) 為 [5，5）。 (請注意，[5，5) 是空的範圍。)  
  
 如果它們有位置以常見的結束位置除外，就會重疊兩個範圍。 空的範圍永遠不會重疊任何其他範圍內，並永遠不會是空的重疊的兩個範圍。  
  
 A<xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>是範圍開始屬性的範圍順序的清單。 在清單中，會合併重疊或相鄰的範圍。 比方說，假設有範圍的組 [5..9)，[0..1)，[3..6)，和 [9..10)，正規化的範圍清單 [0..1)，[3..10)。  
  
#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit、 TextVersion 和文字變更通知  
 文字緩衝區的內容可以變更使用<xref:Microsoft.VisualStudio.Text.ITextEdit>物件。 建立這類物件 (使用其中一種`CreateEdit()`方法的<xref:Microsoft.VisualStudio.Text.ITextBuffer>) 啟動文字編輯內容所組成的文字交易。 每個編輯是文字字串緩衝區中的某些範圍的取代。 座標和每個編輯的內容均表示相對於緩衝區的快照集交易啟動時。 <xref:Microsoft.VisualStudio.Text.ITextEdit>物件調整編輯同一筆交易中的其他編輯受影響的座標。  
  
 例如，請考慮包含這個字串的文字緩衝區：  
  
```  
abcdefghij  
```  
  
 套用交易，其中包含兩個編輯、 取代範圍的一個編輯 [2..4) 使用字元`X`，並取代範圍的第二個編輯 [6..9) 使用字元`Y`。 結果會是這個緩衝區：  
  
```  
abXefYj  
```  
  
 在套用第一次編輯之前，進行第二個編輯座標所計算相對於在開始交易，緩衝區的內容。  
  
 緩衝區中所做的變更才會生效時<xref:Microsoft.VisualStudio.Text.ITextEdit>物件藉由呼叫認可其`Apply()`方法。 如果沒有至少一個非空白的編輯、 新<xref:Microsoft.VisualStudio.Text.ITextVersion>建立時，新<xref:Microsoft.VisualStudio.Text.ITextSnapshot>建立時，有一個`Changed`就會引發事件。 每個文字版本具有不同文字快照集。 文字快照集之後編輯異動，表示文字緩衝區的完成狀態，但文字版本說明只變更從一個快照集的下一步。 一般情況下，適用於一次文字的快照集，然後捨棄，雖然文字版本一段時間必須保持運作。  
  
 包含的文字版本<xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>。 這個集合會描述所做的變更，套用至快照集時，會產生後續的快照集。 每個<xref:Microsoft.VisualStudio.Text.ITextChange>集合中包含的變更、 已取代的字串，並取代字串的字元位置。 已取代的字串是空的以進行基本的插入，並取代字串是空的基本的刪除。 正規化的集合一律都是`null`的文字緩衝的最新版本。  
  
 只有一個<xref:Microsoft.VisualStudio.Text.ITextEdit>可以具現化物件的文字緩衝區在任何時間，以及必須在擁有文字緩衝區 （如果已宣告擁有權） 的執行緒上執行所有的文字編輯內容。 文字編輯可以放棄藉由呼叫其`Cancel`方法或其`Dispose`方法。  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 也會提供`Insert()`， `Delete()`，並`Replace()`類似的方法上找到<xref:Microsoft.VisualStudio.Text.ITextEdit>介面。 呼叫這些具有相同的效果，與建立<xref:Microsoft.VisualStudio.Text.ITextEdit>物件，進行類似的呼叫，然後將套用編輯。  
  
#### <a name="tracking-points-and-tracking-spans"></a>追蹤點和追蹤範圍  
 <xref:Microsoft.VisualStudio.Text.ITrackingPoint>代表文字緩衝區中的字元位置。 如果緩衝區已編輯會造成要移位的字元位置的方式，追蹤點會隨著它轉移。 例如，如果在追蹤點是指位置 10 在緩衝區中，緩衝區開頭就會插入五個字元，追蹤點則參考位置 15。 如果插入發生在精確地表示追蹤點的位置，其行為取決於其<xref:Microsoft.VisualStudio.Text.PointTrackingMode>，這可以是`Positive`或`Negative`。 如果追蹤模式是正數，追蹤點是指相同的字元現在是在插入點; 結尾如果追蹤模式為負數，追蹤點是指到原始位置的第一個插入字元。 如果刪除由追蹤點的位置處的字元時，追蹤點會轉移至第一個字元後面的已刪除的範圍中。 例如，如果追蹤點是指字元在位置 5，且位置為 3 到 6 個字元會被刪除，追蹤點是指 3 位置處的字元。  
  
 <xref:Microsoft.VisualStudio.Text.ITrackingSpan>代表一個範圍的字元，而不是只在一個位置。 其行為取決於其<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>。 如果範圍的追蹤模式<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>，追蹤範圍成長將在其邊緣; 插入的文字範圍的追蹤模式是否<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>，追蹤範圍不會併入插入其邊緣的文字。 不過，如果範圍的追蹤模式<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>，插入將目前位置推入朝開始時，如果 span 的追蹤模式<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>，插入將尾聲時的目前位置推入。  
  
 您可以取得文字緩衝區所隸屬的任何快照集的追蹤點的位置或追蹤範圍的範圍。 追蹤點和追蹤範圍可以安全地參考從任何執行緒。  
  
#### <a name="content-types"></a>內容類型  
 內容類型是內容的一種機制來定義不同類型。 內容類型可以是檔案類型，例如 「 文字 」、 「 程式碼 」 或 「 二進位 」 或技術類型，例如"xml"、"vb"或"c#"。 比方說，word 「 using 」 是在 C# 和 Visual Basic 中，但不是在其他程式設計語言的關鍵字。 因此，這個關鍵字的定義會限制在"c#"和"vb"的內容類型。  
  
 內容類型可做為篩選條件的裝飾和編輯器的其他項目。 許多編輯器功能和擴充點定義每個內容的型別;例如，文字著色是不同的純文字檔、 XML 檔案和 Visual Basic 原始程式碼檔。 建立，且可以變更文字緩衝區的內容類型時，文字緩衝區通常會指派內容的類型。  
  
 內容型別可以多個-繼承自其他內容類型。 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>可讓您指定多個基底型別指定的內容類型的父系。  
  
 開發人員可以定義自己的內容類型，並將它們註冊使用<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>。 許多編輯器功能，可以使用來定義特定的內容類型方面<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>。 比方說，編輯器邊界、 裝飾和滑鼠處理常式可以定義，讓它們只適用於顯示特定內容類型的編輯器。  
  
###  <a name="the-text-view"></a>文字檢視  
 模型檢視控制器 (MVC) 模式的檢視部分定義文字檢視中，檢視，例如捲軸，以及插入號的圖形元素的格式。 所有的 Visual Studio 編輯器中的簡報項目是以 WPF 為基礎。  
  
#### <a name="text-views"></a>文字檢視  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>介面是文字檢視的平台無關表示法。 它主要用來顯示文字文件，在視窗中，但它也可用為其他用途，比方說，在工具提示。  
  
 文字檢視參考不同種類的文字緩衝區。 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A>屬性會參考<xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel>指向這些三個不同的文字緩衝區物件： 資料緩衝區，也就是上方的資料層級緩衝區中的編輯會進行，而且 visual 的緩衝區，也就是緩衝區的編輯緩衝區，文字檢視中顯示。  
  
 文字會根據兩個分類器連接至基礎的文字緩衝區中，格式化，並使用附加至文字檢視本身 adornment 提供者上時。  
  
#### <a name="the-text-view-coordinate-system"></a>文字檢視座標系統  
 文字檢視座標系統指定的文字檢視中的位置。 在此座標系統中，對應至要顯示之文字的左邊緣的 x 值 0.0，並對應至所顯示之文字的上邊緣的 y 值 0.0。 X 座標會增加從左到右，y 座標會增加從上到下。  
  
 在檢視區 （文字視窗中顯示的文字部分） 無法水平捲動方式相同，它會以垂直方式捲動。 在檢視區水平捲動藉由變更其左邊的座標，以便將相關的繪圖介面。 不過，在檢視區可以捲動以垂直方式只能透過變更所呈現的文字，這會導致<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>會引發事件。  
  
 座標系統中的距離會對應至邏輯像素為單位。 如果文字轉譯介面顯示沒有縮放轉換時，文字轉譯的座標系統中的一個單位就對應至顯示畫面上的一個像素。  
  
#### <a name="margins"></a>邊界  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin>介面表示邊界，並啟用可見性的邊界和其大小的控制。 有四個預先定義的邊界，也就名為 「 頂端 」、 「 左 」、 「 權利 」 和 「 下限 」，而連接到頂端、 底部、 左邊或右邊的檢視。 這些邊界是可以在其中放置其他邊界的容器。 介面會定義傳回邊界的大小和邊界的可見性的方法。 邊界會提供其他資訊附加到文字檢視的視覺元素。 例如，行號邊界會顯示 [文字] 檢視的行號。 字符邊界會顯示 UI 項目。  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>介面會處理建立和放置的邊界。 可以排序邊界，相對於其他邊界。 較高優先順序的邊界會位在靠近 [文字] 檢視。 比方說，如果有兩個左右的邊界，邊界的邊界 B，B 邊界優先順序要低於邊界的邊界 B 會顯示左邊的邊界 a。  
  
#### <a name="the-text-view-host"></a>文字檢視主機  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>介面包含 [文字] 檢視和任何相鄰的裝飾，隨附於檢視中，比方說，捲軸。 文字檢視主機也會包含已附加至檢視的框線的邊界。  
  
#### <a name="formatted-text"></a>格式化文字  
 文字檢視中顯示的文字組成<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>物件。 文字檢視中的每一行會對應至其中一行文字檢視中的文字。 基礎的文字緩衝區中的長行可以部分遮蔽 （如果未啟用自動換行） 或分成多個文字檢視數行。 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>介面包含方法和屬性對應座標和字元之間，以及可能會以列相關聯的裝飾。  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> 物件可由使用<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>介面。 如果您只關心目前檢視中顯示的文字時，您可以忽略格式設定的來源。 如果您想要以不同的文字格式顯示在檢視 （例如，支援 rtf 文字剪下並貼上），您可以使用<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>文字緩衝區中文字的格式。  
  
 文字檢視格式其中<xref:Microsoft.VisualStudio.Text.ITextSnapshotLine>一次。  
  
## <a name="editor-features"></a>編輯器功能  
 編輯器的功能被設計，此功能的定義是不同於其的實作。 編輯器包含下列功能：  
  
-   標記和分類器  
  
-   裝飾  
  
-   Projection  
  
-   大綱  
  
-   滑鼠和索引鍵繫結  
  
-   作業和基本項目  
  
-   IntelliSense  
  
### <a name="tags-and-classifiers"></a>標記和分類器  
 標籤是一段文字相關聯的標記。 他們可以看到不同的方式，例如，使用文字著色、 底線、 圖形或快顯視窗。 分類器是一種標記。  
  
 其他類型的標籤都<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>反白顯示文字，<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>供製作大綱，和<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>編譯錯誤。  
  
#### <a name="classification-types"></a>分類類型  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>介面代表等價類別，這是抽象的類別目錄的文字。 分類類型可以多個-繼承自其他分類類型。 例如，程式設計語言分類可能包含 「 關鍵字 」、 「 註解 」 和 「 識別碼 」，它們全都繼承自 「 程式碼 」。 自然語言分類類型可能包含 「 名詞 」、 「 動詞 」 和 「 形容詞 」，它們全都繼承自 「 自然語言 」。  
  
#### <a name="classifications"></a>分類  
 分類會透過一段文字通常是特定類別類型的執行個體。 A<xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan>用來代表分類。 分類範圍可以視為涵蓋特定的一段文字，並告訴系統此段文字是以特定的分類類型的標籤。  
  
#### <a name="classifiers"></a>分類器  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier>是一種機制，將文字分解成一組分類。 必須針對特定內容類型定義的分類器，並將它具現化特定文字緩衝區中。 用戶端必須實作<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>參與文字分類。  
  
#### <a name="classifier-aggregators"></a>分類器的彙總器  
 分類器的彙總工具是一種機制，將某一文字緩衝區的所有分類器結合成只是一組分類。 例如，C# 分類和英文語言分類器可以透過 C# 檔案中的註解建立分類。 此註解，請考慮：  
  
```  
// This method produces a classifier  
```  
  
 C# 分類器可能會標記為註解，整個範圍和英文語言分類可能分類 」 會產生"做為 「 動詞 」 和 「 方法 」 與 「 名詞 」。 彙總工具會產生一組非重疊的分類和集的類型根據所有成果。  
  
 分類器的彙總工具也是分類器，因為它將文字分解成一組分類。 有任何重疊的分類和分類，會排序，也可確保分類彙總工具。 個別的分類器均免費以任何順序，傳回任何一組的分類，且以任何方式重疊。  
  
#### <a name="classification-formatting-and-text-coloring"></a>設定格式化的分類和文字色彩  
 文字格式設定是文字分類根據一項功能的範例。 它供文字檢視層，來判斷的應用程式中的文字顯示。 格式化文字的區域取決於 WPF 中，但邏輯定義的分類不。  
  
 分類格式是一組格式化特定分類類型的屬性。 這些格式會繼承父系的分類類型的格式。  
  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>是一組文字格式設定屬性的分類類型對應。 在編輯器中的格式模式的實作會處理分類格式的所有的匯出。  
  
###   <a name="adornments"></a>裝飾  
 裝飾會直接與無關的字型和色彩的文字檢視中的字元的圖形效果。 比方說，用來標記非編譯程式碼以在許多程式設計語言中的紅色波浪線底線是內嵌透過裝飾，而工具提示快顯的裝飾。 裝飾會衍生自<xref:System.Windows.UIElement>並實作<xref:Microsoft.VisualStudio.Text.Tagging.ITag>。 裝飾標記的兩個特製化的型別是<xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>，如佔用相同的空間，以在檢視中，文字的裝飾和<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>的波浪線底線。  
  
 內嵌的裝飾會構成格式化的文字檢視的一部分的圖形。 組織在不同的疊置順序層級。 有三個內建的層級，如下所示： 文字、 插入號和選取項目。 不過，開發人員可以定義多個圖層，並將它們放在彼此的相對順序。 內嵌的裝飾的三種是文字相對於裝飾 （這會刪除的文字時，可刪除移動時文字會移動，且）、 （其中有如何處理非文字部分檢視） 檢視相對於裝飾和擁有者控制的裝飾 (開發人員必須管理它們的位置）。  
  
 快顯裝飾會出現在上述 [文字] 檢視中，例如工具提示的小視窗的圖形。  
  
###  <a name="projection"></a> 投影  
 投射是一種技術來建構不同種類的文字緩衝區，不會實際儲存的文字，但改為結合其他文字緩衝區中的文字。 比方說，串連兩個其他緩衝區中的文字，並呈現結果，它是在只有一個緩衝區，或隱藏一個緩衝區中的文字部分，可以使用投影緩衝區。 投影緩衝區可以做為另一個投影緩衝區的來源緩衝區。 可以建構一組相關的投影的緩衝區，以許多不同的方式重新排列的文字。 (這類集合，也就是*緩衝區圖形*。)Visual Studio 文字大綱功能藉由使用投影緩衝區來隱藏摺疊的文字，並適用於 ASP.NET 網頁的 Visual Studio 編輯器使用投影來支援內嵌的 Visual Basic 和 C# 等語言。  
  
 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>建立使用<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>。 表示已排序的投影緩衝區<xref:Microsoft.VisualStudio.Text.ITrackingSpan>物件，也就*來源範圍*。 這些範圍的內容會顯示為一連串的字元。 名為從中繪製的來源範圍的文字緩衝區*來源緩衝區*。 要注意，它不同於一般文字緩衝區沒有投影緩衝區的用戶端。  
  
 投影緩衝區會接聽的來源緩衝區上的文字變更事件。 當來源中的文字範圍的變更時，投影緩衝區會變更的文字座標對應至它自己的座標，並引發適當的文字變更事件。 例如，假設有這些內容的來源緩衝區 A 和 B:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 如果投影緩衝區 P 由兩個文字範圍，其中，其中包含所有緩衝區，以及其他，其中包含所有緩衝區 B、 P 就會出現下列內容：  
  
```  
P: ABCDEvwxyz  
```  
  
 如果子字串`xy`刪除從緩衝區 B，則緩衝區 P 引發事件，指出已刪除位置，7 和 8 個字元。  
  
 也可以直接編輯投影緩衝區。 它會傳播到適當的來源緩衝區的編輯。 例如，如果字串插入至緩衝區 P 6 （"v"字元的原始位置） 的位置，插入的動作就會傳播到緩衝區 B 在位置 1。  
  
 有參與投影緩衝區的來源範圍的限制。 來源範圍可能不會重疊;投影緩衝區中的位置無法對應到一個以上的位置，在任何來源緩衝區，而來源緩衝區中的位置無法對應到投影緩衝區中的多個位置。 來源緩衝區關聯性中，也允許沒有 circularities。  
  
 來源組緩衝投影緩衝區變更和來源組跨越變更時，會引發事件。  
  
 省略緩衝區是一種特殊的投影緩衝區。 它主要用來製作大綱和展開和摺疊的文字區塊的作業。 Elision 緩衝區根據一個來源緩衝區，而且省略緩衝區中的範圍必須排序相同，它們的順序來源緩衝區中。  
  
#### <a name="the-buffer-graph"></a>緩衝的圖形  
 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>介面可讓圖表的投射緩衝區之間的對應。 有向非循環圖，如同由語言編譯器所產生的抽象語法樹狀目錄中收集的所有文字緩衝區和投影緩衝區。 圖形是由上方的緩衝區，它可以是任何文字緩衝區定義。 從來源緩衝區中的點上方緩衝區中的點，或從上方緩衝區中要將來源緩衝區中的範圍的 span，可以將對應緩衝區圖形。 同樣地，它可以對應一個點，或從來源緩衝區跨越到上方的緩衝區中的點。 緩衝的圖形藉由使用<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>。  
  
#### <a name="events-and-projection-buffers"></a>事件和投影緩衝區  
 修改投影緩衝區時，所做的修改所傳來的投影緩衝區取決於它的緩衝區。 修改所有緩衝區之後，會引發緩衝區變更事件，從最深的緩衝區。  
  
###  <a name="outlining"></a> 大綱  
 大綱是文字的展開或摺疊的不同文字檢視中區塊的能力。 大綱定義為一種的<xref:Microsoft.VisualStudio.Text.Tagging.ITag>，在相同的方式定義的裝飾。 A<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>定義可以展開或摺疊的文字區域的標記。 若要使用大綱，您必須匯入<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>以取得<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>。 大綱 manager 列舉、 摺疊，並展開不同的區塊，以表示<xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible>物件，並據以引發事件。  
  
###  <a name="mousebindings"></a> 滑鼠繫結  
 滑鼠繫結至不同的命令連結滑鼠動作。 您可以使用定義滑鼠繫結<xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>，並使用所定義的按鍵繫結<xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>。 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>自動具現化的所有繫結並連接到檢視中的滑鼠事件。  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor>介面包含不同的滑鼠事件的前置處理和後續處理的事件處理常式。 其中一個事件的控制代碼，您可以覆寫的一些方法<xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>。  
  
###  <a name="editoroperations"></a> 編輯器作業，  
 編輯器作業，可用來自動化與編輯器中的，以編寫指令碼或其他用途之間的互動。 您可以匯入<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>上的存取作業指定<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。 您接著可以使用這些物件修改選取項目、 捲動檢視，或將插入號移至不同的檢視部分。  
  
###  <a name="intellisense"></a> IntelliSense  
 IntelliSense 支援陳述式完成、 簽章說明 （也稱為 「 參數資訊 」）、 快速諮詢和燈泡。  
  
 陳述式完成提供的方法名稱、 XML 項目，以及其他撰寫程式碼或標記的項目可能的完成項的快顯清單。 一般情況下，使用者筆勢叫用完成工作階段。 工作階段會顯示可能的完成的清單，使用者可以選取其中一個，或關閉清單。 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>負責建立並觸發<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>。 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>計算<xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet>的工作階段的完成項目。  
  
## <a name="see-also"></a>另請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)   
 [編輯器匯入](../extensibility/editor-imports.md)
