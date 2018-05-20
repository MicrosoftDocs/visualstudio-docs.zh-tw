---
title: 在編輯器內 |Microsoft 文件
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
ms.openlocfilehash: ace9e405b52873d08c578c2af8e7005249e7d58c
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="inside-the-editor"></a>在編輯器
編輯器 是由不同子系統，設計用來將編輯器 中 文字 檢視和使用者介面文字模型分開的數字。  
  
 下列各節說明編輯器 中的不同層面：  
  
-   [子系統的概觀](../extensibility/inside-the-editor.md#overview)  
  
-   [文字模型](../extensibility/inside-the-editor.md#textmodel)  
  
-   [文字檢視](../extensibility/inside-the-editor.md#textview)  
  
 下列各節說明編輯器的功能：  
  
-   [標記和分類器](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
-   [裝飾](../extensibility/inside-the-editor.md#adornments)  
  
-   [投影](../extensibility/inside-the-editor.md#projection)  
  
-   [大綱](../extensibility/inside-the-editor.md#outlining)  
  
-   [滑鼠繫結](../extensibility/inside-the-editor.md#mousebindings)  
  
-   [編輯器作業，](../extensibility/inside-the-editor.md#editoroperations)  
  
-   [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
##  <a name="overview"></a> 子系統的概觀  
  
### <a name="text-model-subsystem"></a>文字模型子系統  
 文字模型子系統負責表示文字，並啟用其操作。 文字模型子系統包含<xref:Microsoft.VisualStudio.Text.ITextBuffer>介面，其中描述要編輯器所顯示的字元序列。 此文字可以修改、 追蹤，而且有許多方式操作。 文字模型也會提供類型的下列層面：  
  
-   將文字產生關聯的檔案，並管理讀取和寫入檔案系統中的服務。  
  
-   尋找物件的兩個序列之間的最小差異差異服務。  
  
-   系統，用於描述方面的其他緩衝區中的文字子集的緩衝區中的文字。  
  
 文字模型子系統是免費的使用者介面 (UI) 的概念。 比方說，不是負責文字格式或文字版面配置，它不了解 visual 裝飾時，可能會以文字產生關聯。  
  
 文字模型子系統的公用型別都包含在 Microsoft.VisualStudio.Text.Data.dll 和 Microsoft.VisualStudio.CoreUtility.dll，取決於.NET Framework 基底類別程式庫和 Managed Extensibility Framework (MEF)。  
  
### <a name="text-view-subsystem"></a>文字檢視子系統  
 文字檢視子系統負責格式化和顯示文字。 這個子系統中的類型可分為兩個圖層、 根據型別是否依賴 Windows Presentation Foundation (WPF)。 最重要的型別是<xref:Microsoft.VisualStudio.Text.Editor.ITextView>和<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>，控制要顯示的文字行的集合以及插入號、 選取項目和使用 WPF UI 項目在裝飾文字的機能。 這個子系統也提供文字周圍的邊界會顯示區域。 這些邊界可加以擴充，而且可以包含不同類型的內容和視覺效果。 邊界的範例包括列數字的顯示和捲軸。  
  
 Microsoft.VisualStudio.Text.UI.dll 和 Microsoft.VisualStudio.Text.UI.Wpf.dll 中包含文字檢視子系統的公用類型。 第一個組件包含平台無關的項目，而第二個包含 WPF 特定項目。  
  
### <a name="classification-subsystem"></a>分類子系統  
 分類子系統負責判斷文字的字型屬性。 分類器會將文字分成不同類別，例如 「 關鍵字 」 或 「 註解 」。 分類格式對應與這些類別實際的字型屬性，例如，「 藍色 Consolas 10pt"。 格式化和轉譯文字時文字檢視會使用此資訊。 標記，稍後在本主題中，更詳細地如所述讓相關聯的文字範圍的資料。  
  
 Microsoft.VisualStudio.Text.Logic.dll 中, 所包含的分類子系統的公用型別，以及他們與 Microsoft.VisualStudio.Text.UI.Wpf.dll 中所包含的視覺外觀的分類，互動。  
  
### <a name="operations-subsystem"></a>作業子系統  
 作業子系統定義編輯器的行為。 它提供 Visual Studio 編輯器命令的實作和復原系統。  
  
## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>進一步瞭解文字模型與文字檢視  
  
###  <a name="textmodel"></a> 文字模型  
 文字模型子系統所組成的文字型別不同群組。 其中包括文字緩衝區、 文字快照集，以及文字範圍。  
  
#### <a name="text-buffers-and-text-snapshots"></a>文字緩衝區和文字快照集  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer>介面代表使用 utf-16，也就是編碼使用來進行編碼的 Unicode 字元序列`String`.NET Framework 中的類型。 文字緩衝區可以保存為檔案系統的文件，但這並非必要。  
  
 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>用來建立空白文字緩衝區或從字串或初始化文字緩衝區<xref:System.IO.TextReader>。 文字緩衝區可以保存至檔案系統中<xref:Microsoft.VisualStudio.Text.ITextDocument>。  
  
 文字緩衝區可編輯的任何執行緒，直到執行緒取得文字緩衝的擁有權，藉由呼叫<xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>。 在這之後，只有該執行緒可以執行編輯。  
  
 文字緩衝區可以通過許多版本，在其存留期間。 每次編輯緩衝區，和不變，會產生新的版本<xref:Microsoft.VisualStudio.Text.ITextSnapshot>表示該版本之緩衝區的內容。 因為文字快照集是不變，您可以存取文字快照集上任何執行緒，而且沒有任何限制，即使它所代表的文字緩衝區持續地變更。  
  
#### <a name="text-snapshots-and-text-snapshot-lines"></a>文字快照集和文字快照行  
 為一串字元或一連串的行，您可以檢視文字快照集內容。 字元和線條可同時編製索引 0 開始。 空白文字快照集包含零個字元和一個空白行。 任何有效 Unicode 換行字元序列，或是開頭或緩衝區結尾的分隔列。 分行符號字元會明確表示文字快照集，並不是所有具有相同文字快照中的分行符號。  
  
> [!NOTE]
>  如需 Visual Studio 編輯器中的換行字元的詳細資訊，請參閱[編碼與分行符號](../ide/encodings-and-line-breaks.md)。  
  
 文字行由<xref:Microsoft.VisualStudio.Text.ITextSnapshotLine>物件，可透過從文字的快照集的特定行號或特定的字元位置。  
  
#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints、 SnapshotSpans 和 NormalizedSnapshotSpanCollections  
 A<xref:Microsoft.VisualStudio.Text.SnapshotPoint>代表快照中的字元位置。 保證介於零長度和快照集位置。 A<xref:Microsoft.VisualStudio.Text.SnapshotSpan>代表一段快照中的文字。 結束位置一定會介於零長度和快照集。 <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>組成的一組<xref:Microsoft.VisualStudio.Text.SnapshotSpan>在相同快照中的物件。  
  
#### <a name="spans-and-normalizedspancollections"></a>跨距和 NormalizedSpanCollections  
 A<xref:Microsoft.VisualStudio.Text.Span>間隔可以套用至一段文字快照中的文字。 讓範圍可以包含零的任何位置開始，是以零起始，快照集位置。 `End`範圍的屬性的總和等於其`Start`屬性和其`Length`屬性。 A`Span`不包含字元編製索引`End`屬性。 比方說，有開始範圍 = 5 且長度 = 3 已結束 = 8，其中包括在位置 5、 6 和 7 個字元。 此範圍標記法是 5..8）。  
  
 如果有任何位置，包括結束位置，兩個範圍有交集。 因此的交集 [3, 5) 和 [2, 7) 是 [3, 5) 和交集的 [3, 5) 和 [5, 7) 為 [5，5）。 (請注意，[5，5) 是空的範圍。)  
  
 兩個範圍重疊，如果有位置相同，除了結束位置。 空的範圍永遠不會重疊任何其他範圍內，並永遠不會是空的重疊的兩個範圍。  
  
 A<xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>是順序的範圍開始屬性範圍的清單。 在清單中，會合併重疊或相鄰的範圍。 例如，給定範圍的集合 [5..9)，[0..1)，[3..6)，和 [9..10)，正規化的清單的範圍是 [0..1)，[3..10)。  
  
#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit、 TextVersion 和文字變更通知  
 文字緩衝區的內容可以透過變更<xref:Microsoft.VisualStudio.Text.ITextEdit>物件。 建立這類物件 (使用其中一種`CreateEdit()`方法<xref:Microsoft.VisualStudio.Text.ITextBuffer>) 啟動文字交易組成的文字編輯內容。 每個編輯是文字的某些字串緩衝區中範圍的取代。 座標和每個編輯的內容會表示相對於緩衝區的快照集交易啟動時。 <xref:Microsoft.VisualStudio.Text.ITextEdit>物件調整編輯同一筆交易中的其他編輯受影響的座標。  
  
 例如，請考慮包含這個字串的文字緩衝區：  
  
```  
abcdefghij  
```  
  
 套用交易，其中包含兩個編輯動作，會取代在範圍的一個編輯 [2..4) 使用字元`X`並取代在範圍的第二個編輯 [6..9) 使用字元`Y`。 結果是這個緩衝區：  
  
```  
abXefYj  
```  
  
 在套用第一次編輯之前，進行第二個編輯座標所計算的交易，開頭的緩衝區的內容。  
  
 緩衝區所做的變更才會生效時<xref:Microsoft.VisualStudio.Text.ITextEdit>物件藉由呼叫認可其`Apply()`方法。 如果沒有至少一個非空白的編輯，新<xref:Microsoft.VisualStudio.Text.ITextVersion>建立時，新<xref:Microsoft.VisualStudio.Text.ITextSnapshot>會建立一個`Changed`就會引發事件。 每個文字版本而有不同文字快照集。 文字快照集之後編輯異動，表示文字緩衝的完成狀態，但文字版本說明只變更從一個快照集的下一步。 一般情況下，想要使用一次文字快照集且然後捨棄，而文字版本段時間必須保持運作。  
  
 文字版本包含<xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>。 這個集合描述所做的變更，套用至快照集時，會產生後續的快照集。 每個<xref:Microsoft.VisualStudio.Text.ITextChange>集合中包含的變更、 已取代的字串，並取代字串的字元位置。 在取代的字串是空的基本的插入，並取代字串是空的基本的刪除。 正規化的集合一律都是`null`文字緩衝的最新版本。  
  
 只有一個<xref:Microsoft.VisualStudio.Text.ITextEdit>可以具現化物件的文字緩衝區在任何時間，和必須擁有文字緩衝區 （如果宣告的擁有權） 的執行緒上執行所有的文字編輯內容。 可以在放棄藉由呼叫的文字編輯其`Cancel`方法或其`Dispose`方法。  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 也提供`Insert()`， `Delete()`，和`Replace()`類似的方法上找到<xref:Microsoft.VisualStudio.Text.ITextEdit>介面。 這些呼叫已建立相同的效果<xref:Microsoft.VisualStudio.Text.ITextEdit>物件，進行類似的呼叫，然後將套用編輯。  
  
#### <a name="tracking-points-and-tracking-spans"></a>追蹤點和追蹤範圍  
 <xref:Microsoft.VisualStudio.Text.ITrackingPoint>代表文字緩衝區中的字元位置。 如果緩衝區的編輯，則會造成要移位的字元位置的方式，也會隨著它轉移追蹤點。 例如，如果在追蹤點是指位置 10 在緩衝區中，緩衝區開頭就會插入五個字元，追蹤點然後是指位置 15。 如果插入發生在精確地表示追蹤點的位置，其行為取決於其<xref:Microsoft.VisualStudio.Text.PointTrackingMode>，這可以是`Positive`或`Negative`。 如果追蹤模式是正數，追蹤點是指相同的字元現在是在插入點; 結尾如果追蹤模式為負數，追蹤點是指到原始位置插入的第一個字元。 如果刪除的追蹤點所表示之位置處的字元，則追蹤點會轉移之後已刪除的範圍內的第一個字元。 例如，如果追蹤點是指 5，位置處的字元位置 3 到 6 個字元會被刪除，追蹤點是指位置 3 的字元。  
  
 <xref:Microsoft.VisualStudio.Text.ITrackingSpan>代表一個範圍的字元而不是只在一個位置。 其行為取決於其<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>。 如果範圍追蹤模式為<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>，追蹤範圍會增大，以納入文字插入其邊緣; 如果範圍追蹤模式為<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>，追蹤範圍不會併入插入其邊緣的文字。 不過，如果範圍追蹤模式為<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>，插入將目前位置推入朝開始時，如果範圍追蹤模式<xref:Microsoft.VisualStudio.Text.SpanTrackingMode>，插入推播通知到結尾的目前位置。  
  
 您可以將追蹤點的位置或追蹤範圍的範圍取得文字緩衝區，其所屬的任何快照集。 追蹤點和追蹤範圍可以安全地參考從任何執行緒。  
  
#### <a name="content-types"></a>內容類型  
 內容類型是內容的用來定義不同類型的機制。 內容類型可以是檔案類型，例如 「 文字 」、 「 程式碼 」 或 「 二進位 」 或技術類型，例如"xml"、"vb"或"c#"。 例如，word"using"是關鍵字在 C# 和 Visual Basic 中，但不是在其他程式設計語言。 因此，此關鍵字的定義會受限於"c#"和"vb"的內容類型。  
  
 裝飾和編輯器的其他項目，做為篩選條件可用內容類型。 許多編輯器功能和擴充點會定義每個內容類型。例如，文字著色不相同的純文字檔案、 XML 檔案和 Visual Basic 原始程式碼檔。 建立，且可以變更文字緩衝區的內容型別時，文字緩衝區通常會指派內容類型。  
  
 內容類型可以多-繼承自其他內容類型。 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>可讓您指定多個基底類型指定的內容類型的父系。  
  
 開發人員可以定義自己的內容類型，並使用註冊它們<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>。 許多編輯器功能，可以使用來定義特定的內容類型方面<xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>。 例如，編輯器邊界、 裝飾和滑鼠處理常式可以定義，讓它們只適用於顯示特定內容類型的編輯器。  
  
###  <a name="textview"></a> 文字檢視  
 模型檢視控制器 (MVC) 模式的檢視部分定義文字檢視中，檢視、 圖形元素，例如捲軸，以及插入號的格式。 在 Visual Studio 編輯器中的所有簡報項目是以 WPF 為都基礎。  
  
#### <a name="text-views"></a>文字檢視  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>介面是平台無關的表示文字檢視。 它主要用來顯示文字文件，在視窗中，但它也可用用於其他用途，例如，在工具提示。  
  
 [文字] 檢視會參考不同類型的文字緩衝區。 <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A>屬性參考到<xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel>指向這些三個不同的文字緩衝區物件： 資料緩衝區，這是最上層的資料層級緩衝區編輯緩衝區，在編輯開始進行，而且 visual 緩衝區，這是緩衝區，文字檢視中顯示。  
  
 文字會根據連接到基礎文字緩衝區中，分類器格式化和裝飾藉由附加至文字檢視本身的裝飾提供者。  
  
#### <a name="the-text-view-coordinate-system"></a>文字檢視座標系統  
 文字檢視座標系統中指定文字檢視中的位置。 在此座標系統中，對應於所顯示之文字的左邊緣的 x 值 0.0，對應至所顯示之文字的上邊緣的 y 值 0.0。X 座標會增加從左到右，和 y 座標會增加從上到下。  
  
 檢視區 （文字視窗中顯示文字的一部分） 無法水平捲動的相同方式為垂直捲動。 藉由變更其左邊的座標，因此，它對於繪圖介面移到水平捲動檢視區。 不過，在檢視區可以垂直捲動只能透過變更所呈現的文字，會導致<xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>會引發事件。  
  
 座標系統中的距離會對應至邏輯像素為單位。 如果沒有縮放轉換顯示文字呈現表面，文字轉譯座標系統中的一個單位對應至顯示一個像素。  
  
#### <a name="margins"></a>邊界  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin>介面代表邊界，並可讓控制項的可見性的邊界和它的大小。 有四個預先定義的邊界，也就名為"Top"、"Left"、"權限 」 和 「 下 」，而會附加到頂端、 底部、 左邊或右邊的檢視。 這些邊界是的容器，可在其中放置其他邊界。 介面會定義傳回邊界的大小和邊界的可見性的方法。 邊界會提供其他資訊附加至 [文字] 檢視的視覺項目。 例如，行號邊界會顯示 [文字] 檢視的行號。 字符邊界會顯示 UI 項目。  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>介面會處理建立和邊界的位置。 可以排序相對於其他邊界的邊界。 較高優先權邊界位於更接近文字檢視。 例如，如果兩個左邊的界、 邊界 A 和 B，邊界且邊界 B 的優先權低於邊界 A，邊界 B 會顯示左邊界 a  
  
#### <a name="the-text-view-host"></a>文字檢視主機  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>介面包含文字檢視以及任何相鄰的裝飾，隨附於檢視中，例如，捲軸。 文字檢視主機也會包含已附加至檢視的框線的邊界。  
  
#### <a name="formatted-text"></a>格式化的文字  
 顯示文字檢視中的文字組成<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>物件。 每一行文字檢視對應至一行文字檢視中的文字。 長行基礎文字緩衝區中的可以被部分遮蔽 （如果未啟用自動換行） 或折成多個文字檢視行。 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>介面包含方法和屬性對應座標之間的字元，以及裝飾時，可能會產生關聯的程式行的屬性。  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> 物件可由使用<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>介面。 如果您只關心目前檢視中顯示的文字時，您可以忽略格式設定的來源。 如果您想要以不同的文字格式顯示在檢視 （例如，若要支援 rtf 文字剪下並貼上），您可以使用<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>來格式化文字緩衝區中的文字。  
  
 文字檢視格式一<xref:Microsoft.VisualStudio.Text.ITextSnapshotLine>一次。  
  
## <a name="editor-features"></a>編輯器功能  
 編輯器的功能的設計可讓功能的定義是不同於它的實作。 編輯器包含下列功能：  
  
-   標記和分類器  
  
-   裝飾  
  
-   Projection  
  
-   大綱  
  
-   滑鼠和索引鍵繫結  
  
-   作業和基本類型  
  
-   IntelliSense  
  
###  <a name="tagsandclassifiers"></a> 標記和分類器  
 標記是一段文字相關聯的標記。 它們可以呈現不同的方式，例如，使用文字著色、 底線、 圖形或快顯視窗。 分類器是一種標記。  
  
 其他類型的標記則<xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>反白顯示文字，<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>的大綱，和<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>編譯錯誤。  
  
#### <a name="classification-types"></a>分類類型  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>介面代表等價類別是抽象類別的文字。 分類類型可以多-繼承自其他分類類型。 例如，程式設計語言分類可能包含 「 關鍵字 」、 「 註解 」 和 「 識別碼 」，這些全都繼承自 「 程式碼 」。 自然語言分類類型可能包含 「 名詞 」、 「 指令動詞"和"形容詞"，全都繼承自 「 自然語言 「。  
  
#### <a name="classifications"></a>分類  
 分類是特定類別類型的執行個體通常會透過一段文字。 A<xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan>用來代表一種分類。 分類範圍可以視為涵蓋特定的一段文字，並告訴系統，此段文字屬於特定類別類型的標籤。  
  
#### <a name="classifiers"></a>分類器  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier>是將一組分類的文字分解的機制。 分類器必須定義特定內容類型和具現化特定文字緩衝區。 用戶端必須實作<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>參與文字分類。  
  
#### <a name="classifier-aggregators"></a>分類彙總工具  
 分類的彙總工具是一套機制，將一個文字緩衝的所有分類器結合成一組分類。 例如，C# 分類和英文語言分類無法透過 C# 檔案中的註解建立分類。 請考慮這個註解：  
  
```  
// This method produces a classifier  
```  
  
 C# 分類可能會標記為註解，整個範圍和英文語言分類可能分類"會產生"為"verb 」 和 「 方法 」 為 「 名詞 」。 彙總工具會產生一組非重疊的分類，和集合類型根據所有比重。  
  
 分類的彙總工具也是分類器，因為文字分成一組分類。 有任何重疊的分類，並且會排序的分類，也可確保分類彙總工具。 個別的分類器是免費以任何順序，傳回任何一組的分類，並以任何方式重疊。  
  
#### <a name="classification-formatting-and-text-coloring"></a>分類格式和文字色彩  
 文字格式是根據文字分類之功能的範例。 它可由文字檢視層來判斷應用程式中的文字顯示。 文字格式設定區域會視 WPF 中，但邏輯定義的分類並不會。  
  
 分類格式是一組格式化特定分類類型的屬性。 這些格式會繼承父系的分類類型的格式。  
  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>是從分類類型對應至一組文字格式設定屬性。 在編輯器中的格式對應的實作會處理分類格式的所有的匯出。  
  
###  <a name="adornments"></a> 裝飾  
 裝飾會直接與無關的字型和色彩的文字檢視中的字元的圖形效果。 比方說，用來標記非編譯程式碼以在許多程式設計語言中的紅色波浪線底線是內嵌的裝飾，而工具提示快顯的裝飾。 裝飾衍生自<xref:System.Windows.UIElement>並實作<xref:Microsoft.VisualStudio.Text.Tagging.ITag>。 裝飾標記的兩個特製化的型別是<xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>，如佔據相同的空間，以在檢視中，文字的裝飾和<xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>的波浪線底線。  
  
 內嵌的裝飾會形成格式化的文字檢視部分的圖形。 組織在不同的疊置順序圖層。 有三個內建的層級的如下所示： 文字、 插入號和選取項目。 不過，開發人員可以定義多個圖層，並將它們放在彼此相對順序。 內嵌裝飾的三種為相對文字的裝飾 （其中移動時文字會移動，而且已刪除時刪除的文字）、 檢視相對裝飾 （這是要檢視的非文字部份） 和擁有者控制的裝飾 (開發人員必須管理它們的位置）。  
  
 快顯裝飾會出現在上述 [文字] 檢視中，例如工具提示的小視窗中的圖形。  
  
###  <a name="projection"></a> 投影  
 投射是一項技術建構的不同種類的文字緩衝區不會實際儲存的文字，但改為結合其他文字緩衝區中的文字。 例如，投影緩衝區可用來串連兩個其他緩衝區中的文字，並呈現結果，如同它是在只有一個緩衝區，或是隱藏的同一個緩衝區中的文字部分。 投影緩衝區可做為另一個投影緩衝區的來源緩衝區。 可以建構一組相關的投影的緩衝區，以許多不同的方式重新排列的文字。 (這類集合就是所謂*緩衝區圖形*。)Visual Studio 文字的大綱功能藉由使用投影緩衝區，以隱藏摺疊的文字，並適用於 ASP.NET 網頁的 Visual Studio 編輯器使用投影來支援內嵌的 Visual Basic 和 C# 等語言。  
  
 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>建立使用<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>。 投影緩衝區由已排序的序列<xref:Microsoft.VisualStudio.Text.ITrackingSpan>物件稱為*來源範圍*。 這些範圍的內容會顯示為字元序列。 會命名為來源範圍會從中繪製的文字緩衝區*來源緩衝區*。 投影緩衝區的用戶端並沒有要注意，不同於一般文字緩衝區。  
  
 投影緩衝區接聽來源緩衝區上的文字變更事件。 當來源中的文字範圍的變更時，投影緩衝區變更的文字座標會對應至它自己的座標，並引發適當的文字變更事件。 例如，考慮有這些內容的來源緩衝區 A 和 B:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 如果從兩個文字範圍，其中，其中包含所有緩衝區，而其他所有緩衝區 B，形成投影緩衝區 P P 具有下列內容：  
  
```  
P: ABCDEvwxyz  
```  
  
 如果子字串`xy`刪除從緩衝區 B，則緩衝區 P 引發事件，指出已刪除位置 7 和 8 個字元。  
  
 也可以直接編輯投影緩衝區。 它會傳播到適當的來源緩衝區的編輯。 比方說，如果插入的字串緩衝區 P 位置 6 （"v"字元的原始位置） 中，插入不會傳播至緩衝區 B 在位置 1。  
  
 沒有對投影緩衝區的來源範圍的限制。 來源範圍可能不會重疊。投影緩衝區中的位置無法對應到多個位置中任何來源緩衝區，而且來源緩衝區中的位置無法對應到在投影緩衝區中的多個位置。 來源緩衝區關聯性中不允許任何 circularities。  
  
 當投影緩衝區變更和來源組跨越變更時，緩衝處理的來源組時，會引發事件。  
  
 Elision 緩衝區是一種特殊的投影緩衝區。 它主要用來大綱和展開和摺疊的文字區塊作業。 Elision 緩衝區根據一個來源緩衝區，而且範圍 elision 緩衝區中的必須排序相同為它們的順序中的來源緩衝區。  
  
##### <a name="the-buffer-graph"></a>緩衝區圖形  
 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>介面可讓在投影緩衝區的圖形的對應。 在導向非循環圖形中，很像抽象語法樹狀目錄的語言編譯器所產生之收集的所有文字緩衝區和投影緩衝區。 定義圖形上方的緩衝區，它可以是任何文字緩衝區。 從來源緩衝區中的點上方緩衝區中的點，或從上方緩衝區一組的來源緩衝區中的範圍中的範圍，可以將對應緩衝區圖形。 同樣地，它可以地圖點或從來源緩衝區跨越到最上層的緩衝區中的點。 使用來建立緩衝區圖形<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>。  
  
##### <a name="events-and-projection-buffers"></a>事件和投影緩衝區  
 修改投影緩衝區時，就會從投影緩衝區所做的修改傳送至依賴它的緩衝區。 所有緩衝區時，會都修改之後，會引發緩衝區變更事件，從最深的緩衝區。  
  
###  <a name="outlining"></a> 大綱  
 大綱是文字的展開或摺疊的不同文字檢視中區塊的能力。 大綱定義為一種的<xref:Microsoft.VisualStudio.Text.Tagging.ITag>，在相同的方式與定義裝飾。 A<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>是定義的文字區域可以展開或摺疊的標記。 若要使用大綱，您必須匯入<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>取得<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>。 大綱管理員列舉、 摺疊，並展開不同的區塊，以表示<xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible>物件，並據以引發事件。  
  
###  <a name="mousebindings"></a> 滑鼠繫結  
 滑鼠繫結連結滑鼠移動至不同的命令。 使用已定義滑鼠繫結<xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>，並使用已定義的索引鍵繫結<xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>。 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>自動具現化的所有繫結並連接到檢視中的滑鼠事件。  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor>介面包含不同的滑鼠事件的預先處理序和後置處理的事件處理常式。 其中一個事件的控點，您可以覆寫的部分中的方法<xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>。  
  
###  <a name="editoroperations"></a> 編輯器作業，  
 編輯器作業，可以用來自動化互動編輯器中的，以編寫指令碼或其他用途。 您可以匯入<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>上的存取作業指定<xref:Microsoft.VisualStudio.Text.Editor.ITextView>。 您接著可以使用這些物件修改選取項目、 捲動檢視，或將插入號移至不同的檢視部分。  
  
###  <a name="intellisense"></a> IntelliSense  
 IntelliSense 支援陳述式完成、 簽章說明 （也稱為參數資訊）、 快速諮詢和燈泡。  
  
 陳述式完成提供方法名稱、 XML 項目，和其他程式碼撰寫或標記的項目可能完成快顯的清單。 一般情況下，使用者筆勢會叫用完成的工作階段。 工作階段會顯示可能的完成的清單，使用者可以選取其中一個，或關閉的清單。 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>負責建立及觸發<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>。 <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>計算<xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet>的工作階段的完成項目。  
  
## <a name="see-also"></a>另請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)   
 [編輯器匯入](../extensibility/editor-imports.md)
